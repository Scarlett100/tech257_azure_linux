If a vm doesn't work and it is still unhealthy after certain amount of time, the scale set will create a new one.![alt text](<Screenshot 2024-03-15 at 12.24.40.png>)


continuing to make vm:

![alt text](<Screenshot 2024-03-15 at 12.30.17.png>)


load balancer will have a special rule  that is you come in at port 50000, it will redirect you to port 80. if you click on the pencil next to the interface you will see out ports

![alt text](<Screenshot 2024-03-15 at 12.36.03.png>)

SCALING:
![alt text](<Screenshot 2024-03-15 at 12.42.27.png>)

hEALTH:
![alt text](<Screenshot 2024-03-15 at 12.43.35.png>)

user data:

# what i put into user data that worked
<br>
#!/bin/bash

# CD into app2 folder
cd /tech257-sparta-app/app2

#stopPm2 before rerunning.
pm2 kill 

# Start app with pm2
pm2 start app.js

<br>
![alt text](<Screenshot 2024-03-15 at 12.45.56.png>)

tags:

![alt text](<Screenshot 2024-03-15 at 12.46.32.png>)

when you restart will be unhealthy so you must reimage:

Reimage virtual machine in bar above




![alt text](<Screenshot 2024-03-15 at 15.04.47.png>)