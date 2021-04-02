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
	* SELECT 'Hello World!'; --*Single quotes in select statement will return literal string*
	* SELECT first_name FROM people
* Can specify multiple fields in SELECT statement by seperating each one with a comma
* Asterisk symbol will return all columns in table. Rarely used in report. Too much information
* Selecting data does not change anything in DB. Just lets us read data