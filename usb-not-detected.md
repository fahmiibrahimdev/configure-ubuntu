# USB NOT DETECTED ON UBUNTU 22.04

> Sometimes during the initial install of ubuntu there will be problems, namely regarding the USB that is not detected. this is very useful for connecting the USB port to Arduino / Microcontroller, here I will provide a solution

The Solution is:
```
$ sudo apt remove brltty
$ sudo usermod -a -G dialout $USER
$ sudo reboot
```

Done, Successfully!
