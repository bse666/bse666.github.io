---

layout: post
title: "How to enable sshd on Android"
date: 2014-04-28
published: true
tags: ["linux","android"]

---

If you love android as much as me for it's customizing capabilities you will
love this tutorial. I try to do much on the commandline and use as many
automation as possible for this purpose. 
I got the Code references from the [CM Wiki](http://wiki.cyanogenmod.org/w/Doc:_sshd).
So here it is, my sshd on Android Tutorial.
<!-- more -->

## Why use this long tutorial when there is an app for it?

Because there is an APP for it. One more APP you have to install for things that
are already on your phone.


## Step 1

Install a custom ROM like Cyanogenmod or PAC-ROM. Here are many possibilities to
customize your android experience.
You have to unlock the developer options which will void your warranty in some
countries.

## Here you are.

Assuming that you are already installed and ready. (Android tools for your
distribution and such), there are a few things to do on your phone.
Plug your phone into your computer and follow the next steps.

## Developer Options
To unlock do the following:

* go to settings -> about device and tap 7 times continously on build number.
* enable USB Debugging in settings -> developer options
* also enable root for adb

## Enter the shell
fire up your favourite terminal emulator and hack this into it.
### connect to your phone
adb shell
su

### create the directory structure
mkdir -p /data/ssh/empty
chmod 700 /data/ssh
chmod 700 /data/ssh/empty

### create the host keys
ssh-keygen -t dsa -f /data/ssh/ssh_host_dsa_key -N ""
chmod 600 /data/ssh/ssh_host_dsa_key
ssh-keygen -t rsa -f /data/ssh/ssh_host_rsa_key -N ""
chmod 600 /data/ssh/ssh_host_rsa_key

### configure your sshd server
cat /system/etc/ssh/sshd_config | \
sed 's/#PermitRootLogin yes$/PermitRootLogin yes/' | \
sed 's/#PubkeyAuthentication yes/PubkeyAuthentication yes/' | \
sed 's/#PasswordAuthentication yes/PasswordAuthentication no/' | \
sed 's/#PermitEmptyPasswords no/PermitEmptyPasswords no/' | \
sed 's/#ChallengeResponseAuthentication
yes/ChallengeResponseAuthentication no/' | \
sed 's;/usr/libexec/sftp-server;internal-sftp;' > \
/data/ssh/sshd_config
chmod 600 /data/ssh/sshd_config

### create your private key
mkdir -p /data/.ssh
chmod 700 /data/.ssh
ssh-keygen -t rsa -f /data/.ssh/id_rsa
chmod 600 /data/.ssh/id_rsa
cat /data/.ssh/id_rsa.pub > /data/.ssh/authorized_keys
chmod 600 /data/.ssh/authorized_keys
```


## Fire it up
With the following command you are able to start and stop the server. How you
inject them into your android system is up to you, but i recommend something
like Tasker to enable or disable the Server in trusted environments.

```
/system/bin/sshd -f /data/ssh/sshd_config
```

```
killall sshd
```

Both of these lines have to run as root.

And here you are with your own made ssh Server with only just yourself. Beside
that you also have learned how to enter your phone over usb cable and gain root.
