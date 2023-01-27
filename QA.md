# What are your risk areas? Identify and describe them.

## Risk 1: Lack of business context understanding of data 
Much of the analysis and cleaning was done without any business context for the data. Some assumptions were made that may prove to be false. 

## Risk 2: Low quality questions were asked of the data. 

E.g., in Question 1, of starting with questions:  
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**

The question clearly asks for transaction revenue by city and country. There is a column in the data set named "transactionrevenue". However this column only has 4 records out of 15,314.

The answer to Question 1 should be taken with high skepticism since it's based on so few entries for a relatively large dataset. 

It's likely that the question asked is incorrect. The answer provided in other files is the correct answer to the wrong question. 

## Risk 3: Loss of data precision during loading 
Full visitor Id Data column is imported into pgadmin using the scientific notation when this is done, the unique 19-digit code is transformed to a format where the last 10 digits are lost. 

E.g., 
* Original FullVisitor ID: 20947562074452200
* FullVistor ID Imported Format: 2.09476 E+16
        * when converted back to digit format the code becomes: 20947600000000000
* Looses the uniqueness of this key

# QA Process:
Describe your QA process and include the SQL queries used to execute it.

1.  Every answer was validated to confirm accuracy, by taking counts. Specific QA steps applied are included with their respective queries. (Decided to not include here due to time constaints and complexity of splitting out the information, and loss of value in having them split)


2. When developping complex queries for tables, I used excel concatenation function to automate the writing of the query correctly. This was to minimize the likelihood of imperceptible typos in the code. This was particiularly helpful when doing data cleaning. And determininng the %of null values found in each column of each table.
3. Data cleaning checks / QA:

CHECKED FOR ANY TYPOS IN spelling of country names 
Found these countries was not ported properly because of accents:
* REUNION
* cote divoire 


CHECKED FOR ANY TYPOS IN spelling of city names 
FOund these cities was not ported properly bc of accents:
* Am√£
* found two similar cities: San Francisco and South San Francisco. 


CHECKED CITY and Country disctinct: 
``` sql
SELECT distinct city, country FROM "all_sessions"
ORDER BY country
```
Found a Toronto, United states
