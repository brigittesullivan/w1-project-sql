# What Issues will you address by cleaning the data:

1. Improve ease of use by removing columns that add no value to the problems being solved (e.g., columns with 99%-100% null values)
2. Increase quata quality by grouping “null-ish” values. For example, in the all_sessions table, under city there were values assigned to (not set), and also “not available in demo data set”. Any records with either of these values were updated to NULL, for best efficiency in analysis / reporting. 
3. Correctly represent data in its proper unit of measure (e.g., “unit_price”, was cleaned to be represented in dollars, and cents
4. Load data into pg admin, set best data types upon loading (that will not return errors, but also maintain data quality. 
5. Maintain data integrity by creating “clean” table versions rather than overwriting raw data tables
Improve accuracy of analysis  by removing any duplicate rows in tables


# Queries:
Below, provide the SQL queries you used to clean your data.

## ISSUE 1: Remove columns with 100% NULL values
* Check the percentage of null values for all columns in all_sessions (see: query_1.md) 
* Applied the same steps to other tables
* When clean tables are created, they will not include the columns identified as having all nulls. 
* QA: used Excel to build long select statements consistently to cut down on typing and reduce typos

### Query for issue 1: 
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


## ISSUE 2: Address “Null-ish” values in the all_sessions_clean1 table
* Created all_sessions_clean1 table
* Multiple Null value types were present in the city and country columns
* The following steps were applied for each column sequentially. 
  * QA: checked how many rows of each null-ish exist to confirm # of total rows that need to be updated. When update query run, confirmed the # of values updated was 8,656
  * RESULT - city 
  * (not set) - 354
  * Not available in demo data set = 8302
  * TOTAL = 8,656
 
### Query for issue 2: 

**country column** 

QA: Confirmed # of values that should be updated
```sql 
SELECT country, count(*)
FROM all_sessions_clean1
group by country 
```
RESULT: 24 (not set) values to be updated to NULL

```sql
UPDATE all_sessions_clean1
SET country = NULL
WHERE "country" = '(not set)'
```

QA: Confirmed done correctly by running: 
```sql 
SELECT country, count(*)
FROM all_sessions_clean1
group by country 
```
RESULT: 24 NULL values, all countries showing as "not set" are now NULL

```sql 
SELECT distinct country, count(*) 
from all_sessions_clean1
GROUP BY country
order by country
```

**city column** 
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

```sql
UPDATE all_sessions_clean1
SET city = NULL
WHERE city = '(not set)' 
OR city = 'not available in demo dataset'
```

RESULT : SQL updated 8656 rows (8302 + 354)


## ISSUE 3: Correct Unit of Measure for “unit_price”
* 1. Create new "clean" table version with the cleaned unit_price
### Query for issue 3: 
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

3. Update new column values based on unit_price 
```sql
UPDATE analytics_clean1
SET unit_price_clean = round("unit_price"/1000000,2)

```

**QA STEP: run 
```sql
SELECT * FROM analytics_clean1
```
Confirmed the column was calculated correctly. 

Note: I will use ```unit_price_clean``` to run any calculations.

3. After perfomaing a QA check, I can confidently Drop original unit price from analytics_clean1. Since this is the "clean" version of the table, I decided It is best to only keep the "cleanest" versions of all data. Raw data still exists in the original analytics table for reference. 

```sql
ALTER TABLE analytics_clean1
DROP COLUMN unit_price;
```





## ISSUE 4: Load data into pg admin with data types
* Query_4.md
* Data types assigned before data is loaded, using data types as specific as possible without returning errors despite being a true 'int' fullvisitorid returned errors when a load was attempted when the column had data type set to int due to excel creating a scientific notation of the 19-digit #. 256 and 99 were used as standard character lengths. 

### Query for issue 4: 

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


## ISSUE 5: Creating clean data tables
* The data cleaning process only required new tables for `analytics` and `all_sessions`
* Addressing nullish values was done after a clean table was created. 

### Query for issue 5:
### Creating clean analytics table

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
### Creating clean all_sessions table

```sql
-- create new clean table with only columns where null % under 99 (removed 11 columns from original table)
CREATE TABLE all_sessions_clean1
AS 
SELECT 
"fullVisitorId"
,"channelGrouping"
,"time"
,"country"
,"city"
,"timeonsite"
,"pageviews"
,"sessionqualitydim"
,"date"
,"visitid"
,"type"
,"productprice"
,"productsku"
,"v2productname"
,"v2productcategory"
,"productvariant"
,"currencycode"
,"pagetitle"
,"pagepathlevel1"
,"ecommerceaction_type"
,"ecommerceaction_step"
FROM all_sessions
```


## ISSUE 6: Remove duplicate rows 
* No duplicate rows found in products, sales_by_sku, or sales_report, all_sessions tables
* Analytics Table
  * bounces column excluded from analysis of dupes, since it would return errors. Didn't have time to resolve why
  * QA: Used filtering of HAVING visitid = 1494861519 to make code more manageable to confirm the query was functioning the way I was expecting.

### Query for issue 6: 
### 6.1 sales_by_SKU table

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

### 6.2 products table
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

-- Result: returns no rows with count > 1

```

### 6.3 sales_report table

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

### 6.4 all_sessions
(same query format as previous queries, no duplicates found)


###  6.5 analytics

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

