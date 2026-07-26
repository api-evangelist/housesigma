# HouseSigma (housesigma)

HouseSigma, Inc. Brokerage is a Toronto-based Canadian residential real estate portal and licensed brokerage that pairs map-based MLS listing search with sold-price history and machine-learning home valuations across Ontario, British Columbia, and Alberta. It sits in the challenger layer of the Canadian value chain, below CREA, which operates REALTOR.ca and the national Data Distribution Facility (DDF) that syndicates member boards' listings, and alongside Wahi, Zolo, and Properly, competing on visibility into data the boards control, a position it won in part through the Competition Bureau litigation that forced TRREB to release sold data in 2018. Its API posture is closed. There is no developer portal, no published API program, and no partner or data-licensing page. The subdomains developer., developers., and docs.housesigma.com do not resolve in DNS, and /developers, /api, /api-docs, /openapi.json and /swagger.json all return the single-page-application shell rather than any contract. The only machine surface is housesigma.com/bkv2/api/, the private backend that powers the web and mobile apps, which the site's own robots.txt explicitly disallows to all crawlers and which publishes no documentation, terms, keys, or versioned contract. RESO is absent. HouseSigma does not appear among the Canadian organizations RESO lists as members, and no Web API or Data Dictionary certification, OData $metadata document, or Universal Property Identifier usage was found. No open, unlicensed dataset is published. The underlying listing and sold data is board-licensed and reaches HouseSigma through its own brokerage membership, not through anything a third-party developer can sign up for.

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

## Timestamps

- **Created:** 2026-07-26
- **Modified:** 2026-07-26

## APIs

No public, documented APIs. HouseSigma publishes no developer portal, no API program, and no machine-readable contract of any kind. The only machine surface found is the private, undocumented backend at `https://housesigma.com/bkv2/api/`, which the site's own `robots.txt` disallows to all crawlers — it is an implementation detail of the HouseSigma web and mobile apps, not a developer product, and is therefore not listed here.

## RESO Posture

**Not RESO-certified. No RESO reference found.**

RESO's own [Canadian Membership](https://www.reso.org/canadian-membership/) page lists 19 Canadian member organizations — including CREA, Centris, MPAC, the Real Estate Board of Greater Vancouver, and the REALTORS® Association of Edmonton — and HouseSigma is not among them. No RESO Web API certification, no Data Dictionary certification or version, no OData `$metadata` document, and no Universal Property Identifier (UPI) usage was observed. This is the expected Canadian answer: RESO certification is a US industry mandate driven by NAR, while Canadian residential listings flow through CREA's national Data Distribution Facility (DDF) — a route HouseSigma's `robots.txt` references and disallows at `/bkv2/landing/rootpage/ddf`.

## Access Gate

**`none-published`.** There is nothing for a developer to sign or join, because nothing is on offer. No self-serve signup, no application form, no partner page, no data-licensing page, no API terms. The listing and sold data behind the product is board-licensed and reaches HouseSigma through its own status as a licensed Canadian brokerage with MLS/board membership — a corporate posture, not a developer onboarding path. A third party seeking this data must become a member brokerage or go to CREA's DDF instead.

## Open Data

**None.** No open, unlicensed, publicly callable dataset. The sitemaps declared in `robots.txt` are SEO crawl indexes of HTML pages, not a data product. Canada has no counterpart to HM Land Registry Price Paid or Ordnance Survey open data — provincial land registration is largely privatised, with Teranet operating Ontario's registry under long concession, so even the public record is a commercial product.

## Auth Model

**None published.** No API key programme, no OAuth 2.0 or OpenID Connect developer flow, no SAML member portal. `/.well-known/openid-configuration` returns HTTP 404. The consumer site uses ordinary session-based account sign-in for watchlists and estimates; the private `/bkv2/api/` backend sets `access-control-allow-credentials: true`, consistent with first-party cookie/session auth for its own apps.

## Webhooks, Events, SDKs, Postman

None found — the absence is itself the finding. No webhook or event documentation, no published SDK, and no Postman workspace or collection. The [GitHub organization](https://github.com/housesigma) holds four public repositories (`openmaptiles` fork, `hr-interview`, `atlas`, `listing-chatbot-design`), none of which is an API specification or client library.

## Common Properties

- [Website](https://housesigma.com/)
- [Blog](https://housesigma.com/blog-en/)
- [Blog RSS](https://housesigma.com/blog-en/feed/)
- [GitHub Organization](https://github.com/housesigma)
- [LinkedIn](https://www.linkedin.com/company/housesigma)

## Maintainers

- **Kin Lane** — kin@apievangelist.com
