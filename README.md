# ScrapingAnt

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

ScrapingAnt is a web-data infrastructure platform operated by DATAANT that puts headless Chrome rendering, a rotating pool of 3M+ residential and datacenter proxies, CAPTCHA avoidance and AI-powered extraction behind a single HTTP API. One request returns a fully JavaScript-rendered page as raw HTML, as LLM-ready Markdown, as an extended JSON envelope carrying cookies, headers, XHRs and iframes, or as structured JSON described in plain English. A hosted, remote MCP server exposes three of those formats as native tools to Claude, Cursor, Windsurf, Cline and VS Code, so an AI agent gets live web access without running a browser locally. Billing is metered in API credits with a permanently free 10,000-credit monthly tier; standalone rotating proxies are sold separately by bandwidth.

**Areas:** Data Extraction · Proxies · Web Scraping · Browser Automation · AI Agents · MCP · LLM · Data Collection · Web Data

## ScrapingAnt on APIs.io

Everything profiled for ScrapingAnt is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/scrapingant/](https://apis.io/providers/scrapingant/)** — or go straight to one of the APIs or properties below.

### APIs (5)

- [ScrapingAnt](https://apis.io/apis/scrapingant/scrapingant/) — ScrapingAnt is a web scraping API service that handles proxy rotation, headless browsers, and CAPTCHA solving for reliable web data extraction.
- [ScrapingAnt Scraping API](https://apis.io/apis/scrapingant/scrapingant-scraping-api/) — The ScrapingAnt web scraping endpoint. GET/POST/PUT/PATCH/DELETE /v2/general renders a target URL in headless Chrome behind rotating proxies and returns the…
- [ScrapingAnt Usage API](https://apis.io/apis/scrapingant/scrapingant-usage-api/) — Account credit metering for ScrapingAnt. GET /v2/usage returns the current plan name, subscription period, total plan credits and remaining credits - the…
- [ScrapingAnt MCP Server](https://apis.io/apis/scrapingant/scrapingant-mcp-server/) — First-party hosted remote MCP server at https://api.scrapingant.com/mcp/ exposing get_web_page_html, get_web_page_markdown and get_web_page_text to MCP…
- [ScrapingAnt General API](https://apis.io/apis/scrapingant/scrapingant-general-api/) — The General API from ScrapingAnt — 1 operation(s) for general.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [ScrapingAnt MCP Server](https://apis.io/servers/scrapingant/scrapingant-mcp-server/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Scrapingant Agentic Access](https://apis.io/agentic-access/scrapingant/scrapingant-agentic-access/)

#### Collections (2)

Postman and Open Collection request collections.

- [ScrapingAnt](https://apis.io/collections/scrapingant/open-scrapingant/)
- [ScrapingAnt Scraping API](https://apis.io/collections/scrapingant/open-scrapingant-scraping-api/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Scrapingant Scraping Api Overlay](https://apis.io/overlays/scrapingant/scrapingant-scraping-api-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Scrapingant Authentication](https://apis.io/security/scrapingant/scrapingant-authentication/)
- [Scrapingant Domain Security](https://apis.io/security/scrapingant/scrapingant-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Scrapingant Plans Pricing](https://apis.io/plans/scrapingant/scrapingant-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Scrapingant Rate Limits](https://apis.io/rate-limits/scrapingant/scrapingant-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Scrapingant Finops](https://apis.io/finops/scrapingant/scrapingant-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://scrapingant.com/)
- [Documentation](https://docs.scrapingant.com/)
- [Getting started](https://docs.scrapingant.com/api-basics)
- [API reference](https://api.scrapingant.com/docs)
- [Pricing](https://scrapingant.com/#pricing)
- [Sign up](https://app.scrapingant.com/signup)
- [Support](https://scrapingant.com/#contact)
- [Blog](https://scrapingant.com/blog/rss.xml)
- [Terms of service](https://scrapingant.com/legal/terms-of-use)
- [Privacy policy](https://scrapingant.com/legal/privacy-policy)
- [GitHub](https://github.com/ScrapingAnt)

## API Evangelist rating

**Kin Score 49.7** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 68.3 |
| Contract quality | 47.3 |
| Contract governance | 4.5 |
| Operational transparency | 34.2 |
| Developer ergonomics | 63.7 |
| Access clarity | 64.5 |

**Agent readiness 31.7** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | documented (partial credit) |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | — |

**Regulatory alignment 22.7** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/scrapingant/](https://apis.io/providers/scrapingant/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for ScrapingAnt: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/scrapingant/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
