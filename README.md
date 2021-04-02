# LinkedIn Learning - Learning SQL Programming

## Areas of Learning/Methods Practiced
* Using SQLite with DB browser interface to write querys and practice SQL Language
* Practice with using version control software to upload notes to githuub to use for later reference
* Utilizing Markdown Language to effectively keep track of personal course notes

## Introduction

### Database
* A collection of information organized by columns (fields) and rows (records)
* DB allow to make schemas (realtionships/rules) of the tables

### SQL
* Structured Query Language
* Let's a user form questions a DB can respond to
* Language statements is made up of *Clauses* or keywords in a statement (SELECT, FROM, ORDER BY)
* Statements are...
	* Whitespace independent
	* Composed of clauses made of elements, field names, table names, predicates with expresions
	* Sould end in a semicolon (good practice)
* SQL can be considered for uses as a ...
	* Data Manipulation Language
		* Edit data in the database
		* Create Read Update Delete (CRUD)
	* Data Definition Language
		* Edit the structure (schema) of the database
		* Add, change, or remove fields or tables

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