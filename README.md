# Uniqlo Global Price Comparison

Compare Uniqlo product prices across different countries to find the best deals before you travel.

Ever wondered whether to buy that AIRism shirt at home or wait until you land? This project scrapes Uniqlo product prices from multiple country websites, normalizes currencies, and presents a side-by-side comparison so you can shop smarter.

### Background
I personally like to travel to different countries especially the ones that are near to my country (I am from the Philippines). And since I also like shopping, it's a perfect combination to shop while you are in another country. You get to see better deals, unique products and so much more. Here in my country, the Uniqlo brand is very common and popular. There are lots of branches over the country. I like Uniqlo too - they're basic staple pieces that you can mix and match in your wardrobe. So as a shopper and a traveller, I want to get the good deals. There is always that question that I ask myself before travelling - should I buy clothes here or in the country I'm going to? 

After years of travelling, I want to break that dilemma. Hence, the birth of this tool. As of this writing, I will be travelling to Hong Kong in a few days. That is why the first scope is HK prices versus PH prices.

### Current scope
Philippines vs Hong Kong - with plans to expand to Japan, Taiwan, China, Malaysia, and more. 
Philippine Peso (PHP) will be the common currency, but there are plans to make it to USD or to a currency of your choice.

### What this project does
- Scrapes product data (prices, discounts, categories) from Uniqlo country websites
- Normalizes prices to a common currency (PHP for now) using daily exchange rates
- Matches the same product across countries using product IDs
- Identifies which country is cheaper for each item
- Tracks price changes over time to spot seasonal sales
- Presents everything through a Power BI dashboard and a static website

### Tech Stack
| Layer | Technology |
|---|---|
| Ingestion | Microsoft Fabric Notebooks (Python) |
| Storage | Fabric Lakehouse (Delta tables, medallion architecture) |
| Transformation | Fabric Notebooks (PySpark / Pandas) |
| Visualization | Power BI (PBIP format, version-controlled) |
| Web frontend | GitHub Pages (HTML/JS + Chart.js) |
| Orchestration | Fabric Data Pipeline |
> **Phase B (planned):** Rebuild the pipeline using PostgreSQL + Python + dbt + GitHub Actions as an open-source alternative.

### Architecture
The pipeline follows a medallion architecture (Bronze → Silver → Gold):

1. Bronze: Raw scraped data, stored as-is for traceability
2. Silver: Cleaned and standardized product tables with consistent schema
3. Gold: Final comparison tables with price differences and winner flags

### Project Status
| Phase | Description | Status |
|---|---|---|
| 0 | Manual Excel recon (PH vs HK) | **In progress** |
| 1 | API discovery and data recon | ⬚ Not started |
| 2 | Lakehouse setup + Bronze ingestion | ⬚ Not started |
| 3 | Silver layer transformation | ⬚ Not started |
| 4 | Gold layer + comparison logic | ⬚ Not started |
| 5 | Pipeline orchestration | ⬚ Not started |
| 6 | Power BI dashboard (PBIP) | ⬚ Not started |
| 7 | GitHub Pages website | ⬚ Not started |

### Dashboard Preview
*Screenshots coming soon after Phase 6. Or a sample planned dashboard after Phase 4.*

Planned report pages:
- Overview: KPIs, which country wins by category, top savings opportunities
- Product comparison: Search and drill down into any product across countries
- Discount tracker: Items on sale, discount depth comparison, exclusive deals
- Cheapest finds: Top budget picks in each country, filterable by category
- Price trends: Historical price tracking over time

### How to use
Once the GitHub Pages site is live, visit: https://dencadizal.github.io/uniqlo-global-price-comparisons.

The final end goal is to have no Power BI license needed - the website will provide the full comparison for anyone.

### Planned Repository Structure
```
uniqlo-global-price-comparisons/
├── README.md
├── docs/                    # GitHub Pages site (Phase 7)
├── notebooks/               # Fabric notebooks
│   ├── nb_ingest.py         # Bronze layer ingestion
│   ├── nb_transform.py      # Silver layer transformation
│   └── nb_serve.py          # Gold layer comparison logic
├── pbip/                    # Power BI project (PBIP format)
│   ├── model/               # Semantic model (.tmdl)
│   └── report/              # Report layout (.pbir)
├── data/                    # Manual recon + sample data
│   └── manual_recon.xlsx    # Phase 0: Excel comparison
└── reference/               # API docs, architecture diagram
    └── uniqlo_price_compare_architecture.html
```

### About
Built by [Denisse Mae Cadizal](https://dencadizal.github.io/) as a data engineering portfolio project combining Microsoft Fabric, Power BI, and web development. Parts of web development are made with Claude AI. 

<sup>(This is my first time learning about markdowns here in Github README haha! This is written last 03/16/26)</sup>

### License
MIT

