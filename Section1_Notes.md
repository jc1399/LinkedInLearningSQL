
## Ask for Data from a Database

### SELECT 
* Tells DB that we want to collect spectific information to return to us
* Example
	* SELECT 'Hello World!';  --*Single quotes in select statement will return literal string*
	* SELECT first_name FROM people
* Can specify multiple fields in SELECT statement by seperating each one with a comma
* Asterisk symbol will return all columns in table. Rarely used in report. Too much information
* Selecting data does not change anything in DB. Just lets us read data

### WHERE
* Let's user add selection sriteria to a statement
* Example 
	* SELECT * FROM people WHERE state_code='CA';  -- *CA is an expression. This is case sensitive as defined when table was constructed*
* WHERE clause seach based on column that has some specific entry
* Ensure WHERE remains after SELECT and FROM

### Adding more criteria to a statement
* Find names of people in california and asked for a shirt
```
SELECT first_name, last_name
FROM people
WHERE state_code='CA' AND shirt_or_hat='shirt'
```

Find names of people in california and asked for a shirt and did NOT sign up for Angry Ants Team
```
SELECT first_name, last_name
FROM people
WHERE state_code='CA' AND shirt_or_hat='shirt' AND team!='Angry Ants';
```
* keywords IS and IS NOT
* not equals operator: <>

Find names of people in california or colorado and asked for a shirt
```
SELECT first_name, last_name, shirt_or_hat, state_code
FROM people
WHERE (state_code='CA' OR state_code='CO') AND shirt_or_hat='shirt';
```
* Parenthesis are useful to shape meaning of data and group data relevant to what information you need

### Broadening Limiting Responses
* LIKE '%...'
	* Returns results that match part of a strins
	* The % represents the part of the string we dont care about

Find all people from states that begin with C
```
SELECT *
FROM people
WHERE state_code LIKE 'C%';
```
Find all first names ending with a
```
SELECT *
FROM people
WHERE first_name LIKE '%A';
```
Note that even though the character after % is capital, it will return names that have A lower case

Find all first names containing ON
```
SELECT *
FROM people
WHERE first_name LIKE '%ON%';
```

Find all LLC companies
```
SELECT *
FROM people
WHERE company LIKE '%LLC';
```

* LIMIT n
	* Tells DB the limit of rows we want to return 
* LIMIT n OFFSET m
	* Tells how many rows to skip before counting off limit value
```
SELECT *
FROM people
WHERE company LIKE '%LLC'
LIMIT 5 OFFSET 5;
```

### ORDER BY
* Sorts the results of a query using respective fields

Order names by first name
```
SELECT first_name, last_name
FROM people
ORDER BY first_name;
```
* Defaults to ASC order but can specify DESC order

Order by state then last name
```
SELECT state_code, last_name, first_name
FROM people
ORDER BY state_code, last_name;
```
* orders by the state and in each state the last names are sorted

### Find info about the data
Get first name of all people
```
SELECT first_name, LENGTH(first_name)
FROM people;
```
* returns the length of the string in the cell 

* DISTINCT 
Pull unique name values with in ASC order
```
SELECT DISTINCT(first_name)
FROM people
ORDER BY first_name;
```

* COUNT
Find number of companies that are in CA
```
SELECT COUNT(company)
FROM people
WHERE state_code='CA';
```
