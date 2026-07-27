# HouseSigma (housesigma)

HouseSigma, Inc. Brokerage is a Toronto-based Canadian residential real estate portal and licensed brokerage that pairs map-based MLS listing search with sold-price history and machine-learning home valuations (SigmaEstimate) across Ontario, British Columbia, and Alberta. It sits in the challenger layer of the Canadian value chain, below CREA, which operates REALTOR.ca and the national Data Distribution Facility (DDF) that syndicates member boards' listings, and alongside Wahi, Zolo, and Properly, competing on visibility into data the boards control, a position it won in part through the Competition Bureau litigation that forced TRREB to release sold data in 2018. Its API posture is closed. There is no developer portal, no published API program, and no partner or data-licensing page; developer., developers., and docs.housesigma.com do not resolve in DNS, and /developers, /api, /api-docs, /openapi.json and /swagger.json all return the single-page-application shell rather than any contract. The listing, sold-history and valuation backend at housesigma.com/bkv2/api/ is private, keyless, undocumented, and explicitly disallowed to all crawlers in robots.txt. The one genuinely public, anonymously callable, machine-readable HTTP surface the company operates is the WordPress REST API behind housesigma.com/blog-en, which serves its Canadian housing-market analysis blog as JSON across 157 advertised routes; API Evangelist derived an OpenAPI for the 22 operations verified to answer anonymously. HouseSigma also publishes a real llms.txt and mobile deep-link association documents. RESO is absent: HouseSigma is not among the Canadian organizations RESO lists as members, and no Web API or Data Dictionary certification, OData $metadata document, or Universal Property Identifier usage was found. No open, unlicensed dataset is published. The underlying listing and sold data is board-licensed and reaches HouseSigma through its own brokerage membership, not through anything a third-party developer can sign up for.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/housesigma/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/housesigma/refs/heads/main/apis.yml)

## Tags

- Real Estate
- Canada
- Property Listings
- MLS
- Valuation
- AVM
- PropTech
- Rentals
- Blog
- Content
- WordPress
- oEmbed
- Ontario
- British Columbia
- Toronto

## Timestamps

- **Created:** 2026-07-26
- **Modified:** 2026-07-26

## APIs

The one public, anonymously callable, machine-readable HTTP surface HouseSigma operates is the **HouseSigma Blog Content API** — the WordPress REST API (`wp/v2`) behind `housesigma.com/blog-en`, which serves the company's Canadian housing-market analysis blog as JSON.

- **Human URL:** https://housesigma.com/blog-en/
- **Base URL:** https://housesigma.com/blog-en/wp-json
- **Discovery document:** https://housesigma.com/blog-en/wp-json/ — HTTP 200, 157 routes across 8 namespaces (`wp/v2`, `oembed/1.0`, `basepress_kb/v1`, `contact-form-7/v1`, `saswp-output`, `yoast/v1`, `wp-site-health/v1`, `wp-block-editor/v1`)
- **OpenAPI:** [`openapi/housesigma-blog-content-openapi.yml`](openapi/housesigma-blog-content-openapi.yml) — OpenAPI 3.1.0, 22 operations, **derived by API Evangelist** from that live discovery document. Every path, parameter, type, default and bound is copied from it; nothing is invented. Only routes verified to return HTTP 200 to an anonymous request are included.

This is **not** an official HouseSigma developer product. HouseSigma documents nothing, supports nothing, and issues no keys — it is the standard WordPress REST API left enabled on the company's blog host.

The company's actual product data — listings, sold-price history, and the SigmaEstimate machine-learning valuation — is served only by the private backend at `https://housesigma.com/bkv2/api/`, which is undocumented, keyless, and explicitly disallowed to all crawlers in `robots.txt`. It is an implementation detail of the HouseSigma web and mobile apps, not a developer product, and is deliberately **not** listed in `apis.yml`.

## Artifacts

| Artifact | File | Method |
|---|---|---|
| OpenAPI (Blog Content API, 22 ops) | `openapi/housesigma-blog-content-openapi.yml` | derived |
| Route-discovery source document | `discovery/housesigma-blog-wp-json-index.json` | searched |
| llms.txt (published by HouseSigma) | `llms/housesigma-llms.txt` | searched |
| Well-known index + raw documents | `well-known/` | searched |
| Live request/response examples | `examples/` | searched |
| Error catalog | `errors/housesigma-problem-types.yml` | searched |
| API conventions | `conventions/housesigma-conventions.yml` | derived |
| Data model / ERD | `data-model/housesigma-data-model.yml` | derived |
| Authentication profile | `authentication/housesigma-authentication.yml` | derived |
| Lifecycle | `lifecycle/housesigma-lifecycle.yml` | searched |
| Conformance | `conformance/housesigma-conformance.yml` | derived |
| Embedded components (oEmbed + deep links) | `components/housesigma-components.yml` | searched |
| Agent skills | `skills/` | generated |
| OpenAPI overlay | `overlays/housesigma-blog-content-overlay.yaml` | generated |
| Agentic access contracts | `agentic-access/housesigma-agentic-access.yml` | generated |
| MCP candidate tool design (no server exists) | `mcp/housesigma-mcp.yml` | derived |
| Domain security probe | `security/housesigma-domain-security.yml` | probed |

