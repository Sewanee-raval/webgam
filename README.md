# webgam
These PHP pages along with GAM will allow you to use Apache for specific GAM purposes, protected by a basic username\password challenge.  I don't claim this is the best way to do it, or even a particularly good way to do it.  I claim it is a way to do it.  Call it a starting point!

## Proper Permissions of the User Folder where GAM is installed (for example /home/gamuser)
```
drwxr-xr-x  gamuser apache
chown gamuser:apache /home/gamuser
```
## Permissions for folder /home/gamuser/bin
```
dr-xr-xr-x  gamuser apache
```
## Permissions for folder /home/gamuser/bin/gam
```
drwxrwx---  gamuser apache
```
## Permissions for files inside GAM directory
```
-r--r--r--  gamuser apache  nobrowser.txt
-r--r--r--  gamuser apache  lastupdatecheck.txt
-r--r--r--  gamuser apache  oauth2service.json
-r--r--r--  gamuser apache  client_secrets.json
-rw-r--r--  gamuser apache  noupdatecheck.txt
-rw-r--r--  gamuser apache  whatsnew.txt
-rw-r--r--  gamuser apache  LICENSE
-rw-r--r--  gamuser apache  GamCommands.txt
-rwxr-x---  gamuser apache  gam
-rwxr-xr-x  gamuser apache  oauth2.txt.lock
-rw-rw-rw-  gamuser apache  oauth2.txt
```

Once these settings are set, then Apache should be able to call the /home/gamuser/bin/gam application and provide the results.
## index.php
This is the main file.  It loads header, main, and footer files.
## main.php
This is a basic menu, it only has a link to the email.php file.  You can add entries here if you need to have more commands available.
## login.php
This is the only real protection I have in this example.  This is what controls access to the site.  It uses a username\password option for access.  I am not sure how secure this is, and there are most likely better ways to be more secure.  But as a proof of concept, it's what I went with.  Do not depend on this being too secure, and use something better on an exposed 24/7 website.
## email.php
This is a basic form entry page that allows you to enter an email address which will be passed to functions.php for resolution.
## functions.php
This is where GAM is called, and the results are retrieved, and shown to the user.  At this time, it checks the email address to determine if it is a user or group.  If it is a user, it returns the vacation responder as well as any delegates on the account.  If it is a group, it returns the managers, and members.


# TODO
add menu items for other GAM commands
    Change license type for user
    
add additional security measures
add logging
add error handling
add more options for output formatting
add ability to input / process csv files

