What issues will you address by cleaning the data?





Queries:
Below, provide the SQL queries you used to clean your data.

# Query 1:
## all sessions table
0. check for columsn with 100% null values:
```sql
SELECT  
	 100*SUM(CASE WHEN "all_sessions"."fullVisitorId" IS NULL THEN 1 ELSE 0 END)/count(*) AS fullvisitorid_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."channelGrouping" IS NULL THEN 1 ELSE 0 END)/count(*) AS channelgrouping_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."time" IS NULL THEN 1 ELSE 0 END)/count(*) AS time_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."country" IS NULL THEN 1 ELSE 0 END)/count(*) AS country_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."city" IS NULL THEN 1 ELSE 0 END)/count(*) AS city_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."totaltransactionrevenue" IS NULL THEN 1 ELSE 0 END)/count(*) AS totaltransactionrevenue_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."transactions" IS NULL THEN 1 ELSE 0 END)/count(*) AS transactions_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."timeonsite" IS NULL THEN 1 ELSE 0 END)/count(*) AS timeonsite_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."pageviews" IS NULL THEN 1 ELSE 0 END)/count(*) AS pageviews_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."sessionqualitydim" IS NULL THEN 1 ELSE 0 END)/count(*) AS sessionqualitydim_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."date" IS NULL THEN 1 ELSE 0 END)/count(*) AS date_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."visitid" IS NULL THEN 1 ELSE 0 END)/count(*) AS visitid_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."type" IS NULL THEN 1 ELSE 0 END)/count(*) AS type_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."productrefundamount" IS NULL THEN 1 ELSE 0 END)/count(*) AS productrefundamount_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."productquantity" IS NULL THEN 1 ELSE 0 END)/count(*) AS productquantity_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."productprice" IS NULL THEN 1 ELSE 0 END)/count(*) AS productprice_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."productrevenue" IS NULL THEN 1 ELSE 0 END)/count(*) AS productrevenue_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."productsku" IS NULL THEN 1 ELSE 0 END)/count(*) AS productsku_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."v2productname" IS NULL THEN 1 ELSE 0 END)/count(*) AS v2productname_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."v2productcategory" IS NULL THEN 1 ELSE 0 END)/count(*) AS v2productcategory_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."productvariant" IS NULL THEN 1 ELSE 0 END)/count(*) AS productvariant_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."currencycode" IS NULL THEN 1 ELSE 0 END)/count(*) AS currencycode_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."itemquantity" IS NULL THEN 1 ELSE 0 END)/count(*) AS itemquantity_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."itemrevenue" IS NULL THEN 1 ELSE 0 END)/count(*) AS itemrevenue_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."transactionrevenue" IS NULL THEN 1 ELSE 0 END)/count(*) AS transactionrevenue_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."transactionid" IS NULL THEN 1 ELSE 0 END)/count(*) AS transactionid_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."pagetitle" IS NULL THEN 1 ELSE 0 END)/count(*) AS pagetitle_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."searchkeyword" IS NULL THEN 1 ELSE 0 END)/count(*) AS searchkeyword_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."pagepathlevel1" IS NULL THEN 1 ELSE 0 END)/count(*) AS pagepathlevel1_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."ecommerceaction_type" IS NULL THEN 1 ELSE 0 END)/count(*) AS ecommerceaction_type_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."ecommerceaction_step" IS NULL THEN 1 ELSE 0 END)/count(*) AS ecommerceaction_step_null_num_perc
, 100*SUM(CASE WHEN "all_sessions"."ecommerceaction_option" IS NULL THEN 1 ELSE 0 END)/count(*) AS ecommerceaction_option_null_num_perc
 FROM "all_sessions"
 ```

 RESULT: the following columns show or 100% null values, will not be included in new clean table: 
*  productrefundamount_null_num_perc = 100, 
* itemquantity_null_num_per = 100, 
* itemrevenue_null_num_perc = 100, 
* searchkeyword_null_num_perc = 100, 

After seeing 7 columns with 99% nulls, decided it was safe to also remove those columns. 
* totaltransactionrevenue_null_num_perc = 99 
* transactions_null_num_perc = 9 9
* productquantity_null_num_perc = 99
* productrevenue_null_num_perc = 99
* transactionrevenue_null_num_perc = 99
* transactionid_null_num_perc = 99
* ecommerceaction_option_null_num_perc = 99 

### 2. Create new "clean" table version

### 3. Update "null"ish values to one consistent null value. 
COUNTRY
```sql
UPDATE all_sessions_clean1
SET country = NULL
WHERE "country" = '(not set)'
```

