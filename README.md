# HouseSigma

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

HouseSigma, Inc. Brokerage is a Toronto-based Canadian residential real estate portal and licensed brokerage that pairs map-based MLS listing search with sold-price history and machine-learning home valuations (SigmaEstimate) across Ontario, British Columbia, and Alberta. It sits in the challenger layer of the Canadian value chain, below CREA, which operates REALTOR.ca and the national Data Distribution Facility (DDF) that syndicates member boards' listings, and alongside Wahi, Zolo, and Properly, competing on visibility into data the boards control, a position it won in part through the Competition Bureau litigation that forced TRREB to release sold data in 2018. Its API posture is closed. There is no developer portal, no published API program, and no partner or data-licensing page; developer., developers., and docs.housesigma.com do not resolve in DNS, and /developers, /api, /api-docs, /openapi.json and /swagger.json all return the single-page-application shell rather than any contract. The listing, sold-history and valuation backend at housesigma.com/bkv2/api/ is private, keyless, undocumented, and explicitly disallowed to all crawlers in robots.txt. The one genuinely public, anonymously callable, machine-readable HTTP surface the company operates is the WordPress REST API behind housesigma.com/blog-en, which serves its Canadian housing-market analysis blog as JSON across 157 advertised routes; API Evangelist derived an OpenAPI for the 22 operations verified to answer anonymously. HouseSigma also publishes a real llms.txt and mobile deep-link association documents. RESO is absent: HouseSigma is not among the Canadian organizations RESO lists as members, and no Web API or Data Dictionary certification, OData $metadata document, or Universal Property Identifier usage was found. No open, unlicensed dataset is published. The underlying listing and sold data is board-licensed and reaches HouseSigma through its own brokerage membership, not through anything a third-party developer can sign up for.

**Areas:** Real Estate · Canada · Property Listings · MLS · Valuation · AVM · PropTech · Rentals · Blog · Content · WordPress · oEmbed

## HouseSigma on APIs.io

Everything profiled for HouseSigma is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/housesigma/](https://apis.io/providers/housesigma/)** — or go straight to one of the APIs or properties below.

### APIs (1)

- [HouseSigma Website (WordPress REST)](https://apis.io/apis/housesigma/housesigma-com-blog-en-website-wordpress-rest/) — The public WordPress REST API (wp-json) of the HouseSigma website at housesigma.com/blog-en: the route index of the site's content management system,…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [housesigma-blog-content](https://apis.io/servers/housesigma/housesigma-blog-content/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Housesigma Agentic Access](https://apis.io/agentic-access/housesigma/housesigma-agentic-access/)

#### Examples (5)

Example requests and responses.

- [Housesigma Blog Content Error 400 Rest_Invalid_Param](https://apis.io/examples/housesigma/housesigma-blog-content-error-400-rest_invalid_param/)
- [Housesigma Blog Content Error 401 Rest_Forbidden](https://apis.io/examples/housesigma/housesigma-blog-content-error-401-rest_forbidden/)
- [Housesigma Blog Content Error 404 Rest_Post_Invalid_Id](https://apis.io/examples/housesigma/housesigma-blog-content-error-404-rest_post_invalid_id/)
- [Housesigma Blog Content Getoembed 200](https://apis.io/examples/housesigma/housesigma-blog-content-getOembed-200/)
- [Housesigma Blog Content Listtaxonomies 200](https://apis.io/examples/housesigma/housesigma-blog-content-listTaxonomies-200/)

#### Collections (1)

Postman and Open Collection request collections.

- [Moved to /providers/housesigma/](https://apis.io/collections/housesigma/open-housesigma-blog-content/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Housesigma Authentication](https://apis.io/security/housesigma/housesigma-authentication/)
- [Housesigma Domain Security](https://apis.io/security/housesigma/housesigma-domain-security/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://housesigma.com/)
- [Support](https://housesigma.com/blog-en/contact-us/)
- [Blog](https://housesigma.com/blog-en/)
- [Terms of service](https://housesigma.com/blog-en/2018/04/25/terms-of-use/)
- [Privacy policy](https://housesigma.com/blog-en/2018/04/25/privacy-policy/)
- [GitHub](https://github.com/housesigma)

## API Evangelist rating

**Kin Score 20.6** — emerging · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 64.3 |
| Contract quality | 6.5 |
| Contract governance | 4.5 |
| Operational transparency | 2.6 |
| Developer ergonomics | 30.4 |
| Access clarity | 21.1 |

**Agent readiness 9.4** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | — |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | documented (partial credit) |
| Rate Limit Signal | — |
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

**Regulatory alignment 24.5** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/housesigma/](https://apis.io/providers/housesigma/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for HouseSigma: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/housesigma/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
