The Excel workbook contains separate sheets for each item set, with current market listings and info for each set.

## Using the Excel dashboard
What you will need:
A TORN API key, Excel

1. Download or clone the repo.
2. Open `excel/torn_points_market_dashboard.xlsx`.
3. Copy your API from TORN setting -> API keys (see API key/config in README.md).
4. Paste your API key in the designated space. (Home sheet)
5. Click the adjacent Refresh button to refresh the queries (may take some time). Please do NOT enter incorrect keys, other text, or anything other than your correct API, and click refresh. This may cause a long series of errors in Excel. To close them, try clicking cancel in the bottom left; otherwise, click through them all. You can click refresh after you enter the correct keys for your account.
6. If Excel asks for privacy/authentication settings for the web source, approve as required.
7. After clicking refresh, the workbook fetches all real-time updates from TORN. All the tables will be updated.
8. On your main worksheet (home), you will get a summary of all museum items and sets along with their market and current values. The dashboard will also show the lower value you can get per point, as well as the item set.
9. Each item set has its own sheet with a market listing of different items and set values, along with per-point values.
