# Import CSV

## CSV Directory & Permissions
- the command-line PostgreSQL account "postgres" has its own permissions
- to avoid permission problems with the CSV files place them in either:
   - /tmp on Linux or Mac is accessible by all users
   - C:\Users\Public on Windows is accessible by all users
 
## If a table does not exist CREATE TABLE
- make a column of the correct data type for each column to be imported
- the "id" column here is new from the Basics
   - SERIAL type increments by one each row
   - PRIMARY KEY means it can not have duplicate values so each row is uniquely referenced

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/2_importCSV/screencaps/psql_1importCSV_createTable.png?raw=true "create tables")

## Use the \COPY command
- to keep it simple make sure the CSV file columns match the table
- start the command with \COPY [tableName] ([columnName1], [columnName2]...)
- enter allows the command to continue on the next line, FROM '[CSVfilePath]'
- then DELIMITER '[delimiterCharacter]'
   - DELIMITER can only accept one character to use an escape character "\" add the E flag
      - example: DELIMITER E'\t' is needed for the TAB character
- CSV HEADER tells it to ignore the first row
- close the command with the semi-colon character ";"
- it should return how many rows were copied if successful

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/2_importCSV/screencaps/psql_1importCSV_copyCSV.png?raw=true "copy CSV")

## Select rows from the table to verify
- the example import pulled in 100,000 rows
- using just SELECT * FROM [tableName] from the Basics would try to return all 100,000
- use LIMIT at the end of the command to request a few to verify it worked
   - example: SELECT * FROM ev LIMIT 10

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/2_importCSV/screencaps/psql_1importCSV_selectTen.png?raw=true "select ten")
