We need to determine which device had the longest running connection out of the towers with the following coordinates:

    (41.639642, -79.220682)
    (40.598271, -78.801089)
    (41.045892, -79.068358)
    (41.257279, -77.529468)

Additionally, let’s focus on only finding the longest running connection with a dBm greater than -100.

Submit the flag as flag{device_imei}. Example: flag{123456789012345}.
__________________________________________________________________________________________


I really didnt want to do a join Query for this so I end up doing it the long way. So bear with me!

Once again I looked through all the tables useing simple SELECT * FROM statements to familiarize myself with the tables and the information they have.
I also took screen shots on the side of the top labels of the tables so I could refrence later on when makeing other Query statements.

Using this query format I rant it four time with each lat and long that we were given from the prompt
SELECT DISTINCT tower_id FROM WHERE latitude =  "...." AND longitude = "....";
And I found these belonged to towers 105, 123, 187, 200
<img width="1410" height="246" alt="image" src="https://github.com/user-attachments/assets/43e1d6c1-7566-476c-a581-89b93e4b4a4f" />
<img width="1373" height="326" alt="image" src="https://github.com/user-attachments/assets/08087779-ce86-40cd-b0a3-b3425af7dd1f" />
<img width="1390" height="319" alt="image" src="https://github.com/user-attachments/assets/b6f8afc5-f82a-4751-99c9-8866f30bbdc6" />
<img width="1402" height="326" alt="image" src="https://github.com/user-attachments/assets/862ebf2a-da5d-46bd-9098-ef9d6fdc2e1a" />


Using this information when the do a new query:
SELECT connection_duration, singal_strength FROM Connections WHERE tower_id = " ... "
And ran it for all the tower IDs we captured.
Tower 105
<img width="1603" height="915" alt="image" src="https://github.com/user-attachments/assets/7533c782-215a-493c-bd73-df8f410b4791" />

Tower 123
<img width="1595" height="546" alt="image" src="https://github.com/user-attachments/assets/9ba3fff7-f7c4-4b61-91a6-99e3e81fc021" />

Tower 187
<img width="1576" height="768" alt="image" src="https://github.com/user-attachments/assets/fa604521-ed04-48df-b46f-62675df7b295" />

Tower 200
<img width="1572" height="778" alt="image" src="https://github.com/user-attachments/assets/7c32e1cd-a744-4bba-bbc4-88a8671e8d49" />

From the above Querys we were able to find that Tower 200 had the longest duration time at 85709 now we can look for its imei!
At this point I was looking on how to connect the Device table and COnnections table for I now knew the duration. I then saw that both tables held device_id.
I used a simple Query: SELECT device_id FROM Connections WHERE tower_id = "200" AND connection_duration = "85709"
<img width="1571" height="300" alt="image" src="https://github.com/user-attachments/assets/c2467bd9-004d-4963-8bca-b861c40fc923" />

It gave me the device id of 344. Now that we have the device id we can now go into the Devices table and look for its imei.
SELECT device_imei FROM Devices WHERE device_id = "344";

And from there we found the flag!




