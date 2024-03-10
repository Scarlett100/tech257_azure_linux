# DEPLOYING APP


# SSH INTO VM


# PLAN SCRIPT.


TWO STEPS: <br>
    - manually , working commands, must work without user input <br>

    - automate with a bash script
on Azure vm, we will need:
1,. Ubuntu 22.04 LTS -DONE
1. UPDATE & UPGRADE (ISSUE1. WITH USER PROMPT WITH UPGRADE COMMAND - NOT AN ISSUE ON 22.04)
      1. #update
        sudo apt update -y

        #upgrade
        sudo apt upgrade -y


#  INSTALL WEBSERVER -NGINX (ENSURE IT IS ENABLED)
# install nginx
```
sudo apt install -y nginx
```

# restart nginx
```
sudo systemctl restart nginx
```

# enable nginx
```
sudo systemctl enable nginx
```

# check status < not needed in script>
systemctl status nginx

3. right version of Node JS version 20.x (automatically will install npm) issue2 FIND OUT
```
https://deb.nodesource.com/setup_20.x | sudo -E bash - &&\
sudo apt-get install -y nodejs

. ```
![alt text](<../images/Node.js v20.x.png>)


4. right version of node js 
![alt text](../images/node_install.png)

1. ‘app’ folder with code - ISSUE 3 FIND OUT TO COPY APP FOLDER TO VM
2. in app folder, we need to do 2 commands:
    1. npm install
    2. npm start OR node.js


log out of vm
run command to copy app folder to virtual maching
first way:
scp or rsync

create a git repo:
for sole purpose of storing app folder call repo tech257-sparta-app
(git clone)


scp -i /c/Users/username/.ssh/private_key -r /c/Users/username/Downloads/app username@public-ip:/path/to/save

scp -i ~/.ssh/morgan-az-key -r app2 adminuser@172.167.181.33:.

```
![alt text](../images/mv_file.png)
```

rsync -avz -e "ssh -i ~/.ssh/morgan-az-key" ./app2 adminuser@172.167.181.33:.:.

after app copied do npm install, then npm start npm --version within app folder

ip addy : 3000

## git way
run this
git remote add origin https://github.com/Scarlett100/tech257-sparta-app.git
git branch -M master
git push -u origin master

to copy onto vm