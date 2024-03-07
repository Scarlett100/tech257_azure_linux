# Linux tasks

- [Linux tasks](#linux-tasks)
  - [Why is managing file ownership important?](#why-is-managing-file-ownership-important)
  - [What is the command to view file ownership?](#what-is-the-command-to-view-file-ownership)
  - [What permissions are set when a user creates a file or directory? Who does file or directory belong to?](#what-permissions-are-set-when-a-user-creates-a-file-or-directory-who-does-file-or-directory-belong-to)
- [Why does the owner, by default, not receive X permissions when they create a file?](#why-does-the-owner-by-default-not-receive-x-permissions-when-they-create-a-file)
- [2.8b Research managing file ownership](#28b-research-managing-file-ownership)
  - [Does being the owner of a file mean you have full permissions on that file?](#does-being-the-owner-of-a-file-mean-you-have-full-permissions-on-that-file)
  - [If you give permissions to the User entity, what does this mean?](#if-you-give-permissions-to-the-user-entity-what-does-this-mean)
  - [If you give permissions to the Group entity, what does this mean?](#if-you-give-permissions-to-the-group-entity-what-does-this-mean)
  - [If you give permissions to the Other entity, what does this mean?](#if-you-give-permissions-to-the-other-entity-what-does-this-mean)
  - [You give the following permissions to a \[file: Use\](file: Us "‌")r permissions are read-only, Group permissions are read and write, Other permissions are read, write and execute. You are logged in as the user which is owner of the file. What permissions will you have on this file? Explain.](#you-give-the-following-permissions-to-a-file-usefile-us-r-permissions-are-read-only-group-permissions-are-read-and-write-other-permissions-are-read-write-and-execute-you-are-logged-in-as-the-user-which-is-owner-of-the-file-what-permissions-will-you-have-on-this-file-explain)
  - [Here is one line from the ls -l. Work out everything you can about permissions on this file or directory.](#here-is-one-line-from-the-ls--l-work-out-everything-you-can-about-permissions-on-this-file-or-directory)
  - [What numeric values are assigned to each permission?](#what-numeric-values-are-assigned-to-each-permission)
  - [What can you with the values assign read + write permissions?](#what-can-you-with-the-values-assign-read--write-permissions)
    - [What value would assign read, write and execute permissions?](#what-value-would-assign-read-write-and-execute-permissions)
    - [What value would assign read and execute permissions?](#what-value-would-assign-read-and-execute-permissions)
    - [Often, a file or directory's mode/permissions are represented by 3 numbers. What do you think 644 would mean?](#often-a-file-or-directorys-modepermissions-are-represented-by-3-numbers-what-do-you-think-644-would-mean)
- [References](#references)

#2.8a

## Why is managing file ownership important?
Managing files is very important because it is pivotal concerning fill access and therefore maintanance of security.  



## What is the command to view file ownership?
The command is:
``` 
ls -l
``` 


## What permissions are set when a user creates a file or directory? Who does file or directory belong to?

By default, When new files are created the permissions given are: rw-rw-r– . The r, w, and x signify the read, write, and execute permissions.


# Why does the owner, by default, not receive X permissions when they create a file?
This is for safeguarding reasons, to ensure the file is not tampered with in a way that could pose security risks or deletion.

What command is used to change the owner of a file or directory?
Chown is used.

``` 
#command below changes the owner of the film called program.py to morgan
chown morgan program.py
``` 

# 2.8b Research managing file ownership
## Does being the owner of a file mean you have full permissions on that file? 
No, not technically, although you have all others, you do not have executable permissions by default.

## If you give permissions to the User entity, what does this mean?

The owner of the file is the **user**, this is usually the creator of the file gets  rw-rw-r–

## If you give permissions to the Group entity, what does this mean?

There is usually a **group** that consists of users. Joint ownership of a file decided the permissions given to group members. 


## If you give permissions to the Other entity, what does this mean?
A user can be related to more than group. It should be noted that you can also be niether an owner or group member, in this case you would be considered an **other**.

## You give the following permissions to a [file: Use](file: Us "‌")r permissions are read-only, Group permissions are read and write, Other permissions are read, write and execute. You are logged in as the user which is owner of the file. What permissions will you have on this file? Explain.

The file permissions will be read, write, and execute (rwx)
The  owner or **user** permission as read-only (r).
However, since you are logged in as the owner of the file, a special rule applies. 
File system permissions check your category first.
By default The owner (you) always has full control , therefore, means you can read, write, and execute the file.

## Here is one line from the ls -l. Work out everything you can about permissions on this file or directory.

#2.8c
## What numeric values are assigned to each permission?

Read (r): 4 <br>
Write (w): 2 <br>
Execute (x): 1 <br>


## What can you with the values assign read + write permissions?

Read (r): 4 <br>
Write (w): 2 <br>
Therefore, to represent read and write permissions (r + w), you would add the corresponding values:

Read + Write (r + w): 4 + 2 = 6
So, the numeric value 6 represents read and write permissions in Linux.

With this permission level, you can perform the same actions as described previously:

Read (r):

View the file contents . <br>
List the contents of a directory. <br>
Access information about the file. <br>
<br>
Write (w): <br>

Modify the content of the file. <br>
Create new files within a directory. <br>
Delete or rename files within a directory (provided you have the necessary permissions). <br>



### What value would assign read, write and execute permissions?
### What value would assign read and execute permissions?
### Often, a file or directory's mode/permissions are represented by 3 numbers. What do you think 644 would mean?


# References
please see references for info below

https://www.baeldung.com/linux/new-files-dirs-default-permission#:~:text=The%20operations%20that%20a%20user,%2C%20and%20execute%20permissions%2C%20respectively.
https://www.ibm.com/docs/en/aix/7.2?topic=c-chown-command#:~:text=Description,group%20can%20also%20be%20specified.







