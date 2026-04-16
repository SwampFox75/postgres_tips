# Realign

## Deleting rows
- using the DELETE command DELETE FROM [tableName] USING or WHERE
  - example: this will show more than ten rows in the "ev" table

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/4_realign/screencaps/psql_3realign_show20.png?raw=true "show 20")

  - example: after the DELETE command only 10 rows remain in the "ev" table

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/4_realign/screencaps/psql_3realign_delete.png?raw=true "delete")


## Re-order the Sequence ID
- after importing tables the data may be disordered by their sequence ID
- for this example we can re-use the 2025 export from the exportCSV example
- halt all processing on the table so new entries do not get mixed in
  - example: use SELECT * with LIMIT to see the current 2025 table
    - note: the "id" column is all out-of-order which makes new row inserts a problem

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/4_realign/screencaps/psql_3realign_order0.png?raw=true "step 1")

- STEP 1: use the following command to FIND the sequence index in the schema
  - SELECT column_default
  - FROM information_schema.columns
  - WHERE table_name = '[tableName]' AND column_name = '[sequenceColumnName]';
    - note: the variable for the index will be the first part in single quotes within the parenthesese

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/4_realign/screencaps/psql_3realign_order1.png?raw=true "step 2")

- STEP 2: use the following command to SEE the current sequence index value using the output of the last command
  - SELECT last_value FROM [sequenceIndexVariable];
    - note: this is disordered data inserted into a new table so it thinks it is starting at 1 

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/4_realign/screencaps/psql_3realign_order2.png?raw=true "step 3")

- STEP 3: use the following command to SEE the last index number from the disordered data
  - SELECT MAX([sequenceColumnName]) AS [customColumnName] FROM [tableName];
    - note: this is the last sequence number from the disordered inserted data of 2025 cars
    - note: the current sequence is 1 but the last inserted row has sequence 99986

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/4_realign/screencaps/psql_3realign_order3.png?raw=true "step 4")

- STEP 4: use the following command to SET the sequence index to the last one from the inserted data
  - SELECT SETVAL('[sequenceIndexVariable]', [number OR (query)]);
    - note: this is going to match the last sequence number from the disordered inserted data
    - note: the sequence index can be entered manually but its going to be more accurate to fetch it just in case

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/4_realign/screencaps/psql_3realign_order4.png?raw=true "step 5")

- to verify the example an insert will be performed and the new id should be one newer in sequence
- inserting a parody car into the ev table

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/4_realign/screencaps/psql_3realign_order5.png?raw=true "proof 0")

- to verify the insert and result of the sequence index running SELECT on the last ids

![alt text](https://github.com/SwampFox75/postgres_tips/blob/main/4_realign/screencaps/psql_3realign_order6.png?raw=true "proof 1")
