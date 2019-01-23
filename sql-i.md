## Creating Tables

- Define these datatypes in PostgreSQL:

  - NULL- nothing there
  - INTEGER- whole number
  - DECIMAL- not whole numbers
  - FLOAT- how many numbers you will allow and where decimal will be 
  - TEXT- character string as long as data entered
  - VARCHAR(n)- character string with designated length

- What does SERIAL do in Postgres? (Note: in chinook.ml this will be INTEGER PRIMARY KEY AUTOINCREMENT)-creates a new number that adds one to the current highest value and assigns to new data

- What is the syntax for creating a new table?

  CREATE TABLE table_name
(
column1 data_type(size),
column2 data_type(size),
column3 data_type(size),
....
);

table_name:  name of the table.
column1: name of the first column.
data_type: Type of data we want to store in the particular column. 
            For example,int for integer data.
size: Size of the data we can store in a particular column. For example if for
a column we specify the data_type as int and size as 10 then this column can store an integer
number of maximum 10 digits. 

- On <http://postgres.devmountain.com> , create a student table with this schema:
  - id - integer - SERIAL
  - first_name - varchar(255)
  - hometown - varchar(255)
  - fun_fact - text

  CREATE TABLE student
(
  id SERIAL,
  first_name varchar(255),
  hometown varchar(255),
  fun_fact text
 )

## Inserting Data (Section 9)

- What is the syntax for inserting values into a table?

- Insert the following data into the student table from above:
  
  ```
  first_name: 'Eric'
  hometown: 'Dallas'
  fun_fact: NULL
  ```
  
  ```
  first_name: 'James'
  hometown: 'Dallas'
  fun_fact: 'Postgres is progress.'
  ```
INSERT INTO student(first_name, hometown, fun_fact)
VALUES
('Eric', 'Dallas', null),
('James', 'Dallas', 'Postgres is progress.');


## Updating Data (Section 9)

- What is the syntax for updating existing values in a table?

- Update Eric's fun_fact to be 'I love SQL' using his id.

UPDATE student
set fun_fact = 'I love SQL'
where first_name = 'Eric';

## Querying Data (Section 2 and 3)

### Syntax

- How do you select all columns from a table?
SELECT * FROM student

- How do you select 2 specific columns from a table?

SELECT column1, column2 FROM student

- What does DISTINCT do?
Eliminated duplicates in return values

- What does ORDER BY do?
Tells what data the results should be ordered by

- Practice: Get all the information we currently have in the student table, sorted by id, with the highest id first.

SELECT * FROM student
ORDER BY id

### WHERE clauses

- What are 4 comparison operators in PostgreSQL? (Hint: Look in the WHERE section)
 IN, OR, NOT IN, AND, +, <,>,>=, <> or != not, 

- What do AND, OR and IN do?
AND- chains, OR- will take anything with either value, IN- has the values listed

- How do you check for NULL values? (Hint: it's not = NULL or != NULL)
IS NULL

- What does LIMIT do?
Returns the specified number of data points from the top

- What do each of these aggregate functions do?

  - min() gets the minimum value in a set 
  - max() gets the max value in a set
  - sum() calculates the values in a set
  - avg() averages the values in a set
  - count() counts rows in a table

- How does LIKE work?
serches for a specified pattern, can be used for case sensitivity depending on sql (postgress is ILIKE) 

- What's the difference between % and \_ with LIKE?

200% starts with 200 
%200% has 200 in it
_00% has 00 in the second and third position
2_%_% any values that start with 2 and are at least 3 char long
%2 ends in 2
_2%3 has 2 in second pos and end in 3
2___3 has any value in 5 digit number that start with 2 and end with 3 
