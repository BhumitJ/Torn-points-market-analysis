A Power BI rebuild of the Excel dashboard in this repo. A quick look to see which item set is the cheapest route to museum points at current market prices?
The Excel version answers this with formulas across one sheet per item category. This version uses a dimensional model and four measures that work across every set at once, so adding a new set means adding rows to a CSV—no query or formula edits. ERRORS and TROUBLESHOOTING below.

Most sets cluster within a narrow band of roughly 30,700–32,300 per point. This will help to get a clear view of which sets yield the best value points and help estimate costs.

The CSV files in the folder contain information about the items and sets they belong to. Items are identified by their item ID. The file sets.csv is used to build the sets with their corresponding items, with quantities of items required to build the set. The file set_info.csv has the points info per set.
- sets is a bridge table. It resolves the many-to-many between items and sets into two one-to-many relationships.
- set_info exists as a separate table for one specific reason: points_awarded is a fact about a set, not about an item within a set. 

Items Missing Price counts items in a set with no price from the API. An item with no current listings returns blank, and blank silently contributes zero to Set Cost, making the set look cheaper than it is, with no error anywhere. The card makes that visible instead.

## Using the Power BI dashboard:
1. Download or clone the repo.
2. Open powerbi/torn-points.pbix. It opens with cached data, so you can see the report without a key.
3. To refresh with live prices, you will need to enter your api key and the file path for the extracted/cloned folder.
4. RepoPath — the folder you cloned this repo into,e.g. C:\projects\Torn-points-market-analysis
5. ApiKey — your own Torn API key. A public-access key is sufficient. Copy your API key from TORN settings -> API keys (see API key/config in README.md).
6. Home > Refresh. If prompted for credentials for api.torn.com, choose Anonymous — the key travels in the query string.

The committed PBIX has no API key in it. See the key-handling section in the root README.

Adding a set
Add rows to powerbi/sets.csv (one per item) and one row to powerbi/set_info.csv, then refresh.


## Errors and Troubleshooting
1. Setup and file paths
  "We couldn't find the file" / DataSource.Error on refresh
  The path built from RepoPath doesn't point to a real file. The queries construct their source as RepoPath & "\powerbi\sets.csv", so RepoPath must be the repo's   root folder (Not the powerbi folder). Check:
  - The folder actually contains powerbi\sets.csv and powerbi\set_info.csv.
  - If you downloaded a ZIP from GitHub, the extracted folder is often nested — Torn-points-market-analysis-main\Torn-points-market-analysis-main. Point at the     inner one, the one that directly contains powerbi.

2. A "Privacy levels" dialogue appears on refresh
Expected, and the normal path on a fresh copy of the file. Power BI is asking how to treat the two sources it's combining: the local CSV folder and https://api.torn.com/.
Tick "Ignore Privacy Levels checks for this file" and click Save. The two dropdowns can be left empty.
If Save stays greyed out, set both dropdowns to Public instead and save. Either works.
NOTE - Nothing sensitive is involved here. The warning exists because combining sources can send data from a private source into a public one. In this model, the local data is set definitions authored in the CSV files, and the outbound request contains item IDs, so there is nothing to leak.

3. Prompted for credentials for api.torn.com
Choose Anonymous. The API key travels in the query string, not in an authentication header, so any other option will fail.
If you picked the wrong one earlier, clear it: File > Options and settings > Data source settings > select the Torn entry > Clear Permissions, then refresh.

4. Null values, half data or bad gateways
There is a limit for requests per API in Torn (100 requests per minute). If you refresh too many times and encounter such an error, wait for a minute and try again. Also check that ApiKey has a real value if it fails on the first try.

## Known limitations
* Lowest-listing approximation. market[price] is the single cheapest listing per item. When a set needs multiple units, and the cheapest listing holds fewer than that, the true acquisition cost is higher than reported, because you clear the cheapest listing and move to the next. 
* Point-in-time. Every figure is a snapshot from the last refresh. Prices move. No history is stored, so the model cannot show trends or volatility.
