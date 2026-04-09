# Basics

## How to see what tables are in the database
- use the \dt command to display tables
   - this database has one table called "ev"

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/1_basics/screencaps/psql_0basics_displayTables.png?raw=true "display tables")

## How to remove tables from the database
- use the DROP TABLE command ending with a semi-colon
   - seperate multiple tables with a comma
      - Ex: DROP TABLE table1, table2, table3;
- use the \dt command again to verify tables 

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/1_basics/screencaps/psql_0basics_dropTables.png?raw=true "drop tables")

## How to create tables in the database
- use the CREATE TABLE command which will extend the console command until it is closed
   - each column needs to have its data type defined and sometimes its size as well
   - in this example
      - VARCHAR is "Variable Characters" for alphanumeric strings
      - INT is "Integer" and can only use whole numbers
- close off the command with parenthesis and a semi-colon ");"
- use the \dt command again to verify tables

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/1_basics/screencaps/psql_0basics_createTables.png?raw=true "create tables")

## How to insert data into a table
- use the INSERT INTO command which will extend the console command until it is closed
   - put the column names seperated by commas into the parentheses with the INSERT command
- the VALUES command switches from column names to the inserted data
   - the values are also in parentheses
   - multiple entries are seperated by commas
- the final entry is ended with a semi-colon ";"
- the console should return "INSERT" with the row count, in this case 3
   - the first digit is the OID but that can be ignored for now

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/1_basics/screencaps/psql_0basics_insertRows.png?raw=true "insert rows")

## How to view all records in a table
- use SELECT * from [tableName] to get all rows from a table
   - the asterisk is the wildcard character so it will get everything
   - more complex selections can be made with tailored statements
- close off the command with a semi-colon ";"

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/1_basics/screencaps/psql_0basics_selectAll.png?raw=true "select all")
