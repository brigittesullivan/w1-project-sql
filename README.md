# Final-Project-Transforming-and-Analyzing-Data-with-SQL

## Project/Goals
1. Upload data into pgadmin
2. clean data to the point where is can be analysed with sufficient accuracy
3. perform the necessary analysis on the data
4. identify key results


## Process
### 1. Load data into PgAdmin(your step 1)
For each data file:
* open file in excel, save as UTF CSV
* quick review of data in excel to identify data types
* Create table in PGAdmin
  * sometimes used the PGAdmin Create table dialog, to create tables and columns
  * other times, where the # of columns was large (all_sessions), used excel formula to build create table alter table queries more efficiently
* lots of time spent figuring out best data type to use that would result in a successful upload

### 2. Cleaning 
1. **unit price conversion:** Added new column `unit_price_clean` to the `analytics` table

```sql 
-- updating unit price to dollars as a new column to show work, unit_price_clean will be used in all calculations
alter table analytics 
add column unit_price_clean numeric ; 
update analytics 
set unit_price_clean = ROUND(unit_price/1000000,2)
```
2. remove columns with 100% null values in clean table versions 
3. group null-ish values in the all_sessions Table

### 3. Analysis
1. completed the questions in the starting with data file
2. completed questions in the starting with questions file
 * found that many questions asked to use data that had 99% null values (see challenge #5 below) 

## Results
(fill in what you discovered this data could tell you and how you used the data to answer those questions)

 1. users spend the most time on average pruchasing kid's/infant apparel 
 2. 6 out of the top 10 revenue generating cities were located in the US
3. there are two different SKU formats, one possible explanation is that one SKU format is for active items and another for inactive (discontinued items)

## Challenges 
(discuss challenges you faced in the project)


1. Difficult understanding requirements of project
2. difficulty loading data into pgadmin
3. challenges with understanding the business context of the data
4. challenges with removing duplicate rows of data when there was no unique column to use. 
5. the wrong questions seemed to be asked of the data in the "starting with data" file.
   * I had to redo cleaning the tables since I removed columns that had 99% null values in the data cleaning step assuming no meaningful analysis could come from so little data. Had to recreate those table with the removed columns. 


## Future Goals
What would you do if you had more time?

### 1. Data Cleaning: 
#### 1.1. correct scientific notation in ID columns
Spent so much time with the mentor trouble shooting this. In the end, i decided to document it here as known item that needs to be reviewed. Due to complexity and time constraint, did not attempt to resolve further. 

**Approach: attempted this query but could not get correct outcome** 
          
```sql 
SELECT CONVERT(numeric(16,0) CAST(fullVisitorId AS FLOAT))
FROM all_sessions 
```

#### 1.2. Double quotations in queries
Figure out why when I create a table, I must use “double quotes” to reference any columns within that table. 

#### 1.3. provide more accurate data type lengths. 
I would have analysed the max min character lengths for for all varchar data types and assigned a max length of +120% of the largest character length, to be confirmed with a further review of the data. E.g., if the data showed great variability in length the character length may not be updated at all. 

### 2. Normalize Database - Assign primary keys and foreign keys for all tables. 
* Did not have time to conduct a full analysis to assign primary keys and normalize datable
* many columns were repeated accross numerous tables 
* Began with assigning the ProductSKU as a primary key in the Products table, but encountered issues when I attempted to assign SKU as a foreign key in other tables like sales_report and sales_by_sku. 
Issue was that there were product SKU in each of these tables that were not in the products table (which was assigned as the primary key. Naturally, postgres would return an error since there can't be foreign keys in one table that don't exist in the primary key table. 
* would need to do further analysis to determine if these rows could be dropped to allow the relationship or if there is another more appropriate relationship. 

### 3. Understand business context better 
* lack of business context made it difficult to confirm if the questions being asked of the data were even valid. 
* had to make assumptions about the data to perform the analysis that should have been confirmed before proceeding 