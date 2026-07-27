---
name: Mirror the HouseSigma content catalog
description: >-
  Walk the complete public HouseSigma Blog Content API surface - posts, pages, media, authors,
  categories, tags and the type/taxonomy registry - page by page, to build a local index of
  everything the company publishes openly.
api: openapi/housesigma-blog-content-openapi.yml
base_url: https://housesigma.com/blog-en/wp-json
auth: none
operations: [listTypes, listTaxonomies, listStatuses, listPosts, listPages, listMedia,
  listUsers, listCategories, listTags, getPost, getPage, getMediaItem]
generated: '2026-07-26'
method: generated
---

# Mirror the HouseSigma content catalog

Build a complete local index of HouseSigma's public content. This is the whole of HouseSigma's
open API footprint — there is no listings, sold-price or valuation API to mirror, and the
private `/bkv2/api/` backend is robots-disallowed and out of bounds.

## Before you start

- Base URL: `https://housesigma.com/blog-en/wp-json`, anonymous HTTPS GETs only.
- No published rate limit and no rate-limit headers are returned. Run sequentially with a
  pause between pages; back off and stop on repeated non-2xx responses.
- At the time of capture the catalog was small (105 posts), so a full walk is cheap. Re-check
  `X-WP-Total` before assuming that is still true.

## Steps

1. **Read the registry first.** Call `listTypes`, `listTaxonomies` and `listStatuses`. These
   tell you which content types exist, their `rest_base` values, which taxonomies apply to
   which types, and which statuses are public. Do not hard-code the type list.
2. **Walk each collection.** For `listPosts`, `listPages`, `listMedia`, `listUsers`,
   `listCategories` and `listTags`:
   - Request `per_page=100` (the declared maximum) and `page=1`.
   - Read `X-WP-Total` and `X-WP-TotalPages` from the response headers to size the walk, or
     follow the `Link` header `rel="next"`.
   - Increment `page` until you have consumed `X-WP-TotalPages`.
   - Use `orderby=id&order=asc` for a stable walk so new publishing during the crawl does not
     shift items between pages.
3. **Keep responses small.** Pass `_fields` with only the properties you store — for example
   `_fields=id,date,modified,slug,link,title,categories,tags,author,featured_media` on posts.
   Add `_embed` only on the items you actually render.
4. **Fetch detail selectively.** `getPost`, `getPage` and `getMediaItem` retrieve a single
   record by `id`. You rarely need them after a `_fields`-shaped collection walk; use them to
   refresh a single changed item.
5. **Do incremental refreshes.** On later runs, call `listPosts` and `listPages` with
   `modified_after=<last-run ISO 8601 timestamp>` and `orderby=modified&order=asc`. This
   returns only what changed. Media uses `after` / `before` on upload date.
6. **Resolve relationships from the ids you already hold.** Posts reference `author`,
   `featured_media`, `categories[]` and `tags[]` as bare integers; the entity graph is written
   out in `data-model/housesigma-data-model.yml`. Join locally instead of re-fetching per item.

## Conventions and failure handling

- Pagination: `page` / `per_page` (max 100) / `offset`; totals in `X-WP-Total` and
  `X-WP-TotalPages`; `Link` carries `rel="next"` / `rel="prev"`. All three headers are named
  in `Access-Control-Expose-Headers`, so browser clients can read them.
- No `ETag` or `Last-Modified` is returned — conditional requests are not available. Use
  `modified_after` for incrementality instead.
- `rest_invalid_param` (400) on `per_page>100`: the value is rejected, not clamped.
- `rest_forbidden` (401) on `/wp/v2/settings`, `/wp/v2/block-types`, `/oembed/1.0/proxy` and
  `/basepress_kb/v1/kb_categories` — these are excluded from the spec on purpose. Skip them.
- Full detail: `conventions/housesigma-conventions.yml`, `errors/housesigma-problem-types.yml`.
