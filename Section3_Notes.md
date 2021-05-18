## Data Types, Math, and Helpful Features

### Data Types in SQL
* Data type: The kind of data stored in a field
	* Can be numeric, binary, etc
* Certain operations are excluded for some data types
Types:
* Binary Fields: stores short binary sequences (ex: 10010) or longer sequences (files)
* Date/Time Types: Store a value that shoul be treated as a date/time data (ex: 2021-04-05 ; 2021-04-05 17:35:00)
* Number Types: Stores number values as integers of various lengths, floating point numbers, etc
* Text Types: Store values intended to be used as text strings. Is a fixed or variable numbers of characters (varchar = variable character length or char = fixed length of characters)
* Boolean: Stores true or false value
* NULL: represents a field having no value (not the same as false, no or zero)

### Math in SQL
* Most basic: use SELECT statement (ex: SELECT 4+2)
* Supports arithmetic operators: +,-,asterisk,/,and %
* Assumes interger operations unless otherwise specified
* Supports comparison operators: >,<,>=,<=,=,!=,or <>
* Some SQL DBMS supports ADD() and SUM()
Example:
```
SELECT 4+2
```
Following returns boolean true
```
SELECT 5>2
```
```
SELECT MAX(quiz_points), MIN(quiz_points), SUM(quiz_points)
FROM people
```
Breaks down how many ppl are in each team
```
SELECT team, COUNT(*), SUM(quiz_points), SUM(quiz_points)/COUNT(*) 
FROM people
GROUP BY team
```

### Compund SELECT
List all people in data who achieved highest score
```
SELECT first_name,last_name, quiz_points
FROM people
WHERE quiz_points=(SELECT MAX(quiz_points) FROM people);
```

```
SELECT *
FROM people
WHERE state_code(
	SELECT state_abbrev FROM state WHERE state_name='Minnesota'
	);
```

### Transforming Data 
We are able to transform data in the database to something we need in the database.(chage case of string, converting value to different type, trimming a value)

To present data in a perticular way... 

Change data to upper or lower case
```
SELECT LOWER(first_name), UPPER(last_name)
FROM people;
```

Return substring of the last name starting from 
```
SELECT first_name, SUBSTR(last_name, 1, 5)
FROM
```

Cast data in the database
```
SELECT quiz_points
FROM people
ORDER BY CAST quiz_points as CHAR)
```

### Aliasing with AS
To change the return name of a field to make it clear what information is in the column
Especially helpful when exporting to spreadsheet or providing output to an application
Good to use names without spaces

### Aliasing with AS


