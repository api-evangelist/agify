# Agify.io

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

Agify.io is a free REST API that predicts the age of a person based on their first name using statistical data from over one billion records spanning 195+ countries. The service is provided by Demografix ApS and shares a single API key with the companion Genderize.io and Nationalize.io APIs.

## Quick Start

```bash
# Single name lookup (free, no key required for initial test)
curl "https://api.agify.io?name=michael&apikey=YOUR_API_KEY"

# Response
# {"name":"michael","age":65,"count":298219}

# With country scoping
curl "https://api.agify.io?name=michael&country_id=US&apikey=YOUR_API_KEY"

# Batch lookup (up to 10 names per request)
curl "https://api.agify.io?name[]=alice&name[]=bob&name[]=charlie&apikey=YOUR_API_KEY"
```

## API Details

- **Base URL:** `https://api.agify.io`
- **Method:** GET
- **Authentication:** API key via `apikey` query parameter (obtain at agify.io/register)
- **Free Tier:** 2,500 names/month — no credit card required

## Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `name` | Yes | First name to predict age for |
| `apikey` | Yes | API key from your Agify account |
| `country_id` | No | ISO 3166-1 alpha-2 country code for localized predictions |

## Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `name` | string | The name as processed by the API |
| `age` | integer | Predicted age in years (null if insufficient data) |
| `count` | integer | Number of data records supporting the prediction |
| `country_id` | string | Returned when country scoping is applied |

## Rate Limit Headers

| Header | Description |
|--------|-------------|
| `X-Rate-Limit-Limit` | Total names allowed in the current monthly window |
| `X-Rate-Limit-Remaining` | Names remaining in the current window |
| `X-Rate-Limit-Reset` | Seconds until the quota window resets |

## Pricing

| Plan | Monthly Cost | Names/Month |
|------|-------------|-------------|
| Free | $0 | 2,500 |
| Standard | $60 | 250,000 |
| Enterprise | Custom | 25,000,000+ |

See [plans/agify-plans-pricing.yml](plans/agify-plans-pricing.yml) for full plan details.

## Links

- **Website:** https://agify.io
- **Documentation:** https://agify.io/documentation
- **API Reference:** https://agify.io/documentation/api/reference
- **Pricing:** https://agify.io/pricing
- **FAQ:** https://agify.io/faq
- **SDKs & Libraries:** https://agify.io/libraries
- **Data Coverage:** https://agify.io/our-data
- **Register:** https://agify.io/register

## Related APIs

Agify.io is part of the Demografix suite. The same API key works across all three:

- [Genderize.io](https://genderize.io) — predict gender from a name
- [Agify.io](https://agify.io) — predict age from a name
- [Nationalize.io](https://nationalize.io) — predict nationality from a name

## Company

**Demografix ApS**
Eriksvej 30, 4000 Roskilde, Denmark
Email: info@genderize.io

GDPR compliant. Submitted names are discarded immediately and never stored.

---

*This repository is an [APIs.json](https://apisjson.org) profile maintained by [API Evangelist](https://apievangelist.com).*
