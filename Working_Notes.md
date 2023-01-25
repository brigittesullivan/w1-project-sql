### 1 - Product Codes
When I run this code:
```sql
SELECT * from products
WHERE "SKU" NOT LIKE '%GG%'
```

I see that all `OrderedQuantity` and `Stocklevel` values are zero. Suggests that one format of product SKU's is for discontinued items. Add new column to label discontinued items? 

Also, when I run this: 
```sql
SELECT * from all_sessions
WHERE productsku NOT LIKE '%GG%'
```
I find that all prices are set to $0.00. 

### 2 - CLEANING  / QA STEP 
Ran SELECT DIsctinct Country from all_sessions 

CHECKED FOR ANY TYPOS IN spelling of country names 
FOund these countries was not ported properly bc of accents:
* REUNION
* cote divoire 


CHECKED FOR ANY TYPOS IN spelling of city names 
FOund these cities was not ported properly bc of accents:
* Am√£
* San Francisco = South San Francisco ? ? 


CHECKED CITY and Country disctinct: 
``` sql
SELECT distinct city, country FROM "all_sessions"
ORDER BY country
```

Found a Toronto, United states

## IN ALL_SESSIONS 13 COLUMNS WITH SUM OF NULLS > 0 ARE... 
-- SELECT 
-- 	transactionRevenue_null_num

-- 	, transactionId_null_num

-- 	, timeOnSite_null_num

-- 	, sessionQualityDim_null_num

-- 	, productRefundAmount_null_num

-- 	, productQuantity_null_num

-- 	, productRevenue_null_num

-- 	, currencyCode_null_num

-- 	, itemQuantity_null_num

-- 	, itemRevenue_null_num

-- 	, transactionRevenue_null_num

-- 	, searchKeyword_null_num

-- 	, eCommerceAction_option_null_num 

-- FROM 

testing git status - jan 25
