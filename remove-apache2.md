# Remove Apache2 :

Follow these steps to remove the apache2 service using Terminal:

1. First stop the apache2 service if it is running with: `sudo service apache2 stop`
2. Now remove and cleanup all the apache2 packages with:
```
  sudo apt-get purge apache2 apache2-utils apache2.2-bin apache2-common
  // or 
  sudo apt-get purge apache2 apache2-utils apache2-bin apache2.2-common
```
3. Finally, run `sudo apt-get autoremove` just in case any other cleanup in needed

You can do the following two tests to confirm apache has been removed:
1. `which apache2` - should return a blank line
2. `sudo service apache2 start` - should return apache2: unrecognized service

Done, Successfully!
