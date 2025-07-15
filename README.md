# 🏘️ Rightmove Property Scraper (Showcase Version)

This repository showcases a powerful, custom-built Python scraper that dynamically collects property listings from **Rightmove's live "For Sale" and "To Rent" sections** using nothing more than **postcodes** as input.

The actual logic has been redacted to protect proprietary techniques, but this showcase demonstrates the scraper’s **modular architecture**, **intelligent design**, and a deep understanding of how Rightmove internally structures its listings — particularly through their use of hidden `locationIdentifier` tokens.

---

## 🚀 What This Code Demonstrates

- 💡 **Live `locationIdentifier` resolution**
  - Rightmove listings are powered by a `locationIdentifier` code — an internal, dynamically-generated string that most scrapers ignore or hardcode.
  - This system automatically accesses the **Rightmove House Prices page** for a postcode and parses the JavaScript to extract a **working location ID**, enabling robust and postcode-only      scraping.
  - This makes the tool highly **scalable**, adaptable to **any UK postcode**, and avoids reliance on outdated or manual data.

- 🔗 **Accurate URL construction**
  - From the extracted ID, it builds:
    - A valid "For Sale" listings URL
    - A valid "To Rent" listings URL
  - These links are then passed into the core scraping logic to retrieve all current property cards.

- 🧠 **Smart listing scraping**
  - Scrapes every listing in a postcode from the search results page.
  - Filters and collects only valid property URLs using `propertyCard-link` anchors.
  - Extracts unique property IDs to compare against existing Excel entries.

- 📊 **Excel-aware integration**
  - Connects directly to internal stock register files (.xlsx) using `openpyxl`
  - Each property is matched against an Excel sheet by postcode
  - **Missing entries are appended** with scraped data: price, agent, floor level, size (sq ft), listing date
  - **Existing entries are updated** if prices or data have changed, while preserving manually added square footage where applicable

- 🧱 **Fully modular structure**
  - The code is split into clean, testable functions:
    - `get_location_id()` → fetches the unique ID per postcode
    - `setup()` → builds usable Rightmove URLs
    - `scrape_links()` → gathers all listing links
    - `check_and_add_links()` → compares Excel vs scraped data
    - Parsing helpers: `agent()`, `floor()`, `bedroom()`, `price()`, `size()`, `date()`

- 🧪 **Robust handling**
  - Includes retry logic with exponential backoff to handle failed requests
  - Avoids re-scraping the same data
  - Skips irrelevant floor references like "residents’ gym on floor 32"

---

## 🔍 Why `locationIdentifier` Matters

Rightmove does **not** index listings by postcode alone. Instead, each search query requires an encoded `locationIdentifier`, like:

https://www.rightmove.co.uk/property-for-sale/find.html?locationIdentifier=POSTCODE^1387867


Many scrapers:
- Miss listings because they skip this step
- Rely on outdated or hardcoded location identifiers
- Only work for limited regions

This scraper solves that by:
- Visiting the *House Prices* page for a postcode
- Parsing the HTML to extract the correct `locationIdentifier`
- Dynamically building **both sale and rental URLs**

This approach ensures **full postcode coverage** and **future-proofing**, regardless of Rightmove’s front-end changes.

---

## ❌ Not Included (By Design)

- ❗ Actual Excel file paths (confidential internal locations)
- ❗ Full parsing and request logic (proprietary system)
- ❗ Live credentials, scheduling, or internal workflows

---

## ✅ What You Can Learn from This

This project is a showcase of how to:

- **Reverse-engineer modern web apps** like Rightmove
- Extract **hidden data** like `locationIdentifier` for dynamic URL creation
- Build modular, production-ready scrapers with `requests`, `BeautifulSoup`, `re`, and `openpyxl`
- Handle real-world issues like rate limiting, HTML changes, and Excel preservation logic
- Create a bridge between public data sources and structured internal tools

---
