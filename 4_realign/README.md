# Realign

## Deleting rows
- using the DELETE command DELETE FROM [tableName] USING or WHERE
  - example: this will show more than ten rows in the "ev" table

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/1_basics/screencaps/psql_0basics_displayTables.png?raw=true "display tables")

  - example: after the DELETE command only 10 rows remain in the "ev" table

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/1_basics/screencaps/psql_0basics_displayTables.png?raw=true "display tables")


## Re-order the rows and index
- after exporting or importing tables the data may be chopped up by date or id
- for this example we can re-use the 2025 export from the exportCSV example
  - halt all processing on the table so new entries do not get mixed in
  - example: use SELECT * with LIMIT to see the current 2025 table
    - note: the "id" column is all out-of-order which makes new row inserts a problem

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/1_basics/screencaps/psql_0basics_displayTables.png?raw=true "display tables")


- use the following command to find the sequence index
  - SELECT column_default
  - FROM information_schema.columns
  - WHERE table_name = '[tableName]' AND column_name = '[sequenceColumnName]'

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/1_basics/screencaps/psql_0basics_displayTables.png?raw=true "display tables")

- use the following command to see the current sequence index using the output of the last command
  - SELECT last_value FROM [resultFromPreviousQuery]
    - note: this is disordered data inserted into a new table so it thinks it is starting at 1 

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/1_basics/screencaps/psql_0basics_displayTables.png?raw=true "display tables")

- use the following command to see the last index number from the disordered data
  - SELECT MAX([sequenceColumnName]) FROM [resultFromPreviousQuery]
    - note: this is disordered data inserted into a new table so it thinks it is starting at 1 

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/1_basics/screencaps/psql_0basics_displayTables.png?raw=true "display tables")
