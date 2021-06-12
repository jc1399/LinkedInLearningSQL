## Add or Modify Data

### Add Data to a Table
* INSERT: The keyword that adds a record to a table
	* Must what table to add data to, what fields to add info in, and values toput into those fields
```
INSERT INTO people (first_name) VALUES ('Bob');
-- To check change in the table run following command and look ad end of data
SELECT * FROM people
```
There will be no information in that row since we did not specify any, just created that row

```
INSERT INTO people
(first_name, last_name, state_code, city, shirt_or_hat)
VALUES
('Mary', 'Hamilton', 'OR', 'Portland', 'hat');
```
Above code will add a row with all the information stated. Information is input in the order stated to respective columns.

```
INSERT INTO people
(first_name, last_name)
VALUES
('George', 'Costanza')
('Jerry', 'Seinfeld')
('Elaine', /*NULL*/);
```
When fields are provided to recieve data, data must be given. Above code will return an error since the third name given does not provide a last_name. Use NULL to specify that data will not be input into that cell as shown in the comment. An empty value may be specified to another value like 0, depending on table implementation.

### Modify Data in a Table
* UPDATE: Keyword used to change data already stored in the fields in a record
	* Must specify what tables we are using, which fields to modify with what values, and optionally a where clause to specify how to find records we want to update

```
--Check if there are other people with first name Carlos
SELECT last_name FROM people WHERE first_name='Carlos' ;
-- We have multiple Carlos'. Since we know his name is mispelled, we can specify the last name with the mispelling
UPDATE people 
SET last_name='Morrison' 
WHERE last_name='Morrrison';
```
Can also do this update by matching other fields that relate to this participant.
```
SELECT last_name 
SET last_name='Morrison'
WHERE first_name='Carlos' AND city='Houston'; 
```
We can alternatively use the unique id number ties to the person we want to change information for
```
SELECT people
SET last_name='Morrison'
WHERE id_number=175
```
It is possible to change multiple rows of data in one command.
```
UPDATE people SET company='Megacorp INC' WHERE company='Fisher LLC';
```

### Removing Data from a Table
DELETE - To remove data from table
Should specify scope of deletion

Following deletes a row where 1001 is the id number
```
DELETE FROM people WHERE id_number=1001;
```
Can also remove multiple records at a time with a WHERE statememnt that matches more than one record. Can get messy!

```
DELETE FROM people WHERE quiz_points IS NULL;
```
Above code will delete any rows where the column 'quiz_points' has a value equal to NULL.

## Challenge Task: Practice Working with Data
Process requests to change data
ADD:
Walter St. John, 93 points, Baffled Badgers
Buffalo, NY (hat)

Emerald Chou, 92 points, Angry Ants
Topeka, KS (shirt)

CHANGE: 
Bonnie Brooks wants a shirt, not a hat!

REMOVE: 
Lois Hart has requested to be removed from our list

```
INSERT INTO people
(first_name, last_name, quiz_points, team, city, state_code, shirt_or_hat)
VALUES
('Walter', 'St. John', '93', 'Baffled Badgers', 'Buffalo', 'NY', 'hat');

INSERT INTO people
(first_name, last_name, quiz_points, team, city, state_code, shirt_or_hat)
VALUES
('Emerald', 'Chou', '92', 'Angry Ants', 'Topeka', 'KS', 'shirt');

UPDATE people 
SET shirt_or_hat='shirt' 
WHERE id_number=12;

DELETE FROM people WHERE id_number=590;
```