Confirmed done correctly by running: 
```sql 
SELECT country, count(*)
FROM all_sessions_clean1
group by country 
```
And seeing 24 NULL values, all countries showing as "not set" are now NULL

CITY

```sql
UPDATE all_sessions_clean1
SET city = NULL
WHERE city = '(not set)' 
OR city = 'not available in demo dataset'
```
Result: update 8656 (8302 + 354)


e.g., - update "(not set)" and "not available in demo dataset" to null

QA: checkted how many rows of each exist to confirm # of total rows that need to be updated. 
RESULT - city 
(not set) - 354
Not available in demo data set = 8302

```sql 
SELECT distinct city, count(*) 
from all_sessions_clean1
GROUP BY city
order by city
```
RESULT - country 
(not set) - 24


```sql 
SELECT distinct country, count(*) 
from all_sessions_clean1
GROUP BY country
order by country
```



## analytics table

1. Create new "clean" table version
```sql
-- create new clean table with only columns where null % under 100 (removed userid)
CREATE TABLE analytics_clean1
AS 
SELECT 
 "visitnumber"
, "visitid"
, "visitstarttime"
, "date"
, "fullvisitorid"
, "channelgrouping"
, "socialengagementtype"
, "units_sold"
, "pageviews"
, "timeonsite"
, "bounces"
, "revenue"
, "unit_price"
FROM analytics
``` 

2. add a column to clean unit price in the analytics clean table
```sql
ALTER TABLE analytics_clean1 
ADD COLUMN unit_price_clean numeric;
```

3. Update column values based on unit_price 
```sql
UPDATE analytics_clean1
SET unit_price_clean = round("unit_price"/1000000,2)

```

**QA STEP: run SELECT * FROM analytics_clean1 to confirm the column was calculated correctly. 

```sql
SELECT *, round("unit_price"/1000000,2) as unit_price_clean
FROM analytics 
```
Note: I will use ```unit_price_clean``` to run any calculations.

3. After perfomaing a QA check, I can confidently Drop original unit price from analytics_clean1. Since this is the "clean" version of the table, I decided It is best to only keep the "cleanest" versions of all data. Raw data still exists in the original analytics table for reference. 



## Query 2: Loading data correctly into pgadmin

```sql 
CREATE TABLE analytics (
	visitNumber int ,
	visitId int ,
	visitStartTime int ,
	date int ,
	fullvisitorId varchar(99) ,
	userid int ,
	channelGrouping varchar(256) ,
	socialEngagementType varchar(256) ,
	units_sold int ,
	pageviews int ,
	timeonsite int ,
	bounces int ,
	revenue decimal(256) ,
	unit_price decimal(256)
);
```

```sql
ALTER TABLE analytics ADD "fullvisitorId" varchar(99);
```

Notes:
- despite being a true 'int' fullvisitorid returned errors when a load was attempted when the column had data type set to int due to excel creating a scientific notation of the 19-digit #. 256 and 99 were used as standard catch all character lengths. 
  - I had asked a mentor if the revenue should be under the "money" data type in pgadmin, they weren't familiar with that data type and suggested to stick with decimal. 
- a column constraint was added for the `userid` column for`not null`, however this returned an error when loading data. Logic for not null on this column is that if it is either a primary / foreign key, every row in the table should have a userid. It was meant as a preventative QA step. However was removed so that the load could be completed.
- 


Jan 20 @ 2045 - testing the git push went through. - B

## Query 3 - check for duplicates

### 3.1 sales by SKU table

```sql
-- Check for duplicates in the sales by sku table. 
SELECT
	"SKU"
	, "total_ordered"
	, count(*)
FROM sales_by_sku
GROUP BY "SKU", "total_ordered"
HAVING count(*)>2
-- result returns no rows. 

-- QA: -- Confirm no rows with count greater than 2, means there are no duplicates, and original query was accurate.

SELECT
	"SKU"
	, "total_ordered"
	, count(*)
FROM sales_by_sku
GROUP BY "SKU", "total_ordered";
```

### 3.2 products table
```sql 
-- Check for duplicates in the PRODUCTS table 
SELECT
	"SKU"
	, "name"
	, "orderedQuantity"
	, "stockLevel"
	, "restockingLeadTime"
	, "sentimentScore"
	, "sentimentMagnitude"
	, count(*)
FROM products
GROUP BY 	"SKU"
	, "name"
	, "orderedQuantity"
	, "stockLevel"
	, "restockingLeadTime"
	, "sentimentScore"
	, "sentimentMagnitude"
HAVING count(*)>2;
-- Result: returns no rows. 

-- QA: -- Confirm no rows with count greater than 2 by scanning, means there are no duplicates, and original query was accurate.

SELECT
	"SKU"
	, "name"
	, "orderedQuantity"
	, "stockLevel"
	, "restockingLeadTime"
	, "sentimentScore"
	, "sentimentMagnitude"
	, count(*)
FROM products
GROUP BY 	"SKU"
	, "name"
	, "orderedQuantity"
	, "stockLevel"
	, "restockingLeadTime"
	, "sentimentScore"
	, "sentimentMagnitude";

```
### 3.2 sales_report table

