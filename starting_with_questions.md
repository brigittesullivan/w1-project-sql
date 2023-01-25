Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**

```sql
SELECT 
"country", 
"city", 
sum("transactionrevenue")
FROM all_sessions
GROUP BY
"city",
"country"
HAVING sum("transactionrevenue") IS NOT NULL
ORDER BY "country"
```
Answer:
"United States"	"Sunnyvale"	"$200,000,000.00"
"United States"	"not available in demo dataset"	"$2,190,950,000.00"

almost no data for transaction revenue only **4** rows have a not null value out of 15,134. 
I removed this column during my data cleaning, so the result is using the uncleaned raw data
QA: 
```sql
SELECT 
"country", 
"city", 
"transactionrevenue"
FROM
all_sessions
WHERE "transactionrevenue" IS NOT NULL
```




**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:
```sql 
SELECT 
"country",
"city",
ROUND(avg("productquantity"),2) as avg
FROM
all_sessions
GROUP BY 
"country",
"city"
HAVING sum("productquantity") IS NOT NULL
ORDER BY "country", "city"
```

QA CHECK:
```sql 
SELECT 
"country",
"city",
sum("productquantity"),ROUND(avg("productquantity"),2) as avg,count("productquantity")
FROM
all_sessions
GROUP BY 
"country",
"city"
HAVING sum("productquantity") IS NOT NULL
ORDER BY "country", "city"
```

Answer:
[Q2 answer image](/Users/brigitteasullivan/Desktop/w1-project-sql/Question_2_answer.png)




**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:



Answer:





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:



Answer:





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:







