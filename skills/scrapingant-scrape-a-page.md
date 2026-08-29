---
name: scrapingant-scrape-a-page
description: >-
  Fetch the rendered content of a web page through ScrapingAnt, choosing the cheapest option
  set that will actually work, and handle the anti-bot and quota failures correctly.
api: ScrapingAnt Scraping API
provider: scrapingant
generated: '2026-08-29'
method: generated
source: >-
  openapi/_original/scrapingant-openapi.json, https://docs.scrapingant.com/api-basics,
  https://docs.scrapingant.com/request-response-format, https://docs.scrapingant.com/errors,
  https://docs.scrapingant.com/credits-cost
operations:
  - scrapingant_general_request_v2_general_get
base_url: https://api.scrapingant.com/v2
---

# Scrape a page with ScrapingAnt

## When to use this

You need the content of a URL that a plain HTTP GET will not give you — the page renders
client-side, or the origin blocks datacenter traffic, or you need a specific country's view.

## Authenticate

Send your key as the `x-api-key` HTTP header. The published OpenAPI declares it as a query
parameter; prefer the header anyway, because query strings end up in access logs and Referer
headers. A missing key returns **422**, not 401.

## Pick the option set before you call — it changes the price by 125x

`GET /v2/general?url=<urlencoded>`

| What you set | Credits | Use when |
|---|---|---|
| `browser=false` | 1 | Static HTML, server-rendered, friendly origin |
| `browser=true&return_page_source=true` | 2 | You want the raw server response, no JS |
| `browser=true` (default) | 10 | SPA, lazy-loaded, JS-dependent content |
| `browser=false&proxy_type=residential` | 25 | Static page behind IP-based blocking |
| `browser=true&proxy_type=residential` | 125 | Hard target: Cloudflare, retail, social |

Start at the cheapest row that could plausibly work and escalate only on failure. Do not
default to residential + browser; it is the most expensive call in the product.

Other parameters worth knowing:

- `timeout` — 5 to 60 seconds. Lower it when a fast partial answer beats a slow complete one.
- `wait_for_selector` — a CSS selector to wait for. The right tool when content arrives late;
  far better than raising `timeout` and hoping.
- `block_resource=image&block_resource=font&block_resource=media` — repeatable; drop payload
  you will not parse and cut render time.
- `proxy_country` — ISO code from: ae au br ca cn cz de es fr gb hk id il in it jp kr my nl ph
  pl ru sa sg th us vn.
- `js_snippet` — base64-encoded JavaScript run after load.

## Read the response

A **200** returns the page's HTML as the response body — not JSON, despite what the spec's
declared media type says. The `Ant-credits-cost` response header tells you what the call cost.

## Handle failures by status, not by string

- **423 anti-bot detected** — the expected failure on hard targets. Escalate ONE step:
  `browser=false` → `browser=true`, then `proxy_type=residential`, then add a `proxy_country`
  near the target's audience. Do not retry the identical request; it will fail identically.
  No `Retry-After` is returned, so you own the backoff.
- **409 concurrency limit** — free plan only. Reduce in-flight requests and retry with
  exponential backoff plus jitter.
- **403** — ambiguous: either the key is wrong or the credits are gone. Do not retry blind.
  Call `GET /v2/usage` and read `remained_credits`. Zero means top up; non-zero means the key
  is bad.
- **404** — the TARGET url is unreachable, not a ScrapingAnt routing error. Verify the URL.
- **422** — missing or invalid parameter. Read `detail`, which may be a plain string OR an
  array of `{loc, msg, type}` objects. Handle both shapes.
- **500** — retry once, then report.

Every error body is `{"detail": "..."}`. There is no error code to switch on.

## Do not do this

Do not send POST, PUT, PATCH or DELETE to `/v2/general` unless you specifically intend to make
that request against the target site. ScrapingAnt proxies the method through. There is no
idempotency key and no way to undo it.
