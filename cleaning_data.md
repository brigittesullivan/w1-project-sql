What issues will you address by cleaning the data?





Queries:
Below, provide the SQL queries you used to clean your data.

## Query 1:
```sql
SELECT *, round("unit_price"/1000000,2) as unit_price_clean
FROM analytics 
```
Note: I will use ```unit_price_clean``` to run any calculations.

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


Jan 20 @ 2045 - testing the git push went through. - B