**Not present, and why.** No `packages/` (zero first-party libraries on npm, PyPI, RubyGems, crates.io or Packagist). No `scopes/` (no OAuth anywhere). No `asyncapi/` (no event, streaming or webhook surface on any host). No `sandbox/`, `cli/`, or `changelog/` (none published). No `security/` vulnerability-disclosure or trust-center file (`/.well-known/security.txt` 404s; `trust.housesigma.com` does not resolve; no named certification is published). No `MCPServer` pointer is wired, because HouseSigma operates no MCP server.

## RESO Posture

**Not RESO-certified. No RESO reference found.**

RESO's own [Canadian Membership](https://www.reso.org/canadian-membership/) page lists 19 Canadian member organizations — including CREA, Centris, MPAC, the Real Estate Board of Greater Vancouver, and the REALTORS® Association of Edmonton — and HouseSigma is not among them. No RESO Web API certification, no Data Dictionary certification or version, no OData `$metadata` document, and no Universal Property Identifier (UPI) usage was observed. This is the expected Canadian answer: RESO certification is a US industry mandate driven by NAR, while Canadian residential listings flow through CREA's national Data Distribution Facility (DDF) — a route HouseSigma's `robots.txt` references and disallows at `/bkv2/landing/rootpage/ddf`.

## Access Gate

**`none-published`.** There is nothing for a developer to sign or join, because nothing is on offer. No self-serve signup, no application form, no partner page, no data-licensing page, no API terms. The listing and sold data behind the product is board-licensed and reaches HouseSigma through its own status as a licensed Canadian brokerage with MLS/board membership — a corporate posture, not a developer onboarding path. A third party seeking this data must become a member brokerage or go to CREA's DDF instead.

## Open Data

**None.** No open, unlicensed, publicly callable dataset. The sitemaps declared in `robots.txt` are SEO crawl indexes of HTML pages, not a data product. Canada has no counterpart to HM Land Registry Price Paid or Ordnance Survey open data — provincial land registration is largely privatised, with Teranet operating Ontario's registry under long concession, so even the public record is a commercial product.

## Auth Model

**None published.** No API key programme, no OAuth 2.0 or OpenID Connect developer flow, no SAML member portal. `/.well-known/openid-configuration`, `/.well-known/oauth-authorization-server`, `/.well-known/oauth-protected-resource`, `/.well-known/api-catalog` and `/.well-known/security.txt` all return HTTP 404. The public Blog Content API requires no credentials at all; its discovery document advertises WordPress application passwords over HTTP Basic for write methods, which HouseSigma issues to nobody outside the company. The consumer site uses ordinary session-based account sign-in for watchlists and estimates; the private `/bkv2/api/` backend sets `access-control-allow-credentials: true`, consistent with first-party cookie/session auth for its own apps.

## Webhooks, Events, SDKs, Postman

None found — the absence is itself the finding. No webhook or event documentation (no AsyncAPI, no event catalog, no callback surface on any host), no published SDK (zero packages matching `housesigma` on npm, PyPI, RubyGems, crates.io or Packagist), and no Postman workspace or collection. The [GitHub organization](https://github.com/housesigma) holds four public repositories (`openmaptiles` fork, `hr-interview`, `atlas`, `listing-chatbot-design`), none of which is an API specification or client library.

## Common Properties

- [AgenticAccess](agentic-access/housesigma-agentic-access.yml)
- [DomainSecurity](security/housesigma-domain-security.yml)
- [Authentication](authentication/housesigma-authentication.yml)
- [Website](https://housesigma.com/)
- [Blog](https://housesigma.com/blog-en/)
- [BlogRSS](https://housesigma.com/blog-en/feed/)
- [GitHubOrganization](https://github.com/housesigma)
- [LinkedIn](https://www.linkedin.com/company/housesigma)
- [LLMsTxt](llms/housesigma-llms.txt)
- [WellKnown](well-known/housesigma-well-known.yml)
- [Conventions](conventions/housesigma-conventions.yml)
- [ErrorCatalog](errors/housesigma-problem-types.yml)
- [Lifecycle](lifecycle/housesigma-lifecycle.yml)
- [Conformance](conformance/housesigma-conformance.yml)
- [DataModel](data-model/housesigma-data-model.yml)
- [Components](components/housesigma-components.yml)
- [AgentSkill](skills/_index.yml)
- [Examples](examples/)
- [Overlay](overlays/housesigma-blog-content-overlay.yaml)
- [TermsOfService](https://housesigma.com/blog-en/2018/04/25/terms-of-use/)
- [PrivacyPolicy](https://housesigma.com/blog-en/2018/04/25/privacy-policy/)
- [Support](https://housesigma.com/blog-en/contact-us/)
- [FAQ](https://housesigma.com/blog-en/faq/)
- [About](https://housesigma.com/blog-en/about-us/)
- [Careers](https://team.housesigma.com/)
- [iOSApp](https://itunes.apple.com/ca/app/toronto-real-estate-housesigma/id1255490256?mt=8)
- [AndroidApp](https://play.google.com/store/apps/details?id=com.housesigma.android&hl=en_CA)
- [Facebook](https://www.facebook.com/housesigma/)
- [Instagram](https://www.instagram.com/housesigma/)

## Maintainers

- **Kin Lane** — kin@apievangelist.com
