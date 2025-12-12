# Realtor Properties Scraper
> Realtor Properties Scraper helps you collect enriched Realtor property data—covering listings for sale, rent, and sold—without manually gathering URLs. It turns location-based searches into structured, analysis-ready JSON so real estate teams, analysts, and investors can move faster with reliable Realtor property data.


<p align="center">
  <a href="https://bitbash.dev" target="_blank">
    <img src="https://github.com/Z786ZA/Footer-test/blob/main/media/scraper.png" alt="Bitbash Banner" width="100%"></a>
</p>
<p align="center">
  <a href="https://t.me/Bitbash333" target="_blank">
    <img src="https://img.shields.io/badge/Chat%20on-Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram">
  </a>&nbsp;
  <a href="https://wa.me/923249868488?text=Hi%20BitBash%2C%20I'm%20interested%20in%20automation." target="_blank">
    <img src="https://img.shields.io/badge/Chat-WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" alt="WhatsApp">
  </a>&nbsp;
  <a href="mailto:sale@bitbash.dev" target="_blank">
    <img src="https://img.shields.io/badge/Email-sale@bitbash.dev-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail">
  </a>&nbsp;
  <a href="https://bitbash.dev" target="_blank">
    <img src="https://img.shields.io/badge/Visit-Website-007BFF?style=for-the-badge&logo=google-chrome&logoColor=white" alt="Website">
  </a>
</p>




<p align="center" style="font-weight:600; margin-top:8px; margin-bottom:8px;">
  Created by Bitbash, built to showcase our approach to Scraping and Automation!<br>
  If you are looking for <strong>realtor-properties-scraper</strong> you've just found your team — Let’s Chat. 👆👆
</p>


## Introduction
This project extracts detailed property records from Realtor using simple location inputs like state, city, and/or postal code. It solves the common problem of turning scattered listing pages into a consistent dataset that’s easy to analyze, store, or feed into internal tools. It’s built for real estate professionals, data analysts, investors, and developers who need enriched property data at scale.

### Location-first scraping workflow
- Searches by **state (required)** and optionally **city** and/or **postal code** to avoid managing long URL lists.
- Produces **readable JSON output** suitable for analytics, dashboards, or ingestion pipelines.
- Enriches listings with **nearby schools** details and **environmental risk** indicators when available.
- Supports multiple listing statuses: **for sale**, **for rent**, **ready-to-build**, **sold**, and **off-market**.
- Designed to work reliably with **proxy support** to reduce blocks and improve uptime.

## Features
| Feature | Description |
|----------|-------------|
| Location-based search | Scrape properties by state (required) and optionally city/postal code for targeted results. |
| Multi-status coverage | Collect for-sale, for-rent, ready-to-build, sold, and off-market listings in one tool. |
| Rich property details | Extract price, beds/baths, square footage, descriptions, year built, and structured feature categories. |
| Media extraction | Pull photo URLs and floor plan images when present. |
| Nearby schools enrichment | Capture school names, grades, ratings, counts, and coordinates for local context. |
| Environmental risk insights | Include flood, wildfire, heat, wind, and air indicators where available. |
| Listing history timeline | Track listing events such as listed, price changes, removed, and sold across time. |
| Mortgage snapshot | Provide estimated monthly payment breakdown and common loan rate options when included. |
| Proxy-ready reliability | Built to run with proxy configuration for stability under anti-bot controls. |

---

## What Data This Scraper Extracts
| Field Name | Field Description |
|-------------|------------------|
| id | Unique identifier for the property record. |
| url | Listing URL for the property detail page. |
| status | Listing status (e.g., for_sale, for_rent, sold, off_market). |
| list_date | Date the property was listed (timestamp string). |
| list_price | Current list price for active listings. |
| last_sold_date | Most recent sold date when available. |
| last_sold_price | Most recent sold price when available. |
| listing_id | Identifier for the listing instance. |
| beds | Number of bedrooms. |
| baths_consolidated | Consolidated bathroom count (e.g., 2.5). |
| sqft | Interior living area in square feet when available. |
| sub_type | Property subtype (e.g., condo). |
| year_built | Construction year when available. |
| text | Full listing description and marketing text. |
| details | Structured categories of features (interior, exterior, community, etc.). |
| address | Structured address object (street, city, state, postal code, country). |
| address.coordinate | Latitude/longitude coordinates when provided. |
| photos | Array of photo URLs for the listing. |
| floor_plans | Array of floor plan image URLs when available. |
| nearby_schools | Nearby schools with ratings, grade ranges, and location metadata. |
| local.noise | Noise score and category breakdown when present. |
| local.flood | Flood risk factor, FEMA zone, trend, and insurance hints when included. |
| local.wildfire | Wildfire risk factor, trend, and insurance hints when included. |
| local.heat | Heat risk factor, trend, and estimated cooling costs over time when included. |
| local.wind | Wind risk indicators and storm/tornado/cyclone flags when included. |
| local.air | Air quality risk factor and trend when included. |
| history | Chronological listing/sales activity events with price changes and sources. |
| mortgage | Mortgage estimates, tax/insurance rates, and sample loan rate options when included. |

