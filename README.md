# Final-Project-Transforming-and-Analyzing-Data-with-SQL

## Project/Goals
(fill in your description and goals here)
Jan 20-1: testing upload to git from local machine

## Process
### (your step 1)
### (your step 2)

## Results
(fill in what you discovered this data could tell you and how you used the data to answer those questions)

## Challenges 
(discuss challenges you faced in the project)

## Future Goals
(what would you do if you had more time?)

### 1. correct scientific notation in ID columns
Spent so much time with the mentor trouble shooting this. In the end, i decided to document it here as known item that needs to be reviewed. Due to complexity and time constraint, did not attempt to resolve further. 

**Approach 1:** 
          
```sql 
SELECT CONVERT(numeric(16,0) CAST(fullVisitorId AS FLOAT))
FROM all_sessions 
```
**Approach 2:**



resources from mentor:
1. https://stackoverflow.com/questions/6750021/casting-scientific-notation-from-varchar-numeric-in-a-view 

2. https://stackoverflow.com/questions/43736180/how-do-i-convert-a-varchar-containing-a-number-in-scientific-notation-to-a-numer 

### 2. Double quotations in queries
Figure out why when I create a table, I must use “double quotes” to reference any columns within that table. 

### 2. provide more accurate data type lengths. 
I would have analysed the max min character lengths for for all varchar data types and assigned a max length of +120% of the largest character length, to be confirmed with a further review of the data. E.g., if the data showed great variability in length the character length may not be updated at all. 

### 2. Assign primary keys and foreign keys for all tables. 

Jan 20 20:45 - TESTING THE GIT PUSH WENT THROUGH