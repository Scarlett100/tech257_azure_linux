# Blob Task

So I had to edit my script a few times because it was not finding the index.ejs file. So I decided to make it very clear how to get to index file by cd'ing into folder instead of having views/index.ejs in sed file, just index.ejs. First we had to have the app running, then write a script to add the cat.

you can see in my screenshot below, the cat is showing!

![alt text](<Screenshot 2024-03-15 at 10.28.18.png>)

# <center> Script <center/>

One of the things i found incredibly useful, was on microsftf documents, it mentioned you can add access when creating containers and storage accounts.<br>
For example at the end of making a storage account you can add 
 ```
 --allow-blob-public-access true
 ```
 you can see the full command below:
 <br>

  ```
# Create a storage account
az storage account create \
 --name tech257morganstorage \
 --resource-group tech257 \
 --location uksouth \
 --sku Standard_LRS \
 --allow-blob-public-access true
 ```

 Likewise when making a container we can do the same, but it is imperative we also **set** the permission afterward. Note the ** --public-access container** flag. 

 ```
#create container
 az storage container create \
    --account-name tech257morganstorage \
    --name testcontainer \
    --public-access container \
    --auth-mode login

#az storage container set-permission to make blob public\
az storage container set-permission \
    --name testcontainer \
    --account-name tech257morganstorage \
    --public-access container \
    --auth-mode login
 ```


# <center> Working Script <center/>

 ```
 #!/usr/bin/bash


# upgrade for bypassing user input, may not be needed but just in case
sudo DEBIAN_FRONTEND=noninteractive apt-get upgrade -yq


# Create a storage account
az storage account create --name tech257morganstorage --resource-group tech257 --location uksouth --sku Standard_LRS  --allow-blob-public-access true

# sleep for 15

sleep 15

# enable anonymous blob access on storage account
# added a  --allow-blob-public-access flag to storage account


#create container
 az storage container create \
    --account-name tech257morganstorage \
    --name testcontainer \
    --public-access container \
    --auth-mode login

#az storage container set-permission to make blob public\
az storage container set-permission \
    --name testcontainer \
    --account-name tech257morganstorage \
    --public-access container \
    --auth-mode login


#download a cat picture (jpg) using the curl command
curl -o NationalGeographic_2572187_square.jpg https://i.natgeofe.com/n/548467d8-c5f1-4551-9f58-6817a8d2c45e/NationalGeographic_2572187_square.jpg

#rename the cat pic to newcat.jpg
mv NationalGeographic_2572187_square.jpg newcat.jpg


#upload blob

az storage blob upload \
    --account-name tech257morganstorage \
    --container-name testcontainer \
    --name newcat.jpg \
    --file newcat.jpg \
    --auth-mode login

#make blob public <--command done with container

# cd to home
cd /

# CD into app2/views folder
cd /tech257-sparta-app/app2/views

# make a backup of this file
sudo cp index.ejs index.ejs.bk

# modify homepage file (index.ejs found in views folder) to include cat image in blob storage (could use sed command to replace )
sudo sed -i "/<h2>The app is running correctly.<\/h2>/a <img src=\"https://tech257morganstorage.blob.core.windows.net/testcontainer/newcat.jpg\">" index.ejs

# cd back to app folder
cd ..

# stopPm2 before rerunning.
pm2 kill 

# Start app with pm2
pm2 start app.js
 ```

 Below you can see my storage account, container and blob exists:

## STORAGE ACCOUNT
 ![alt text](<Screenshot 2024-03-15 at 10.39.54.png>)

 ## CONTAINERS ACCOUNT

 ![alt text](<Screenshot 2024-03-15 at 10.40.39.png>)

## BLOBS

 ![alt text](<Screenshot 2024-03-15 at 10.44.05.png>)