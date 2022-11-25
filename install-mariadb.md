# Prerequisites
 > Root access to your server or a sudo user.

## Step 1: Setup Initialization
Start by updating the packages to the latest version available using the following command.
```
  sudo apt update
  sudo apt upgrade
```
Once you have updated the setup you can start the setup.

## Step 2: Install MariaDB
By default Ubuntu 22.04 repositories have the MariaDB version 10.6 package. So you can install it directly
```
sudo apt install mariadb-server mariadb-client
```
Once the installation is completed, the MariaDB service will start automatically. To verify that the MariaDB server is running, type:
```
sudo service mariadb status
```
The output should show that the service is enabled and running:
```
● mariadb.service - MariaDB 10.6.7 database server
     Loaded: loaded (/lib/systemd/system/mariadb.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2022-05-12 16:49:10 UTC; 9h ago
       Docs: man:mariadbd(8)
             https://mariadb.com/kb/en/library/systemd/
   Main PID: 1632 (mariadbd)
     Status: "Taking your SQL requests now..."
      Tasks: 7 (limit: 1146)
     Memory: 261.7M
        CPU: 1min 41.373s
     CGroup: /system.slice/mariadb.service
             └─1632 /usr/sbin/mariadbd
```
Done, Successfully!
