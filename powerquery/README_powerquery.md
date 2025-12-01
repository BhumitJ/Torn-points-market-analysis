This is the Power Query to extract market data for any item from the Torn API. It is within the torn_excel_query.xlsm. Clone or download the repo to get started.

## Why not pull directly
The data pulled directly is in JSON and not in a tabular form. It is mostly under records and different layers. It can become messy and complicated to arrange neatly for viewing effectively.

## How to get any item data
1. Open torn_excel_query.xls → Data → Get Data → Launch Power Query Editor.
2. There is a list of queries on the left-hand side. The top three will be the KEY, ITEM INFO, and MARKET DATA.
3. The KEY is pulled in from the home sheet, so there's no need to do anything here. Put in your key in the designated space. 
4. You can use automated queries to pull item info and market data for a given item using its item ID. Please take a look below to know more about getting the item ID for any item in Torn. Please always make sure you enter the correct item ID.
5. ITEM INFO pulls in the data about the item, which includes the ID, name, type and average_price.
6. MARKET DATA pulls the real-time market listings of that item available in the Item Market in TORN CITY. It shows two columns, one for price and one for quantity. It won't display any other item info, so please be careful when entering the item ID.
7. After getting the info, you can click on close and load. If you have results for more than one query, you won't be able to load them in the current worksheet. One way is to load them as connection-only, then load them in the worksheet from the current queries list on the right-hand side. Right-click the query, then click Load for options. On closing the Power Query Editor directly with the close button it will ask in a dialouge where to save it. If you save it will load all queries in different sheets.
8. Load as tables in desired place. With each refresh the values will be updated. You can refresh from the button in home sheet, or from data ribbon, or from Power Query Editor.
9. The museum items sets in excel/torn_points_market_dashboard.xlsm have all been loaded in this way. 

## Obtaining item ID for different items
There are a couple of ways
1. You directly use your key in this URL - https://api.torn.com/torn/?selections=items&key=YOUR_KEY_HERE
   This will give you a list of all items in torn with their item ID. Search for you item using ctrl+F and find out the item ID.
2. If you would like a clean list, this URL contains the item info - https://beta.tornstats.com/items (the item ID is written with the name)

## Errors and Troubleshooting
If you encounter **bad gateway** just try again.
There is a limit for requests per API in torn (100 requests per minutue). If you referesh too many times and encounter such error, wait for a minute and try again.
