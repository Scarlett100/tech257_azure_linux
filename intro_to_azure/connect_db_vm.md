
# Manually connect database and VM




- [Manually connect database and VM](#manually-connect-database-and-vm)
- [create db vm](#create-db-vm)
- [Manually work out each command](#manually-work-out-each-command)
- [Install mongo db](#install-mongo-db)
- [Edit bind file in vim:](#edit-bind-file-in-vim)
- [In app vm](#in-app-vm)
- [NPM Install](#npm-install)
- [Check application](#check-application)
- [Check application with database](#check-application-with-database)
- [references](#references)





The goal with this task is to get /posts page working manually to do this, we will need to to deploy a database and connect a database vm and our app vm through an environment variable that houses our private IP.

# create db vm

There are a few things to note:
1. private subnet
2. using ramons image for now
3. only using ssh port
 <br>

 As you can see below, the validation passed.
   
![alt text](<../images/Screenshot 2024-03-13 at 11.59.06.png>)
# Manually work out each command

Once I had ssh'd into my vm I ran an update and upgrade:
 ``` 
# Update
sudo apt update -y

#  upgrade for bypassing user input
sudo DEBIAN_FRONTEND=noninteractive apt-get upgrade -y

 ``` 

# Install mongo db

``` 
# install curl
sudo apt-get install -y gnupg curl

# get our key

curl -fsSL https://www.mongodb.org/static/pgp/server-7.0.asc | \
   sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg \
   --dearmor


echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-7.0.list

# run an update
sudo apt-get update -y

# install mongo

sudo apt-get install -y mongodb-org=7.0.6 mongodb-org-database=7.0.6 mongodb-org-server=7.0.6 mongodb-mongosh=2.1.5 mongodb-org-mongos=7.0.6 mongodb-org-tools=7.0.6
``` 

# Edit bind file in vim:

``` 
sudo vim /etc/mongod.conf
change bind ip to all 0's so that we have the correct bind IP

check changes made
cat /etc/mongod.conf

# check status again:
sudo systemctl status mongod
You will see that it is running, as seen in photo below.
``` 

![alt text](<../images/Screenshot 2024-03-13 at 12.23.39.png>)


# In app vm
 Next we in another terminal and ssh into our app vm (remember we are using the public ip) and run:

 ``` 

 export DB_HOST=mongodb://<ip-address>:27017/posts

 export DB_HOST=mongodb://10.0.3.5:27017/posts

Note, that we use the *private* ip of the db vm.
Also note, in our script, we may not want to connect to db, so we can comment this DB_HOST line out.


 Check env variable has been set
 ``` printenv DB_HOST 

``` 

If we have used pm2 with user data, as we have it will not stop the process so we must first find the process id with 
``` 
ps aux

 ``` 

 <br>
 then we must find pm2, and kill it. To do this we must run:
 <br>

 ``` 
 sudo kill 968 <968 is pm2 process id>
 
  ``` 


![alt text](<../Linux/Screenshot 2024-03-13 at 12.45.59.png>)

# NPM Install

If we just run npm install from where we are it will fail.


![alt text](<../Linux/Screenshot 2024-03-13 at 13.08.43.png>)

don't need to do if we have app folder in home directory but since i do we must ass the **-E**
sudo -E npm install

sudo -E npm start
![alt text](<../Linux/Screenshot 2024-03-13 at 13.09.43.png>)


# Check application


App will now be back up running

![alt text](<../Linux/Screenshot 2024-03-13 at 12.53.56.png>)

# Check application with database

and we will see app is back online and post page works once we add /posts to the end of ip

![alt text](<../Linux/Screenshot 2024-03-13 at 12.52.55.png>)




# references

https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/
https://www.hostinger.co.uk/tutorials/how-to-install-mongodb-on-ubuntu/
