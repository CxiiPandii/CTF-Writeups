We’re running with an assumption that d34th drove around and connected to various cell towers the day leading up to the attack.

We need you to determine which device IMEI connected to the most unique towers on September 7 from 16:10 to 18:54.

Submit the flag as flag{device_imei}. Example: flag{123456789012345}.
________________________________________________________________________________

 Sadly I never found the flag for this challenge but I did attempt it!

Same SSH  from the previous SkyWave Challenges we establish the connection.

When we lookinto the connections Table we find theres  a column called "connection time "  we want to set our perameter to the ones rquired while it returns the tower id and device id
Query looks like this: 
SELECT DISTINCT tower_id, device_id 
FROM Connections 
WHERE connection_time BETWEEN "2024-09-07 16:10:00" AND "2024-09-07 18:54:00";

With this I got that there were two devices  that were connected at the time. And they were both connected to 5 unique towers in the specified time frame.
<img width="1583" height="948" alt="image" src="https://github.com/user-attachments/assets/908b53eb-6097-460f-a541-256e7aceba9c" />
