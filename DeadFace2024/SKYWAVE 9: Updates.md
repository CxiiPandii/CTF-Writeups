(Forgot to copy the prompt) But the flag was the amount of Software Updates done on a tower.

Connected  to the SSH from the previous challenges.

Used the command "SHOW TABLES;" TO fimalrize my self again with the tables.
<img width="739" height="614" alt="image" src="https://github.com/user-attachments/assets/568edb0b-dae0-4b4e-b422-3cebfd85a53f" />


Then Used the command "SELECT * FROM Tower_Maintenance;" to see the tables scheme. This allowed me to see what were the column names in each table and the information they held.

Then used command SELECT * FROM Tower_Maintenance WHERE maintenance_type = Software updates;
Using this command I got back 96 rows which is actually inccorect.
<img width="1540" height="511" alt="image" src="https://github.com/user-attachments/assets/759218e9-f6ee-4c64-8604-c6c9bf5fd8f9" />

I then went back and thought what could have fone wrong. Then I decided to run the query with DISTINCT and specify DISTINCT for the tower_id column.
Query: SELECT DISTINCT tower_id FROM Tower_Maintenance WHERE maintenance_type = Software updates;
And from here we got the correct amount of rows for the flag!
