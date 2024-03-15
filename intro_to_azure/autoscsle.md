If a vm doesn't work and it is still unhealthy after certain amount of time, the scale set will create a new one.![alt text](<Screenshot 2024-03-15 at 12.24.40.png>)


continuing to make vm:

![alt text](<Screenshot 2024-03-15 at 12.30.17.png>)

## Load Balancers
Load balancer will have a special rule  that is you come in at port 50000, it will redirect you to port 80. if you click on the pencil next to the interface you will see out ports. Load balancers  distributing incoming network traffic effectively across  backend servers or resources. Load balancers allow us to increase availability by distributing resources within and across zones.They also load balance external and internal traffic to Azure virtual machines whilst efficiently establishing outbound connectivity for vm's.

![alt text](<Screenshot 2024-03-15 at 12.36.03.png>)

## SCALING:
![alt text](<Screenshot 2024-03-15 at 12.42.27.png>)

## HEALTH:
![alt text](<Screenshot 2024-03-15 at 12.43.35.png>)

user data:

# what i put into user data that worked
<br>

```
#!/bin/bash

# CD into app2 folder
cd /tech257-sparta-app/app2

#stopPm2 before rerunning.
pm2 kill 

# Start app with pm2
pm2 start app.js
 ```
<br>
![alt text](<Screenshot 2024-03-15 at 12.45.56.png>)

tags:

![alt text](<Screenshot 2024-03-15 at 12.46.32.png>)

## My healthy Scaleset.
![alt text](<Screenshot 2024-03-15 at 15.04.47.png>)


# <center> How to create an unhealthy image for testing <center/>
The user data runs on the provisioning of a vm, so when you restart the user data the vm won't reload the user data. Likewise when you restart a scale set it just restarts the vm's associated. User data only runs once. As you can see below when we restart our vm's are unhealthy: 
<br>
![alt text](<Screenshot 2024-03-15 at 15.22.56.png>)

One way in which we can fix this is to reimage the scale set. Reimaging refers to going over the disk with a new image, imagine a fresh vm, a clean slate.
This is how we provision:
![alt text](<Screenshot 2024-03-15 at 15.29.12.png>)

you can see that as the update is running they have changed to healthy:
![alt text](<Screenshot 2024-03-15 at 15.31.03.png>)

Now the status is restored to running:
<br>

![alt text](<Screenshot 2024-03-15 at 15.31.50.png>)


If we refresh the load balancer ip we will find the app is back up, whwereas before we got a bad gateway error:

![alt text](<Screenshot 2024-03-15 at 15.34.14.png>)


# <center>  How to ssh into instance <center/>


# How to delete a vm scale set

There are two options:
1. If you have tags then you can go into your resource group and delete everything with a tag associated with the scale set.
2. you can manually select eveythin and begin to delete.




![alt text](<Screenshot 2024-03-15 at 15.04.47.png>)