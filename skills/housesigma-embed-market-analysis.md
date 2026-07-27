---
name: Embed a HouseSigma market-analysis post
description: >-
  Turn a HouseSigma blog URL into a ready-to-paste, attributed embed using the oEmbed 1.0
  endpoint, with a fallback card built from the post record and its featured image.
api: openapi/housesigma-blog-content-openapi.yml
base_url: https://housesigma.com/blog-en/wp-json
auth: none
operations: [getOembed, search, getPost, getMediaItem]
generated: '2026-07-26'
method: generated
---

# Embed a HouseSigma market-analysis post

`getOembed` is the only embeddable surface HouseSigma exposes. It returns a standards-compliant
oEmbed 1.0 `rich` response for any HouseSigma blog URL, including ready-made iframe HTML, a
title, a description and a thumbnail. There is no listing widget, map widget or SigmaEstimate
valuation widget — those are not offered publicly, so do not attempt to build one.

## Steps

1. **Get the canonical URL.** If you only have a phrase, call `search` with
   `search=<phrase>&per_page=5` and take the `url` from the best hit. If you have a post id,
   call `getPost` and take `link`.
2. **Resolve the embed.** Call `getOembed` with `url=<the housesigma.com/blog-en/... URL>`.
   Optional `maxwidth` / `maxheight` constrain the returned dimensions. The response contains:
   - `provider_name` (`HouseSigma`) and `provider_url` — use these for attribution
   - `title`, `description`, `author_name`, `author_url`
   - `type: rich`, `width`, `height`
   - `html` — a `wp-embedded-content` blockquote fallback plus a sandboxed iframe
     (`sandbox="allow-scripts" security="restricted"`) pointing at `{post-url}/embed/`
   - `thumbnail_url` — the post's featured image
3. **Decide how to render.**
   - Rich host that allows iframes: insert `html` verbatim. It carries WordPress's own
     `receiveEmbedMessage` resize script; keep the `data-secret` attributes intact or the
     iframe will not resize.
   - Restricted host: build your own card from `title`, `description`, `thumbnail_url`,
     `author_name` and the source URL. Never strip the link back to HouseSigma.
4. **Enrich the card when you need more.** `getPost` gives `excerpt.rendered` (HTML — strip
   tags) and `featured_media`; pass that id to `getMediaItem` for `source_url`,
   `media_details.sizes` and `alt_text` so you can pick a size that fits your layout.
5. **Discover the endpoint from the page if you prefer.** HouseSigma blog pages advertise
   `<link rel="alternate" type="application/json+oembed" href="...">`, so a generic
   oEmbed-aware consumer can resolve an embed without hard-coding the route.

## Constraints and failure handling

- Do **not** call `/oembed/1.0/proxy` — it returns `rest_forbidden` (401) anonymously and is
  excluded from the spec.
- A URL that is not a HouseSigma blog permalink returns a 404 in the WordPress envelope
  (`{code, message, data: {status}}`), not RFC 9457 problem+json.
- No rate limit is published or signalled. Cache the oEmbed response per URL rather than
  re-resolving on every render.
- Content is HouseSigma's. Preserve `provider_name` attribution and the outbound link; see
  https://housesigma.com/blog-en/2018/04/25/terms-of-use/.
- Full detail: `conventions/housesigma-conventions.yml`,
  `components/housesigma-components.yml`, `errors/housesigma-problem-types.yml`.
