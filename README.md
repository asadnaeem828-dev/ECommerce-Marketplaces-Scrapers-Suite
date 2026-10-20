# E-Commerce Marketplaces & Merchant Lead Scrapers Suite

[![Apify Partner](https://img.shields.io/badge/Apify-Official%20Developer%20Partner-0083FE?logo=apify&logoColor=white)](https://apify.com/automation_studio)
[![Category](https://img.shields.io/badge/Category-E--Commerce%20%26%20Retail-green)](https://apify.com/automation_studio)
[![Scrapers Count](https://img.shields.io/badge/Scrapers%20Included-9%20Production%20Actors-brightgreen)](https://apify.com/automation_studio)
[![Sample Dataset](https://img.shields.io/badge/Dataset-Verified%20CSV%20Sample-success)](./sample_leads.csv)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

Official enterprise monorepo housing **9 production data extraction actors** deployed on [Apify](https://apify.com/automation_studio).

Every scraper in this suite provides accredited member directories, clean decision-maker contacts, real-time listing feeds, and automated exports to CSV, JSON, and Excel.

---

## 🏛️ Included Scrapers Directory (9 Actors)

| Scraper / Actor Title | Capability Overview | Apify Console | Store Page |
|---|---|---|---|
| **FlipLead AI - Fashion Resale & Vintage Arbitrage Scraper** | High-velocity data extraction and verified lead scraper on Apify.... | [Run on Apify](https://console.apify.com/actors/F4ZCPiWfToARLFdKS) | [Store Page](https://apify.com/automation_studio/vinted-depop-poshmark-scraper) |
| **SurplusLead AI - GovDeals & Surplus Auction Tracker** | High-velocity data extraction and verified lead scraper on Apify.... | [Run on Apify](https://console.apify.com/actors/M93TEVxI3VSlvEnmg) | [Store Page](https://apify.com/automation_studio/govdeals-surplus-auction-scraper) |
| **Amazon Trend Finder: Hot New Releases & Breakout Products** | High-velocity data extraction and verified lead scraper on Apify.... | [Run on Apify](https://console.apify.com/actors/gRgWIPtEfDM5klMgE) | [Store Page](https://apify.com/automation_studio/amazon-trend-product-finder) |
| **Amazon KDP Profitable Niche Detector & BSR Sales Calculator** | High-velocity data extraction and verified lead scraper on Apify.... | [Run on Apify](https://console.apify.com/actors/VrMqG5S1LiYOo9maI) | [Store Page](https://apify.com/automation_studio/amazon-kdp-niche-detector) |
| **⌚ Chrono24 Luxury Watch Arbitrage & Deal Finder** | High-velocity data extraction and verified lead scraper on Apify.... | [Run on Apify](https://console.apify.com/actors/05ILPal9vGliwcBih) | [Store Page](https://apify.com/automation_studio/chrono24-watch-arbitrage-finder) |
| **Amazon Best Sellers Scraper** | High-velocity data extraction and verified lead scraper on Apify.... | [Run on Apify](https://console.apify.com/actors/sXrmN7hBVfdZzsq5h) | [Store Page](https://apify.com/automation_studio/amazon-bestsellers-scraper) |
| **eBay Sold & Completed Items - Real-Time Price Arbitrage Scraper** | High-velocity data extraction and verified lead scraper on Apify.... | [Run on Apify](https://console.apify.com/actors/TuOGB98eQzedQXf01) | [Store Page](https://apify.com/automation_studio/ebay-sold-comps-scraper) |
| **Shopify Tech Stack & Sales Opportunity Scraper** | High-velocity data extraction and verified lead scraper on Apify.... | [Run on Apify](https://console.apify.com/actors/P1Asro4v0Biyub4kQ) | [Store Page](https://apify.com/automation_studio/shopify-opportunity-scanner) |
| **Liquidation & Pallet Auction Scanner** | High-velocity data extraction and verified lead scraper on Apify.... | [Run on Apify](https://console.apify.com/actors/7m3JtPwi18SZNHeHS) | [Store Page](https://apify.com/automation_studio/pallet-liquidation-scanner) |

---

## 🔑 How to Get Your Free Apify API Token

To run any scraper in this suite programmatically or integrate it into your automated sales pipeline:

1. **Sign Up for Free**: Visit [Apify Signup](https://apify.com/) and create a free account. Every new account includes **$5 of free platform credits every month** (enough to run thousands of scrape queries).
2. **Access Your API Settings**: Once logged in, go directly to the [Apify Console Integrations Page](https://console.apify.com/account/integrations).
3. **Copy Your Personal API Token**: Under **API tokens**, click the copy icon next to your **Personal API Token**.
4. **Authenticate in Code**: Pass your token via the `APIFY_TOKEN` environment variable or directly in the client initialization:
   ```python
   from apify_client import ApifyClient
   client = ApifyClient("your_personal_api_token_here")
   ```

---

## ⚡ Quickstart: Programmatic Extraction (Python)

Run any actor from this suite using Python and the official `apify-client` package:

```python
from apify_client import ApifyClient
import pandas as pd

# 1. Initialize Apify client with your API token
client = ApifyClient("YOUR_APIFY_API_TOKEN")

# 2. Run your chosen actor on Apify Cloud
run = client.actor("automation_studio/vinted-depop-poshmark-scraper").call(
    run_input={
        "maxResults": 500,
        "requireEmail": True
    }
)

# 3. Fetch verified lead items from the default dataset
items = client.dataset(run["defaultDatasetId"]).list_items().items
print(f"Extracted {len(items)} verified records.")

# 4. Save directly to CSV or load into pandas
df = pd.DataFrame(items)
df.to_csv("leads_output.csv", index=False)
```

### Direct cURL Command

```bash
curl -X POST "https://api.apify.com/v2/acts/automation_studio~vinted-depop-poshmark-scraper/runs?token=YOUR_API_TOKEN" \
     -H "Content-Type: application/json" \
     -d '{"maxResults": 250, "requireEmail": true}'
```

---

## 📊 Sample Dataset Preview

The repository includes [`sample_leads.csv`](./sample_leads.csv) demonstrating the verified 15-column schema:

| Field Name | Type | Description |
|---|---|---|
| `Company Name` | String | Legal corporate or registered trading name |
| `Trade Member ID` | String | Official accreditation identifier or business ID |
| `Primary Email` | String | Validated corporate or sales inquiry email (RFC 5322) |
| `Telephone` | String | Direct business phone with national dialing code (E.164) |
| `Website` | String | Official corporate web address |
| `Street Address` | String | Verified operational facility or corporate headquarters |
| `City` / `State` / `Country` | String | Standardized geographic coordinates |
| `Postal Code` | String | National ZIP or postal routing code |
| `Specializations` | String | Core capabilities and trade tags |
| `Executive Contact` | String | Key decision-maker or managing director |
| `Job Title` | String | Executive functional role |
| `LinkedIn URL` | String | Official corporate LinkedIn profile page |
| `Lead Quality Score` | Integer | Automated composite verification rating (90-100) |

---

## 🛡️ License & Commercial Terms

This repository code is licensed under the [MIT License](./LICENSE). When utilizing scraped data for cold outreach, ensure full compliance with regional regulations including CAN-SPAM, GDPR, and CASL.

- **Developer Profile**: [@automation_studio](https://apify.com/automation_studio)
- **Portfolio Hub**: [asadnaeem828-dev](https://github.com/asadnaeem828-dev)