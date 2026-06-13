# Agify.io

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
