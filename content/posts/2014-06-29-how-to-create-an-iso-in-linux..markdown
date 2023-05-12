---

layout: post
title: "How to create an ISO in linux."
published: true
date: 2014-06-29
tags: ["linux"]

---

#### fastest way:

Open a Terminal and type in:
``` bash
cat /dev/sr0 > $HOME/test.iso
```
#### Or with _dd_
``` bash
isoinfo -d -i /dev/sr0 |grep -i -E 'block size|volume size'
dd if=/dev/sr0 of=$HOME/test.iso bs=<blocksize> count=<volumesize>
```
#### Test your Image against the CD/DVD
``` bash
cmp $HOME/test.iso /dev/sr0
```
