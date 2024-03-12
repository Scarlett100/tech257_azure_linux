# Reverse Proxy Manually


To find where the default file is:
```
/etc/nginx/sites-available/
```
2. Copy the default file in case of any issues, i have made a backup with the bk file
```
sudo cp default default.bk
```
![alt text](../images/renamining_default.png)

Then make a simple change in the default file changing the:

```
try_files $uri $uri/ =404;

to 

proxy_pass http: //127.0.0.1:3000 

the 127.0.0.1 means this computer.
```
It must be remembered to do with sudo priveledges to be able to access file. Once saved, you can go back to the home of the repo and restart ngix to recognise the changes: 
```
# Restart nginx
sudo systemctl restart nginx

# Enable nginx
sudo systemctl enable nginx
```
in the folder the app resides in run:

#npm start 
if you have yet to install npm, an
npm install will be needed beforehand.

Once succesful you will get the below message:

![alt text](../images/dapp_listening.png)

and you can go to your browser and enter your azure ip (not the 127.0.0.1) entered in default and you will get the below:

![alt text](../images/manual_reverse_proxy.png)


To automate it within our script we must put the below after we install :

sudo sed -i "s|try_files .*;|proxy_pass http://127.0.0.1:3000;|g" /etc/nginx/sites-available/default

