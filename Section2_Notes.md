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