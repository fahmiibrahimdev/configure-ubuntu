Remove Apache2 :

1. sudo service apache2 stop
2. sudo apt-get purge apache2 apache2-utils apache2-bin apache2.2-common
3. sudo apt-get autoremove

You can do the following two tests to confirm apache has been removed:
1. which apache2 - should return a blank line
2. sudo service apache2 start  - should return apache2: unrecognized service