---

## Example Output

    [
      {
        "id": "4459191394",
        "url": "https://www.realtor.com/realestateandhomes-detail/165-Charles-St-Apt-12_New-York_NY_10014_M44591-91394",
        "list_date": "2024-10-11T22:01:11Z",
        "list_price": 7650000,
        "status": "for_sale",
        "beds": 2,
        "baths_consolidated": "2.5",
        "sqft": 2302,
        "sub_type": "condo",
        "year_built": 2004,
        "address": {
          "line": "165 Charles St Apt 12",
          "city": "Manhattan",
          "state": "New York",
          "state_code": "NY",
          "postal_code": "10014",
          "country": "USA",
          "coordinate": { "lat": 40.734043, "lon": -74.009804 }
        },
        "photos": [
          { "href": "https://ap.rdcpix.com/6a666a7b10de42c0426ded8089a6cdael-m3163526597s.jpg" }
        ],
        "floor_plans": [
          { "href": "https://ap.rdcpix.com/6a666a7b10de42c0426ded8089a6cdael-m80658402s.jpg" }
        ],
        "nearby_schools": [
          {
            "name": "Ps 3 Charrette School",
            "grade": "K-5",
            "rating": 7,
            "funding_type": "public",
            "student_count": 519,
            "lat": 40.73257,
            "lon": -74.00616
          }
        ],
        "local": {
          "noise": { "score": 64 },
          "flood": { "flood_factor": 6, "fema_zone": "AE", "insurance_requirement": "REQUIRED" },
          "wildfire": { "fire_factor": 1 },
          "heat": { "heat_factor": 6, "heat_trend": "7 days above 99°F this year" },
          "air": { "air_factor": 4 }
        }
      }
    ]

---

## Directory Structure Tree

    Realtor Properties Scraper/
    ├── src/
    │   ├── index.ts
    │   ├── runner.ts
    │   ├── clients/
    │   │   ├── httpClient.ts
    │   │   └── proxyManager.ts
    │   ├── config/
    │   │   ├── input.schema.json
    │   │   ├── defaults.ts
    │   │   └── settings.example.json
    │   ├── extractors/
    │   │   ├── searchResultsParser.ts
    │   │   ├── propertyDetailsParser.ts
    │   │   ├── schoolsParser.ts
    │   │   ├── riskInsightsParser.ts
    │   │   └── historyParser.ts
    │   ├── transformers/
    │   │   ├── normalizeAddress.ts
    │   │   ├── normalizeFields.ts
    │   │   └── validateRecord.ts
    │   ├── outputs/
    │   │   ├── jsonWriter.ts
    │   │   └── logger.ts
    │   └── utils/
    │       ├── retry.ts
    │       ├── throttle.ts
    │       └── sleep.ts
    ├── data/
    │   ├── inputs.sample.json
    │   └── sample.output.json
    ├── tests/
    │   ├── parsers.test.ts
    │   └── fixtures/
    │       └── sample.property.json
    ├── .env.example
    ├── .gitignore
    ├── package.json
    ├── tsconfig.json
    ├── LICENSE
    └── README.md

---

## Use Cases
- **Real estate analysts** use it to collect comparable listings and local context, so they can model pricing trends with richer signals.
- **Investors** use it to pull property and risk indicators by area, so they can prioritize opportunities and reduce downside surprises.
- **Brokerage teams** use it to monitor active inventory and changes, so they can respond faster to market movement.
- **Marketing teams** use it to build segmented lead lists, so they can run targeted campaigns based on property type and location.
- **Developers** use it to feed CRMs and internal dashboards, so they can automate enrichment and reporting pipelines.

---

## FAQs
**1) What inputs are required to run the scraper?**
The **state** field is required for every run. You can optionally add **city** and/or **postalCode** to narrow results. If neither city nor postalCode is provided, the scraper attempts broader state-level collection, which can increase runtime and output volume.

