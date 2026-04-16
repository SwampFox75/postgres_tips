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

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/2_importCSV/screencaps/psql_1importCSV_createTables.png?raw=true "create tables")
