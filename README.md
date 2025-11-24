# Torn-points-market-analysis
This repo tracks the prices of items used to earn points at the museum. It includes real-time pricing for various sets used to exchange points and for individual-item markets.
A small data analysis/dashboard project that estimates the cost of in-game item bundles (e.g. plushies/flowers → 10 points) using the Torn API and Excel Power Query. Useful for traders and for demonstrating API integration + valuation modelling.


---

## What this project contains
- `excel/torn_points_market_dashboard.xlsx` — Dashboard with sheets: `Plushies`, `Flowers`, 'coins', . Each sheet loads live data via Power Query and calculates:
  - Total cost to buy all individual items
  - Estimated cost for 10 points (based on in-game exchange set)
- `powerquery/` — Power Query (M) scripts and import instructions so you can paste queries into Excel.
- `data/sample_responses/` — sanitised example JSON responses for offline testing.
- `docs/screenshots/` — Dashboard screenshots.

---

## How to use (quick)
1. **Do not** share your Torn API key publicly. See *Config / API key* below.
2. Download or clone the repo.
3. Open `excel/torn_points_market_dashboard.xlsx`.
4. Create a local sheet/table named `TornAPIKey` and put your API key in it (see `README_EXCEL.md` for exact steps).
5. Go to `Data` → `Refresh All` to refresh the queries.
6. If Excel asks for privacy/authentication settings for the web source, approve as required.

---

## How to reuse the Power Query code
1. Open Excel → Data → Get Data → From Other Sources → Blank Query.
2. Advanced Editor → paste the content of `.m.txt`.
3. Replace placeholders or configure Excel named cells to feed `product_id` and `api_key`.
4. Close & Load.

Detailed step-by-step in `powerquery/import_instructions.md`.

---

## API key/config (security)
- **Do not** store API keys in the repo.
- Recommended: create an Excel named table `TornAPIKey` or use `config.ini` (ignored by git).
- If you accidentally commit a key, rotate it immediately.

---

## License


---

## Contact / Author
Bhumit Joshi - reach me at bhumitjoshi200@gmail.com
