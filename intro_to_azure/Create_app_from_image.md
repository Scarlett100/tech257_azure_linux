
- [1. Create an image](#1-create-an-image)
- [2. Make sure dependencies are installed](#2-make-sure-dependencies-are-installed)
- [3. Create a new vm](#3-create-a-new-vm)
- [4. Import section of bash script](#4-import-section-of-bash-script)
- [5. Blockers](#5-blockers)


Our task was to be able to deploy an app with user data and with an image + a small amount of user data.

# 1. Create an image
 Firstly, we had to create a custom image named 
tech257-morgan-ready-to-run-app-image. 

![alt text](../images/image_created.png)

# 2. Make sure dependencies are installed

Secondly, this image had to have all dependencies installed 
with the app folder somewhere off the root directory, eg. /repo/app:
we have done this via our script.:

![alt text](../images/!binbash.png)

# 3. Create a new vm
Thirdly, we had to create a new VM using the custom image we had created:
![alt text](<../images/Screenshot 2024-03-12 at 16.48.22.png>)

# 4. Import section of bash script
Next we had to use a small portion of your Bash script to paste into user data to:

cd into the app folder
run the app
![alt text](../images/userdatafomrimage.png)

# 5. Blockers
As a blocker, I should have added a stop. Therefore, I will rebuild when I can and add stop. 
I have not yet been able to run it but the desired outcome is that it should be much quicker.