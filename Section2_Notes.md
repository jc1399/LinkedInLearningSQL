## Ask for Data from Two or More Tables

### Ask for Data from Two or More Tables
* Joins/Inner Joins
	* Asks for records across two tables that are associated with each other based on common piece of information (i.e. both tables have columns with same data)
Uses people and states tables to connect names based on their state code
```
SELECT people.first_name, people.state_code,states.division
FROM people
JOIN states ON people.state_code=states.state_abbrev
WHERE people.first_name LIKE 'J%' AND states.region='South';
```
* Can use the dot notation shown above to grab data from multiple tables w/o using JOIN keyword. Known as *Implicit Join*
* Aliases can be used to make table names shorter
	* ex: FROM people ppl, states sts

### Understand JOIN types
#### CROSS JOIN
* Every entry of one table gets paired with every entry of the other table

People Table:
name 		| state
------------|-------------
Marcus		| CA
Jennifer	| VA
Devin		| MA

States Table:
abbr 		 | full 
------------ | -------------
CA 			 | California
DE 			 | Delaware
VA 			 | Virgina

Query: 
```
SELECT * FROM people JOIN states;
```
Result:
name 		| state 	  	| abbr 	       | full 
------------| ------------- | ------------ | -------------
Marcus		| CA 			| CA 			 | California
Marcus		| CA 			| DE 			 | Delaware
Marcus		| CA 			| VA 			 | Virgina
Jennifer	| VA			| CA 			 | California
Jennifer	| VA			| DE 			 | Delaware
Jennifer	| VA 			| VA 			 | Virgina
Devin		| MA			| CA 			 | California
Devin		| MA			| DE 			 | Delaware
Devin		| MA			| VA 			 | Virgina

#### INNER JOIN
* Associate data from one table to other based on a key/given criteria
	* ex: equate data in one table based on state_code
* May not be 1-1 relationship

People Table:
name 		| state
------------|-------------
Marcus		| CA
Jennifer	| VA
Devin		| MA
Britt		| CA

States Table:
abbr 		 | full 
------------ | -------------
CA 			 | California
DE 			 | Delaware
VA 			 | Virgina

Query: 
```
SELECT * FROM people JOIN states ON people.states = states.abbr;
```
Result:
name 		| state 	  	| abbr 	       | full 
------------| ------------- | ------------ | -------------
Marcus		| CA 			| CA 			 | California
Jennifer	| VA 			| VA 			 | Virgina
Britt		| CA 			| CA 			 | California

#### LEFT (OUTER) JOIN
* See all data from one table and get matches from the other
* Where there is a match in the right table, the information shows, otherwise left table values show but will have null for right values

Use Tables from INNER JOIN example...
Query: 
```
SELECT * FROM people LEFT JOIN states ON people.states = states.abbr;
```
Result:
name 		| state 	  	| abbr 	       | full 
------------| ------------- | ------------ | -------------
Marcus		| CA 			| CA 			 | California
Jennifer	| VA 			| VA 			 | Virgina
Devin		| MA 			| *NULL* 		 | *NULL*
Britt		| CA 			| CA 			 | California

#### RIGHT JOIN
* See left join but switch 

Use Tables from INNER JOIN example...
Query: 
```
SELECT * FROM people RIGHT JOIN states ON people.states = states.abbr;
```
Result:
name 		| state 	  	| abbr 	       | full 
------------| ------------- | ------------ | -------------
Marcus		| CA 			| CA 			 | California
Jennifer	| VA 			| VA 			 | Virgina
Britt		| CA 			| CA 			 | California
*NULL* 		 | *NULL*		| DE 			 | Delaware

#### FULL OUTER JOIN 

Use Tables from INNER JOIN example...
Query: 
```
SELECT * FROM people FULL OUTER JOIN states ON people.states = states.abbr;
```
Result:
name 		| state 	  	| abbr 	       | full 
------------| ------------- | ------------ | -------------
Marcus		| CA 			| CA 			 | California
Jennifer	| VA 			| VA 			 | Virgina
Devin		| MA 			| *NULL* 		 | *NULL* 
Britt		| CA 			| CA 			 | California
*NULL* 		 | *NULL*		| DE 			 | Delaware

* *Note not all joins are supported in every SQL software*

Allows user to see what states are not represented in the people quiz table.
There is an abbreveation for the state but those abbr. are not represented in the people table.
```
SELECT DISTINCT(p.state_code), st.state_abbrev
FROM states as st
LEFT JOIN people as p on p.state_code=st.state_abbrev
ORDER BY p.state_code;
```

### Grouping Results
#### GROUP BY

Counts how many quiz participants are from each state
```
SELECT state_code, COUNT(state_code)
FROM people
GROUP BY state_code;
```

How many people from each state got each score
```
SELECT state_code, quiz_points, count(quiz_points)
FROM people
GROUP BY state_code, quiz_points;
```

### CHALLENGE TASK
1) Create summary of how many hats need to be shipped to each state

```
SELECT state_name, count(shirt_or_hat)
FROM people
JOIN states ON  people.state_code = states.state_abbrev
WHERE shirt_or_hat='hat'
GROUP BY state_code
```

2) Create summary showing how many members of each team are in each geographic division

```
SELECT states.division, people.team, count(people.team)
FROM people 
JOIN states ON people.state_code = states.state_abbrev
GROUP BY states.division, people.team
```