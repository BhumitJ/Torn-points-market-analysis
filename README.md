# Torn-points-market-analysis
Several item sets can be exchanged for museum points, at market prices that move constantly. This tracks all of the point sets and answers one question: which set is the cheapest route to points right now?

Live pricing via the Torn API, in two forms — an Excel dashboard and a Power BI report — plus a reusable query that returns market data for any item in Torn.

NOTE - This is a data analysis/dashboard project that shows the cost of in-game item sets (e.g. plushies/flowers → 10 points) using the Torn API, Excel Power Query, and Power BI. Useful for traders and as a worked example of API integration, nested-JSON transformation, and cost modelling over volatile inputs.


## What this project contains
- 'powerbi/Torn_points.pbix' (Power BI file) - Dashboard to get quick live data and cost analysis for each set, with visual cost per point data in real time. 
- `excel/torn_points_market_dashboard.xlsm` — Dashboard with sheets: 'Plushies', 'Flowers', 'Coins', etc. Each sheet loads live data via Power Query using the Torn API.
   These get you:
 * Total cost to buy all individual items
 * Estimated cost per point (based on in-game exchange set)
 * Comparison table and best value determination
 * In-depth market listings for each item in excel sheets
- `powerquery/` — Power Query (M) scripts and import instructions so you can neatly paste queries into Excel using the API and item ID. (works for any item)
- `screenshots/` — Dashboard and other preview screenshots.

## How to use (quick)
### A. Excel
1. **Do not** share your Torn API key publicly. See *Config / API key* below.
2. Download or unzip or clone the repo.
3. Open `excel/torn_points_market_dashboard.xlsm`.
4. Put your API key in the designated space (see `README_EXCEL.md` for exact steps).
5. Click the adjacent Refresh button to refresh the queries (may take some time).
6. If Excel asks for privacy/authentication settings for the web source, approve as required.

### B. Power BI
1. Download, unzip or clone the repo.
2. Open `powerbi/torn-points.pbix`. It opens with saved data, so you can see the report straight away — the steps below are only for refreshing with live prices.
3. **Home > Transform data > Edit Parameters.**
   - `RepoPath` — the folder you unzipped or cloned into.
     e.g. `C:\projects\Torn-points-market-analysis\`
   - `ApiKey` — your Torn API key (public access is enough)
4. **Home > Refresh.** If asked for credentials for `api.torn.com`, choose **Anonymous**.
5. If you get a `Formula.Firewall` error, go to File > Options and settings > Options > Current File > Privacy and select "Ignore the Privacy Levels", then refresh again.

## How to reuse the Power Query
Using Power Query for other items
1. Open Excel -> Data -> Get Data -> Launch Power Query Editor.
2. There is a list of queries on the left-hand side.
3. You can use the automated queries to pull out item info and market data for a given item using the item ID.
4. Enter the item ID. (More details in README_powerquery.md)
5. The query will result in a neat, detailed table from the JSON returned by api. The market data will only have price and quantity. Please always make sure you enter the correct item ID.
6. Close & Load to your workbook.
Detailed step-by-step in `powerquery/README_powerquery.md`.


## API key/config (security)
- **Do not** store API keys in the repo.
- Get your official key from TORN settings.
- To create your API key, go to settings -> API keys -> Create new key -> Name it and add it. 
- There are different access levels. Public-only keys will do fine for this repo. However, if you encounter any errors, you can get a high-level key.
- Official TORN API guide here: https://www.torn.com/api.html#
- If you accidentally commit a key, rotate it immediately.
- Misuse of APIs or stealing APIs may result in action from TORN.
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