```sql
-- Check for duplicates in the SALES_REPORT table 
SELECT
	"productSKU"
	, "total_ordered"
	, "name"
	, "stockLevel"
	, "restockingLeadTime"
	, "sentimentScore"
	, "sentimentMagnitude"
	, "ratio"
	, count(*)
FROM sales_report
GROUP BY 
	"productSKU"
	, "total_ordered"
	, "name"
	, "stockLevel"
	, "restockingLeadTime"
	, "sentimentScore"
	, "sentimentMagnitude"
	, "ratio"
HAVING count(*)>2;
-- -- Result: returns no rows. 

-- QA: -- Confirm no rows with count greater than 2 by scanning, means there are no duplicates, and original query was accurate.

SELECT
	"productSKU"
	, "total_ordered"
	, "name"
	, "stockLevel"
	, "restockingLeadTime"
	, "sentimentScore"
	, "sentimentMagnitude"
	, "ratio"
	, count(*)
FROM sales_report
GROUP BY 	
	"productSKU"
	, "total_ordered"
	, "name"
	, "stockLevel"
	, "restockingLeadTime"
	, "sentimentScore"
	, "sentimentMagnitude"
	, "ratio";
```


### 3.2 sales_report table
-- no duplicates found, used same queries as 3.1 and 3.2

### 3.3  analytics

* Found duplicates in this table. No columns contained unique ID's. 
* created a new clean table version to continue with data cleaning - "anatlytics_clean1"
  * removed userid column since entire column had null values
* in doing QA I would regularly filter by one visit id, to confirm that the queries were functioning as I expected them to. Since the data set is so large. Taking on visitid made it clearer to spot errors.  

### 3.4 all_sessions 

Cleaning Step 1:
* create new clean table version
* set proper null to city and country


# Cleaning step 2: Find % NULL - products table
```sql
-- find Null % fro products table, before creating new clean table
SELECT
 100*SUM(CASE WHEN "SKU" IS NULL THEN 1 ELSE 0 END)/count(*) AS sku_null_num_perc
, 100*SUM(CASE WHEN "name" IS NULL THEN 1 ELSE 0 END)/count(*) AS name_null_num_perc
, 100*SUM(CASE WHEN "orderedQuantity" IS NULL THEN 1 ELSE 0 END)/count(*) AS orderedquantity_null_num_perc
, 100*SUM(CASE WHEN "stockLevel" IS NULL THEN 1 ELSE 0 END)/count(*) AS stocklevel_null_num_perc
, 100*SUM(CASE WHEN "restockingLeadTime" IS NULL THEN 1 ELSE 0 END)/count(*) AS restockingleadtime_null_num_perc
, 100*SUM(CASE WHEN "sentimentScore" IS NULL THEN 1 ELSE 0 END)/count(*) AS sentimentscore_null_num_perc
, 100*SUM(CASE WHEN "sentimentMagnitude" IS NULL THEN 1 ELSE 0 END)/count(*) AS sentimentmagnitude_null_num_perc
FROM products
```
**RESULT - all columns have 0% null values.**

# Cleaning step 2: Find % NULL - sales_report table

```sql
-- check null % for sales report table 
SELECT
100*SUM(CASE WHEN "productSKU" IS NULL THEN 1 ELSE 0 END)/count(*) AS productSKU_null_num_perc
, 100*SUM(CASE WHEN "total_ordered" IS NULL THEN 1 ELSE 0 END)/count(*) AS total_ordered_null_num_perc
, 100*SUM(CASE WHEN "name" IS NULL THEN 1 ELSE 0 END)/count(*) AS name_null_num_perc
, 100*SUM(CASE WHEN "stockLevel" IS NULL THEN 1 ELSE 0 END)/count(*) AS stockLevel_null_num_perc
, 100*SUM(CASE WHEN "restockingLeadTime" IS NULL THEN 1 ELSE 0 END)/count(*) AS restockingLeadTime_null_num_perc
, 100*SUM(CASE WHEN "sentimentScore" IS NULL THEN 1 ELSE 0 END)/count(*) AS sentimentScore_null_num_perc
, 100*SUM(CASE WHEN "sentimentMagnitude" IS NULL THEN 1 ELSE 0 END)/count(*) AS sentimentMagnitude_null_num_perc
, 100*SUM(CASE WHEN "ratio" IS NULL THEN 1 ELSE 0 END)/count(*) AS ratio_null_num_perc
FROM 
sales_report
```
**RESULT - all columns have 0% null values, except ratio_null_num_perc with 17% NULL, still low enough to be considered in dtset.**

