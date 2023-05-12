---

layout: post
title: "Serial and USB Action with wine"
published: true
date: 2014-06-29
tags: ["wine","linux"]

---

First of all you have to add your user to the dialout group which is used in
ubuntu for all serial or usb devices that can perform some kind of /dialouty/
activity. 

For the user to have access to that group it is better to logout and
login again to get the GUI to receive the new Groups.

In the next step you have to browse to your _wineprefix directory_
that in my case resides in $HOME/.PlayOnLinux/wineprefix/nTrip .


{% codeblock %}
sudo adduser $USER dialout          # adds your user to the dialout group
cd $HOME/.wine/                     # enter your directory here
ln -s /dev/ttyUSB0 dosdevices/com1  # /dev/ttyS0 for the first serial port
{% endcodeblock %}

Have Fun.
