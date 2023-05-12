---

layout: post
title: "Android and Ubuntu"
published: true
date: 2014-06-12
comments: true
tags: ["android","linux"]

---
#### The easiest way to flash your Smartphone:

##### First install the android tools

``` bash
sudo apt-get install android-tools-adb android-tools-fastboot
```

##### reboot your phone into recovery

For my nexus 4 it is holding down the powerbutton and the volume down key since
the recovery appears.

##### plug the phone into your computer and sideload your android image

adb sideload cm-11-\*.zip
adb sideload gapps-\*.zip

##### have fun! :)
