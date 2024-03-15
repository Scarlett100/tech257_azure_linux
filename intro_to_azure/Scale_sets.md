# <center> #Scale sets <center/>



Scale Sets (SS) streamline the deployment and management of identical virtual machines (VMs) in Microsoft Azure. SS easily create a group of VMs that share the same configuration, automatically adjusting their number based on demand. This feature ensures high availability by distributing VM instances across multiple fault domains and update domains. Additionally, SS simplifies management tasks such as deploying updates and installing software across all VM instances simultaneously. It optimises costs by dynamically scaling the number of VMs to match workload demands, while Azure's built-in load balancing capabilities evenly distribute incoming traffic among the VM instances.


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


# <center> unhealthy statuses<center/>
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

If you want to get an unhealthy status again, you can restart instance, or start and stop instance. As you can see below I have restarted one instance and ended up with an unhealthy status:


 ![alt text](<Screenshot 2024-03-15 at 15.44.08.png>)

# <center>  How to ssh into instance <center/>
Outside of the testing stage we shouldn't really ssh into our scaleset vm's.
But if we must one way to do it is to first click on the instance we need, for this example I will use the vm that we restarted and is unhealthy. Once we click on it we must ssh into it.
![alt text](<Screenshot 2024-03-15 at 15.48.37.png>)

Once I put in my ssh details path it gives me a code to copy
![alt text](<Screenshot 2024-03-15 at 15.52.46.png>) <br>
However it gives us a private ip, this would only work if we are on the same network.

As you can see below, I have ssh'ed inside:
<br>

```
ssh -i ~/.ssh/morgan-az-key -p 50000 adminuser@4.158.120.166

I had to put the port 50000 and the ip of the load balancer
```
<br>
![alt text](<Screenshot 2024-03-15 at 16.04.23.png>)

However, when i try to ssh into the unhealthy instance by changing the port slightly:

```
ssh -i ~/.ssh/morgan-az-key -p 50001adminuser@4.158.120.166

I had to put the port 50001 and the ip of the load balancer
```
<br>

The connection is closed, because it has been unhealthy for more than 10 minutes
![alt text](<Screenshot 2024-03-15 at 16.10.34.png>)

If we look back at the instances, the unhealthy one has dissapeared and we only have the first one, and now a new one, titled number 2.
![alt text](<Screenshot 2024-03-15 at 16.11.33.png>)




![alt text](<Screenshot 2024-03-15 at 15.04.47.png>)


#
If a vm doesn't work and it is still unhealthy after certain amount of time, the scale set will create a new one.![alt text](<Screenshot 2024-03-15 at 12.24.40.png>)



# How to delete a vm scale set

There are two options:
1. If you have tags then you can go into your resource group and delete everything with a tag associated with the scale set.
2. You can manually select everything and begin to delete.

There are 4 things we need to delete.
load balancer
vms
ip