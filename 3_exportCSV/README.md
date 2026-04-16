# Export CSV

## CSV Directory & Permissions
- the command-line PostgreSQL account "postgres" has its own permissions
- to avoid permission problems with the CSV files place them in either:
   - /tmp on Linux or Mac is accessible by all users
   - C:\Users\Public on Windows is accessible by all users
 
## See what tables are in the database
- use the \dt command to display tables
   - this database has one table called "ev"

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/1_basics/screencaps/psql_0basics_displayTables.png?raw=true "display tables")

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

## Select a few rows from the table to verify
- the example import pulled in 100,000 rows
- using just SELECT * FROM [tableName] from the Basics would try to return all 100,000
- use LIMIT at the end of the command to request a few to verify it worked
- close the command with the semi-colon character ";"
   - example: SELECT * FROM ev LIMIT 10;

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/2_importCSV/screencaps/psql_1importCSV_selectTen.png?raw=true "select ten")

## Get a total row count from the table to verify
- the example import pulled in 100,000 rows
- use SELECT COUNT(*) AS [customColumnName] FROM [tableName]
- COUNT is a aggregation and the asterisk means everything, this counts every row
- "AS" gives the COUNT a name of your choosing
   - try to pick short descriptive names that are not also SQL commands
      - example: re-using just "COUNT" as a name in this case
- close the command with the semi-colon character ";"
   - example: SELECT COUNT(*) AS row_count FROM ev;

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/2_importCSV/screencaps/psql_1importCSV_rowCount.png?raw=true "row count")
