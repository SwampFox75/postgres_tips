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

## Export a whole table to CSV
- start the command with \COPY [tableName]
- enter allows the command to continue on the next line, TO '[CSVfilePath]'
- then DELIMITER '[delimiterCharacter]'
   - DELIMITER can only accept one character to use an escape character "\" add the E flag
      - example: DELIMITER E'\t' is needed for the TAB character
- CSV HEADER tells it to put the header as the first row
- close the command with the semi-colon character ";"
- it should return how many rows were copied if successful

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/3_exportCSV/screencaps/psql_2exportCSV_exportTable.png?raw=true "export table")

## Export a query to CSV
- start the command with \COPY ([SQLQuery])
- enter allows the command to continue on the next line, TO '[CSVfilePath]'
- then DELIMITER '[delimiterCharacter]'
   - DELIMITER can only accept one character to use an escape character "\" add the E flag
      - example: DELIMITER E'\t' is needed for the TAB character
- CSV HEADER tells it to put the header as the first row
- close the command with the semi-colon character ";"
- it should return how many rows were copied if successful
- in this case it is getting all cars made in 2025

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/3_exportCSV/screencaps/psql_2exportCSV_exportQuery.png?raw=true "export query")

## Verifying the exported files
- this has to be outside the postgres console
- go to where the CSV files were supposed to be made
   - example: in this case it is on Linux so "ls /tmp/"

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/3_exportCSV/screencaps/psql_2exportCSV_lsCSV.png?raw=true "ls CSV")

## Verifying the full export
- this has to be outside the postgres console
- check the full export CSV
   - example: in this case it is on Linux so "head -n 10 [filePath]"

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/3_exportCSV/screencaps/psql_2exportCSV_checkFull.png?raw=true "check full")

## Verifying the query export
- this has to be outside the postgres console
- check the query export CSV and verify it is all cars made in 2025
   - example: in this case it is on Linux so "head -n 10 [filePath]"

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/3_exportCSV/screencaps/psql_2exportCSV_check2025.png?raw=true "check 2025")
