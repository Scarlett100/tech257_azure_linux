
# Manually connect database and VM

- [Manually connect database and VM](#manually-connect-database-and-vm)
- [Manually work out each command](#manually-work-out-each-command)
- [install mongo db](#install-mongo-db)
- [In app vm](#in-app-vm)
- [NPM Install](#npm-install)
- [references](#references)





Go through the process we did with the app VM to deploy the app, but now to deploy the database:

when we create vm we must use the
![alt text](<../images/Screenshot 2024-03-13 at 11.59.06.png>)
# Manually work out each command

once I had ssh'd into my vm i ran an update and upgrade:
 ``` 
# Update
sudo apt update -y

#  upgrade for bypassing user input
sudo DEBIAN_FRONTEND=noninteractive apt-get upgrade -y

 ``` 

# install mongo db

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


edit bind file in vim:

sudo vim /etc/mongod.conf
change bind ip to all 0's

check changes made
cat /etc/mongod.conf

# check status again:
sudo systemctl status mongod
will see that it is running.

![alt text](<../images/Screenshot 2024-03-13 at 12.23.39.png>)
``` 

# In app vm
 next we in another terminal and ssh into our app terminal and run:

 export DB_HOST=mongodb://<ip-address>:27017/posts

 export DB_HOST=mongodb://10.0.3.5:27017/posts

 we use the *private* ip of the db vm.


 check env variable
 printenv DB_HOST 

 ps aux
 find pm2, kill pm2: sudo kill 968 <968 is pm2 process id>


![alt text](<../Linux/Screenshot 2024-03-13 at 12.45.59.png>)

# NPM Install

If we just run npm install from where we are it will fail.


![alt text](<../Linux/Screenshot 2024-03-13 at 13.08.43.png>)

don't need to do if we have app folder in home directpry but since i do we must ass the **-E**
sudo -E npm install

sudo -E npm start
![alt text](<../Linux/Screenshot 2024-03-13 at 13.09.43.png>)


App will now be back up running

![alt text](<../Linux/Screenshot 2024-03-13 at 12.53.56.png>)

and we will see app is back online and post page works once we add /posts to the end of ip

![alt text](<../Linux/Screenshot 2024-03-13 at 12.52.55.png>)




# references

https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/

