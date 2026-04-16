# Realign

## Deleting rows
- using the DELETE command DELETE FROM [tableName] USING or WHERE
  - example: this will show more than ten rows in the "ev" table

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/4_realign/screencaps/psql_3realign_show20.png?raw=true "show 20")

  - example: after the DELETE command only 10 rows remain in the "ev" table

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/4_realign/screencaps/psql_3realign_delete.png?raw=true "delete")


## Re-order the rows and index
- after exporting or importing tables the data may be disordered by their sequence id
- for this example we can re-use the 2025 export from the exportCSV example
  - halt all processing on the table so new entries do not get mixed in
  - example: use SELECT * with LIMIT to see the current 2025 table
    - note: the "id" column is all out-of-order which makes new row inserts a problem

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/4_realign/screencaps/psql_3realign_order0.png?raw=true "step 1")


- use the following command to find the sequence index
  - SELECT column_default
  - FROM information_schema.columns
  - WHERE table_name = '[tableName]' AND column_name = '[sequenceColumnName]'

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/4_realign/screencaps/psql_3realign_order1.png?raw=true "step 2")

- use the following command to see the current sequence index using the output of the last command
  - SELECT last_value FROM [resultFromPreviousQuery]
    - note: this is disordered data inserted into a new table so it thinks it is starting at 1 

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/4_realign/screencaps/psql_3realign_order2.png?raw=true "step 3")

- use the following command to see the last index number from the disordered data
  - SELECT MAX([sequenceColumnName]) FROM [tableName]
    - note: this is the last sequence number from the disordered inserted data

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/4_realign/screencaps/psql_3realign_order3.png?raw=true "step 4")

- use the following command to set the sequence index to the last one from the inserted data
  - SELECT MAX([sequenceColumnName]) FROM [tableName]
    - note: this is the last sequence number from the disordered inserted data

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/4_realign/screencaps/psql_3realign_order4.png?raw=true "step 5")

- use the following command to set the sequence index to the last one from the inserted data
  - SELECT MAX([sequenceColumnName]) FROM [tableName]
    - note: this is the last sequence number from the disordered inserted data

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/4_realign/screencaps/psql_3realign_order5.png?raw=true "proof 0")

- use the following command to set the sequence index to the last one from the inserted data
  - SELECT MAX([sequenceColumnName]) FROM [tableName]
    - note: this is the last sequence number from the disordered inserted data

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/4_realign/screencaps/psql_3realign_order6.png?raw=true "proof 1")
