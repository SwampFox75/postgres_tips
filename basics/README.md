# Basics

## How to see what tables are in the database
- Use the \dt command to display tables
   - This database has one table called "ev"

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/basics/psql_0basics_displayTables.png?raw=true "display tables")

## How to remove tables from the database
- Use the DROP TABLE command ending with a semi-colon
   - seperate multiple tables with a comma
      - Ex: DROP TABLE table1, table2, table3;
- Use the \dt command again to verify tables 

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/basics/psql_0basics_dropTables.png?raw=true "drop tables")

## How to create tables in the database
- Use the CREATE TABLE command which will extend the console command until it is closed
   - each column needs to have its data type defined and sometimes its size as well
   - in this example
      - VARCHAR is "Variable Characters" for alphanumeric strings
      - INT is "Integer" and can only use whole numbers
- close off the command with parenthesis and a semi-colon ");"

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/basics/psql_0basics_createTables.png?raw=true "drop tables")
