# Linux_Project_IaC_Script_2

Script to Provide an Apache Web Server

(You can have an additional step to restaure the snapshot so que machine will go back to its initial state without any of those software installed - Before it, do: `shutdown 0`); After restaure the initial state, restart the machine. Login as root and check the ip `ip -a`. 

- Preparing

```

cd /
mkdir scripts2
cd /scripts2/
nano script-iac-webserver.sh

//the sh file should start with: `#!/bin/bash`

```

- 1 Update/upgrade the server 

````
apt-get update
apt-get upgrade -y
````

- 2 Install apache2

````
apt-get install apache2 -y

````

- 3 Install unzip

````
apt-get install unzip -y

//or to install both
apt-get install apache2 unzip -y

````


- 4 Download the app (files with the site) from GitHub and insert it in `/tmp` directory


````
cd /tmp
wget https://github.com/denilsonbonatti/linux-site-dio/archive/refs/heads/main.zip
unzip main.zip

````

- 5 Copy the app files into the default apache directory

````
cd linux-site-dio-main
cp -R * /var/www/html/

````

Crt+0 + Ctrl+x -> to save script

To grant permission to execute the file:

````
ls -l
chmod +x script-iac-webserver.sh
ls l-

````

Create a snapshot at this state to go back here case something went wrong when run the script.

To execute the script

````
./script-iac-webserver.sh
````

To check the files

````
cd /var/www/html/
````

Type the ip on the browser to check the site on your computer


- 6 Upload the script file into the GitHub repository

Create new github repository

On the server:
cd /script2/
git init -> git add . -> git commit -m "apache version 1.0" -> git branch -M main -> git remote add origin https://....git -> git push -u origin main


