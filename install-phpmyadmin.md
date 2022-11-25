# Prerequisites

In order to complete this guide, you will need:
- A server running Ubuntu 20.04.
- Install PHP 8.1
- Install NGINX

## Step 1 — Installing phpMyAdmin
You can install phpMyAdmin by using APT to download the phpmyadmin package from the default Ubuntu repositories.

Begin by updating the server’s package index:
```
sudo apt update
```
Now you can install phpMyAdmin by running the following command:
```
sudo apt install phpmyadmin
```

During the installation process, you will be prompted to choose a web server (either Apache or Lighttpd) to configure. phpMyAdmin can automatically make a number of configuration changes to ensure that it works correctly with either of these web servers upon installation. However, because you are using Nginx as a web server you shouldn’t choose either of these options. Instead, press TAB to highlight the <Ok> and then press ENTER to continue the installation process.

Next, you’ll be prompted whether to use dbconfig-common for configuring the application database. Select <Yes>. This will set up the internal database and administrative user for phpMyAdmin. You will be asked to define a new password for the phpmyadmin MySQL user, but because this isn’t a password you need to remember you can leave it blank and let phpMyAdmin randomly create a password.

```
sudo ln -s /usr/share/phpmyadmin /var/www/your_domain/phpmyadmin
```
Your phpMyAdmin installation is now operational. To access the interface, go to your server’s domain name or public IP address followed by /phpmyadmin in your web browser:
```
https://server_domain_or_IP/phpmyadmin
```
  
## Step 2 — Changing phpMyAdmin’s Default Location
One way to protect your phpMyAdmin installation is by making it harder to find. Bots will scan for common paths, like /phpmyadmin, /pma, /admin, /mysql, and other similar names. Changing the interface’s URL from /phpmyadmin to something non-standard will make it much harder for automated scripts to find your phpMyAdmin installation and attempt brute-force attacks.

In the previous step, you created a symbolic link in your Nginx web document root pointing to /usr/share/phpmyadmin, where the actual phpMyAdmin application files are located. You can rename this symbolic link to change phpMyAdmin’s interface URL.

To do this, navigate to the Nginx document root directory:
```
cd /var/www/your_domain/
```
Then run the following ls command to list the files in the document root directory to get a better sense of the change you’ll make. This command includes the -l option, which tells the command to use the “long listing” format. This will instruct ls to return more information than it would otherwise:
```
ls -l
```
Your output will contain a line like the following:
```
Output
. . .
lrwxrwxrwx 1 root  root   22 Jan 15 21:09 phpmyadmin -> /usr/share/phpmyadmin/
. . .
```
This line indicates that you have a symbolic link named phpmyadmin in this directory. You can change this link name to whatever you’d like, and doing so will in turn change the URL where you can access phpMyAdmin. This will help to obscure the endpoint from bots performing automated searches of common endpoint names.

Choose a name that hides the purpose of the endpoint. This guide will name the endpoint /hiddenlink and use this name in examples throughout, but you should choose an alternate name.

Rename the symbolic link with the mv command:
```
sudo mv phpmyadmin hiddenlink
```
After running this command, run the ls -l command again to confirm that the symbolic link was renamed correctly:
```
ls -l
```
This time, the output will indicate that the listing for the symbolic link has been updated with its new name:
```
Output
total 8
. . .
lrwxrwxrwx 1 root  root   22 Jan 15 21:09 hiddenlink -> /usr/share/phpmyadmin/
. . .
```
Now when you go to the URL you previously used to access phpMyAdmin, you’ll get a 404 error:
```
https://server_domain_or_IP/phpmyadmin
```
![image](https://assets.digitalocean.com/articles/phpmyadmin_lemp_2004/nginx_1.18_404.png)
  
You can instead access your phpMyAdmin interface at the new URL you just configured:
```
https://server_domain_or_IP/hiddenlink
```
![image](https://assets.digitalocean.com/articles/phpmyadmin_lemp_1404/login.png)
  
## Step 3 — Configure Server
Go
```
sudo nano /etc/nginx/sites-available/default
```
and edit code to:
```
server {
  listen ..;
  ...;
  
  root /var/www/html;
  
  index index.html index.htm index.php;
  
  server_name _;
  
  location / {
    try_files $uri $uri/ =404;
  }
  
  location ~ \.php$ {
    include snippets/fastcgi-php.conf;
    fastcgi_pass unix:/var/run/php/php8.1-fpm.sock;
  }
}
```
  
Exit, and save configuration!. Done Successfully!
