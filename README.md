# Torn-points-market-analysis
This repo tracks the prices of items used to get points at the museum in Torn City. It includes real-time pricing and average market values for various sets and items used to exchange points, as well as for individual-item markets. It also contains a built-in query to extract data for any item in Torn.

NOTE - This is a small data analysis/dashboard project that shows the cost of in-game item sets (e.g. plushies/flowers → 10 points) using the Torn API and Excel Power Query. Useful for traders and for demonstrating API integration + valuation modelling.


## What this project contains
- `excel/torn_points_market_dashboard.xlsm` — Dashboard with sheets: 'Plushies', 'Flowers', 'Coins', etc. Each sheet loads live data via Power Query using the Torn API and calculates:
  - Total cost to buy all individual items
  - Estimated cost per point (based on in-game exchange set)
  - Comparison table and best value determination
- `powerquery/` — Power Query (M) scripts and import instructions so you can neatly paste queries into Excel using API and item ID. (works for any item)
- `screenshots/` — Dashboard and other preview screenshots.

## How to use (quick)
1. **Do not** share your Torn API key publicly. See *Config / API key* below.
2. Download or clone the repo.
3. Open `excel/torn_points_market_dashboard.xlsm`.
4. Put your API key in the designated space (see `README_EXCEL.md` for exact steps).
5. Click the adjacent Refresh button to refresh the queries (may take some time).
6. If Excel asks for privacy/authentication settings for the web source, approve as required.

## How to reuse the Power Query
How to reuse the Power Query for other items
1. Open Excel -> Data -> Get Data -> Launch Power Query Editor.
2. There is a list of queries on the left-hand side.
3. You can use the automated queries to pull out item info and market data for a given item using the item ID.
4. Enter in item ID. (More details in README_powerquery.md)
5. The query will result in a neat, detailed tabled from the JSON returned by api. The market data will only have price and quantity. Please always make sure you enter the correct item ID.
6. Close & Load to your workbook.
Detailed step-by-step in `powerquery/README_powerquery.md`.


## API key/config (security)
- **Do not** store API keys in the repo.
- Get your official key from TORN settings.
- To create your API key, go to settings -> API keys -> Create new key -> Name it and add 
- There are different access levels. Public-only keys will do fine for this repo. However, if you encounter any errors, you can get a high-level key.
- Official TORN API guide here - https://www.torn.com/api.html#
- If you accidentally commit a key, rotate it immediately.
- Misuse of APIs or stealing APIs may cause action from TORN.
---

## License
Check LICENSE

### Media & Data Usage
All screenshots included in this repository are free to use for documentation, educational, or demonstration purposes.

Sample JSON responses are from the public Torn API and are in the public domain.

---

## Contact / Author
Bhumit Joshi - reach me at bhumitjoshi200@gmail.com
This is a personal project. Any suggestions are welcome. Always keep your TORN keys and passwords safe. 
