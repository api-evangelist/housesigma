---
name: Track HouseSigma Canadian housing-market commentary
description: >-
  Find, filter and read HouseSigma's published market analysis for Ontario, British Columbia
  and Alberta through the public Blog Content API, using search, taxonomy filters and date
  windows, and resolve each hit to full article text.
api: openapi/housesigma-blog-content-openapi.yml
base_url: https://housesigma.com/blog-en/wp-json
auth: none
operations: [search, listPosts, getPost, listCategories, listTags, getCategory, getTag]
generated: '2026-07-26'
method: generated
---

# Track HouseSigma Canadian housing-market commentary

HouseSigma publishes no developer program. The only public, anonymously callable HouseSigma
API is the WordPress REST surface behind `housesigma.com/blog-en`, which serves the company's
Canadian housing-market analysis as JSON. Listings, sold history and SigmaEstimate valuations
are **not** available through any public API — do not attempt to retrieve them here, and do
not call the private `/bkv2/api/` backend, which the site's `robots.txt` disallows.

## Before you start

- Base URL: `https://housesigma.com/blog-en/wp-json`
- No key, token or header is required. Send plain HTTPS GETs.
- This is an undocumented consumer host with **no published rate limit and no rate-limit
  headers**. Self-throttle: sequential requests, `per_page` at or near its maximum of 100,
  and stop on repeated failures.
- Cite HouseSigma and link the post's `link` field in anything you produce.

## Steps

1. **Orient on the topic taxonomy.** Call `listCategories` with `per_page=100` and
   `orderby=count`, `order=desc`. Each category carries `id`, `name`, `slug` and `count`, so
   you learn which market areas and themes HouseSigma actually writes about before guessing at
   search terms. Do the same with `listTags` when you need finer topics.
2. **Search when you have a phrase.** Call `search` with `search=<phrase>` and
   `per_page=<1..100>`. It returns a thin projection — `id`, `title`, `url`, `type`,
   `subtype`, `_links` — not article bodies. Use it to identify candidates cheaply.
3. **Filter when you have a category, tag or date window.** Call `listPosts` instead, and
   combine:
   - `search` — full-text
   - `categories` / `tags` — arrays of ids from step 1; `categories_exclude` / `tags_exclude`
     to remove noise; `tax_relation` (`AND` / `OR`) when combining
   - `after` / `before` and `modified_after` / `modified_before` — ISO 8601 date-times, for
     "what did HouseSigma publish this quarter"
   - `orderby` (`date` is the useful default for commentary) with `order=desc`
4. **Page correctly.** Read `X-WP-Total` and `X-WP-TotalPages` from the response headers, or
   follow the `Link` header's `rel="next"`. Increment `page`; `per_page` is capped at 100 and
   a larger value fails with `rest_invalid_param` rather than being clamped.
5. **Read the article.** For each candidate call `getPost` with its `id`. `title.rendered`,
   `excerpt.rendered` and `content.rendered` are HTML — strip tags before summarising. Use
   `_embed` to inline the author, featured image and taxonomy terms in the same request, or
   `_fields=id,link,date,title,content` to keep responses small.
6. **Resolve context via `_links`.** Every post carries `_links.author`,
   `_links["wp:featuredmedia"]` and `_links["wp:term"]`. Follow them rather than guessing
   endpoints; `getCategory` and `getTag` resolve individual terms by id.

## Conventions and failure handling

Full detail lives in `conventions/housesigma-conventions.yml` and
`errors/housesigma-problem-types.yml`. The short version:

- Errors are **not** RFC 9457. The envelope is `{code, message, data: {status, ...}}` as
  `application/json`, with the HTTP status echoed at `data.status`.
- `rest_invalid_param` (400) — a parameter broke a declared bound or enum. Read
  `data.params` for the per-parameter message; the OpenAPI carries the same bounds.
- `rest_post_invalid_id` (404) — the id does not exist. List first, then fetch.
- `rest_no_route` (404) — the path or method is not registered. Re-read the live route list
  at `https://housesigma.com/blog-en/wp-json/`.
- `rest_forbidden` (401) — the route is not anonymous. Do not retry and do not try to
  authenticate; HouseSigma issues no credentials for this surface.
- There is no idempotency key and none is needed — every operation here is a safe GET.
