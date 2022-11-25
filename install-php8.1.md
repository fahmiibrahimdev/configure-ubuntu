# Prerequisites

To complete this tutorial, you will need a local or virtual machine with Ubuntu 22.04 installed and have administrative access and an internet connection to that machine.

## Step 1: Update System Dependencies

First we are going to update system dependencies. Run the following command at a command prompt to update the latest packages or dependencies.
```
sudo apt update
sudo apt upgrade
```

## Step 2: Add PHP PPA

Now in this step we are adding PHP PPA. Using following command to install PHP 8.1.
```
sudo apt install software-properties-common
sudo add-apt-repository ppa:ondrej/php
sudo apt update
```

## Step 3: Install PHP 8.x for Apache

Step three is to install PHP 8.x for apache. Execute the following command on command prompt to install PHP 8.1.
```
sudo apt install php8.1
```
To confirm the installation using the following command.
```
php -v
```

## Step 4: Install PHP 8.x Extensions

Now we are going to install PHP 8.x extensions. Using the following command, we can install PHP extensions.
```
sudo apt install php8.1-extension_name
```

Now, install some commonly used php-extensions with the following command.
```
sudo apt install php8.1-common php8.1-mysql php8.1-xml php8.1-xmlrpc php8.1-curl php8.1-gd php8.1-imagick php8.1-cli php8.1-dev php8.1-imap php8.1-mbstring php8.1-opcache php8.1-soap php8.1-zip php8.1-redis php8.1-intl -y
```

## Step 5: Verify PHP Version

Now we are going to verify php version. Using the following command, we can easily verify PHP version.
```
php -v
```

Output:
```
PHP 8.1.5 (cli) (built: JULY 28 2022 10:32:13) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.1.5, Copyright (c) Zend Technologies
    with Zend OPcache v8.1.5, Copyright (c), by Zend Technologies
```

Done, Successfully!