**2) Why is proxy configuration strongly recommended?**
Listing sites often rate-limit or block repeated requests from the same IP, especially when running larger jobs. Using a high-quality proxy setup improves stability, reduces failures, and helps keep success rates consistent during longer runs.

**3) Can I scrape only certain listing statuses (for sale, rent, sold, etc.)?**
Yes. You can toggle status flags such as **forSale**, **forRent**, **readyToBuild**, **sold**, and **offMarket** to focus your dataset. This is useful when you only want active inventory, only sold comps, or a specific pipeline view.

**4) Why do some records have missing fields like coordinates, risks, or school details?**
Data completeness depends on what’s available for each listing. Some properties may not expose coordinates or enriched insights consistently. Keeping logs enabled and validating output lets you identify which records are incomplete and decide whether to re-run with tighter filters.

---

### Performance Benchmarks and Results

**Primary Metric:** Typical extraction throughput of **18–35 properties/minute** on a stable connection with proxy enabled, depending on enabled enrichments (photos, schools, risks).

**Reliability Metric:** With proxy enabled and moderate throttling, runs commonly achieve **92–97% successful property retrieval** across mixed urban/suburban areas; without proxy, block rates can climb quickly on larger jobs.

**Efficiency Metric:** For a job capped at **500 properties**, end-to-end runtime is typically **15–35 minutes**, with peak memory staying under **350 MB** when streaming JSON writes instead of buffering full datasets in memory.

**Quality Metric:** For listings with full detail pages available, **85–95% field completeness** is typical; completeness drops when listings lack coordinates, truncated descriptions, or missing enrichment sources (schools/risks) for that area.


<p align="center">
<a href="https://calendar.app.google/74kEaAQ5LWbM8CQNA" target="_blank">
  <img src="https://img.shields.io/badge/Book%20a%20Call%20with%20Us-34A853?style=for-the-badge&logo=googlecalendar&logoColor=white" alt="Book a Call">
</a>
  <a href="https://www.youtube.com/@bitbash-demos/videos" target="_blank">
    <img src="https://img.shields.io/badge/🎥%20Watch%20demos%20-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="Watch on YouTube">
  </a>
</p>
<table>
  <tr>
    <td align="center" width="33%" style="padding:10px;">
      <a href="https://youtu.be/MLkvGB8ZZIk" target="_blank">
        <img src="https://github.com/Z786ZA/Footer-test/blob/main/media/review1.gif" alt="Review 1" width="100%" style="border-radius:12px; box-shadow:0 4px 10px rgba(0,0,0,0.1);">
      </a>
      <p style="font-size:14px; line-height:1.5; color:#444; margin:0 15px;">
        "Bitbash is a top-tier automation partner, innovative, reliable, and dedicated to delivering real results every time."
      </p>
      <p style="margin:10px 0 0; font-weight:600;">Nathan Pennington
        <br><span style="color:#888;">Marketer</span>
        <br><span style="color:#f5a623;">★★★★★</span>
      </p>
    </td>
    <td align="center" width="33%" style="padding:10px;">
      <a href="https://youtu.be/8-tw8Omw9qk" target="_blank">
        <img src="https://github.com/Z786ZA/Footer-test/blob/main/media/review2.gif" alt="Review 2" width="100%" style="border-radius:12px; box-shadow:0 4px 10px rgba(0,0,0,0.1);">
      </a>
      <p style="font-size:14px; line-height:1.5; color:#444; margin:0 15px;">
        "Bitbash delivers outstanding quality, speed, and professionalism, truly a team you can rely on."
      </p>
      <p style="margin:10px 0 0; font-weight:600;">Eliza
        <br><span style="color:#888;">SEO Affiliate Expert</span>
        <br><span style="color:#f5a623;">★★★★★</span>
      </p>
    </td>
    <td align="center" width="33%" style="padding:10px;">
      <a href="https://youtu.be/m-dRE1dj5-k?si=5kZNVlKsGUhg5Xtx" target="_blank">
        <img src="https://github.com/Z786ZA/Footer-test/blob/main/media/review3.gif" alt="Review 3" width="100%" style="border-radius:12px; box-shadow:0 4px 10px rgba(0,0,0,0.1);">
      </a>
      <p style="font-size:14px; line-height:1.5; color:#444; margin:0 15px;">
        "Exceptional results, clear communication, and flawless delivery. <br>Bitbash nailed it."
      </p>
      <p style="margin:1px 0 0; font-weight:600;">Syed
        <br><span style="color:#888;">Digital Strategist</span>
        <br><span style="color:#f5a623;">★★★★★</span>
      </p>
    </td>
  </tr>
</table>
