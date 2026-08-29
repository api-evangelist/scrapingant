---
name: scrapingant-track-credit-budget
description: >-
  Keep an autonomous ScrapingAnt workload solvent — read the remaining credit balance, estimate
  what a planned batch will cost, and avoid the 403 that means "out of money".
api: ScrapingAnt Usage API
provider: scrapingant
generated: '2026-08-29'
method: generated
source: >-
  openapi/_original/scrapingant-openapi.json (GET /v2/usage, ApiGeneralUsageResponse),
  https://docs.scrapingant.com/credits-cost, https://scrapingant.com/#pricing
operations:
  - scrapingant_usage_v2_usage_get
base_url: https://api.scrapingant.com/v2
---

# Track your ScrapingAnt credit budget

## Why this skill exists

ScrapingAnt gives you no runtime backpressure. There are no `RateLimit-*` headers, no
`Retry-After`, and no 429. When the monthly credit pool runs out you get a **403** whose message
also covers "your API token is wrong" — so a workload that does not track its own spend fails
ambiguously, mid-batch, with no warning.

If you are driving ScrapingAnt through the MCP server, this is worse: **no MCP tool reports
credits**. An agent on MCP alone is blind to its budget and must call REST for this.

## Read the balance

```
GET https://api.scrapingant.com/v2/usage
     with header x-api-key: <KEY>
```

Returns:

```json
{
  "plan_name": "...",
  "start_date": "2026-08-01T00:00:00Z",
  "end_date": "2026-09-01T00:00:00Z",
  "plan_total_credits": 500000,
  "remained_credits": 412300
}
```

`remained_credits` is the number that matters. `end_date` is when the pool resets — and it
resets to the plan total, because **unused credits do not roll over**.

## Estimate before you run

Cost per request depends entirely on the options you pass:

| Options | Credits |
|---|---|
| `browser=false` + datacenter | 1 |
| `browser=true&return_page_source=true` + datacenter | 2 |
| `browser=true` + datacenter (default) | 10 |
| `browser=false` + residential | 25 |
| `browser=true&return_page_source=false` + datacenter | 50 |
| `browser=true` + residential | 125 |
| any Google domain + datacenter | 10 |

AI extractor adds `ceil((markdown_chars + output_chars) / 30)` on top of the fetch cost.

So: `estimated = urls × credits_per_request`. A 5,000-page crawl at the default browser setting
is 50,000 credits — a tenth of a Startup plan, or five times the entire free tier.

## The loop

1. Call `/v2/usage` once before the batch.
2. Estimate the batch cost from the table above.
3. If `estimated > remained_credits`, either downgrade the option set (`browser=false` is a
   10x saving) or split the batch across billing periods. Do not just start and hope.
4. Re-check `/v2/usage` every few hundred requests on a long run. Each response also carries
   `Ant-credits-cost`, which reports what that single call cost — useful for validating your
   estimate against reality early.
5. On a **403**, call `/v2/usage` before doing anything else. `remained_credits: 0` means top
   up or restart the plan (ScrapingAnt lets you restart mid-cycle rather than waiting for the
   reset). Anything else means the key is wrong.

## Free work

Failed requests cost 0 credits. A 423 or a 500 does not draw down the pool, so aggressive
retrying is a latency problem rather than a budget one — but a *successful* retry of an
already-successful fetch does cost full price. Cache what you have already fetched.
