---

title: "Mac Kennwort vergessen"
date: "2012-07-26"
tags: [kennwort, mac, passwort]
published: true

---

How to recreate an Admin Account on a MAC:

> hold CMD-S or WIN-S and power on the MAC.

now some manual editing:
```
fsck -y

mount -uaw /

rm /var/db/.AppleSetupDone

reboot
```

The System now thinks it is not even Set Up yet.
Now you will be creating a new User and go through the Setup process.
This user becomes an Administrator on the Mac after the setup.

Have fun.

After writing this i saw the <a href="http://instant-thinking.de/2008/02/14/mac-os-x-passwort-vergessen/">Article from Dennis</a>