# Cleaning step 2: Find % NULL - sales_by_sku

```sql
-- check null % for sales_by_sku table 
SELECT
100*SUM(CASE WHEN "SKU" IS NULL THEN 1 ELSE 0 END)/count(*) AS productSKU_null_num_perc
, 100*SUM(CASE WHEN "total_ordered" IS NULL THEN 1 ELSE 0 END)/count(*) AS total_ordered_null_num_perc
FROM 
sales_by_sku
```
**RESULT: all 2 columns have 0% nulls**

# Cleaning step 3: Dealing with duplicates in the analytics table

Create new "unique key" column to filter out duplicates correctly. Will be based off visitid and unit-price-clean. 


```sql
CREATE TABLE analytics_clean3 AS (
SELECT 
	 "visitnumber"
	, "visitid"
	, "visitstarttime"
	, "date"
	, "fullvisitorid"
	, "channelgrouping"
	, "socialengagementtype"
	, "units_sold"
	, "pageviews"
	, "timeonsite"
	--, "bounces"
	, "revenue"
	, "unit_price_clean"
FROM analytics_clean1
GROUP BY 
	 "visitnumber"
	, "visitid"
	, "visitstarttime"
	, "date"
	, "fullvisitorid"
	, "channelgrouping"
	, "socialengagementtype"
	, "units_sold"
	, "pageviews"
	, "timeonsite"
	--, "bounces"
	, "revenue"
	, "unit_price_clean")
	``` 

QA - ran another query to confirm all rows had a count of 1
```sql
SELECT 
	 "visitnumber"
	, "visitid"
	, "visitstarttime"
	, "date"
	, "fullvisitorid"
	, "channelgrouping"
	, "socialengagementtype"
	, "units_sold"
	, "pageviews"
	, "timeonsite"
	--, "bounces"
	, "revenue"
	, "unit_price_clean"
	, count(*)
FROM analytics_clean3
GROUP BY 
	 "visitnumber"
	, "visitid"
	, "visitstarttime"
	, "date"
	, "fullvisitorid"
	, "channelgrouping"
	, "socialengagementtype"
	, "units_sold"
	, "pageviews"
	, "timeonsite"
	--, "bounces"
	, "revenue"
	, "unit_price_clean"
HAVING visitid = 1494861519
ORDER BY unit_price_clean, count(*)
```

NOTE: bounces column excluded from analysis of dupes, since it would return errors. DIdn't have time to resolve why. 

# Cleaning step 3: Dealing with duplicates in the all_sessions table

all_sessions table has no duplicates (???)

Confirmed by running. 
```sql
SELECT 
	"fullVisitorId", 
	"channelGrouping", 
	"time", 
	"country", 
	"city", 
	"timeonsite", 
	"pageviews", 
	"sessionqualitydim", 
	"date", 
	"visitid", 
 	"type", 
	"productprice", 
	"productsku", 
	"v2productname", 
	"v2productcategory", 
	"productvariant", 
	"currencycode", 
	"pagetitle", 
	"pagepathlevel1", 
	"ecommerceaction_type", 
	"ecommerceaction_step",
	COUNT(*)
FROM all_sessions_clean1
GROUP BY 
	"fullVisitorId", 
	"channelGrouping", 
	"time", 
	"country", 
	"city", 
	"timeonsite", 
	"pageviews", 
	"sessionqualitydim", 
	"date", 
	"visitid", 
 	"type",
	"productprice", 
	"productsku",
	"v2productname", 
	"v2productcategory", 
	"productvariant", 
	"currencycode", 
	"pagetitle", 
	"pagepathlevel1", 
	"ecommerceaction_type", 
	"ecommerceaction_step"
HAVING count(*) > 1
ORDER BY "visitid" DESC
```

Also ran another query with, which did return duplicates, however has new columns were added to the search, the duplicates gradually went away. 
```sql 
"fullVisitorId", 
	"channelGrouping", 
	"time", 
	"country", 
	"city", 
	"timeonsite", 
	"pageviews", 
	"sessionqualitydim", 
	"date", 
	"visitid", 
```