---
name: scrapingant-page-to-markdown-for-llm
description: >-
  Turn any URL into clean, token-efficient Markdown for an LLM context window or a RAG index,
  using either the ScrapingAnt REST Markdown endpoint or its MCP tool.
api: ScrapingAnt Scraping API
provider: scrapingant
generated: '2026-08-29'
method: generated
source: >-
  https://docs.scrapingant.com/llm-markdown, https://docs.scrapingant.com/credits-cost,
  mcp/scrapingant-mcp-tools-list.json (probed 2026-08-29)
operations:
  - GET /v2/markdown
mcp_tools:
  - get_web_page_markdown
base_url: https://api.scrapingant.com/v2
---

# Page to Markdown for an LLM

## When to use this

You want a page's *meaning* in a context window, not its DOM. Markdown strips nav, ads and
scripts and tokenizes far more cheaply than raw HTML, which matters when you are pushing many
pages into a prompt or chunking for a vector store.

## Two ways in — pick by where you are

**If you are an agent with the ScrapingAnt MCP server connected**, call the tool:

```
get_web_page_markdown(url="https://example.com", browser=true,
                      proxy_type="datacenter", proxy_country=null)
```

That is the whole surface. The tool takes only those four arguments — no timeout, no
`wait_for_selector`, no resource blocking. If you need any of those, drop to REST.

**If you are writing code**, call REST:

```
GET https://api.scrapingant.com/v2/markdown?url=<urlencoded>
     with header x-api-key: <KEY>
```

It accepts the same parameter set as `/v2/general`, so `browser`, `proxy_type`,
`proxy_country`, `timeout`, `wait_for_selector` and `block_resource` all work here.

## The response

```json
{ "url": "https://example.com", "markdown": "# Heading\n\nParagraph..." }
```

Read `markdown`. That is the field you put in the prompt.

## Cost

Markdown transformation adds nothing on top of the underlying fetch — you pay the normal
`/v2/general` rate for whatever browser and proxy options you chose (10 credits for the
default browser + datacenter combination, 1 credit with `browser=false`). Failed requests are
free.

For a large ingest, that gap is the whole budget: `browser=false` on documentation sites and
static blogs costs a tenth of the default. Test one URL both ways and compare the Markdown
before you decide the cheap path is unusable.

## Chunking note

Markdown output preserves heading structure. Chunk on headings rather than on a fixed character
count — it keeps sections intact and gives each chunk a natural title for retrieval.

## Errors

Identical to `/v2/general`: 423 anti-bot (escalate to `proxy_type=residential`), 409 concurrency,
403 bad key or exhausted credits, 404 target unreachable, 422 bad parameter or missing key.
See `errors/scrapingant-problem-types.yml`.
