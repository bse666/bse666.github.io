---

layout: post
title: "Deleting ZFS Snapshots"
published: true
date: 2014-08-14
comments: true
tags: ["zfs","linux","freebsd"]

---

If you are in the situation to deal with many zfs snapshots that are not needed
anymore you can try this. !!! USE AT YOUR OWN RISK !!!

``` bash Deletes all Snapshots found!!! (thanks to SysadminBlog) http://sysadminman.net/blog/2008/remove-all-zfs-snapshots-50
#!/bin/bash
for snapshot in `zfs list -H -t snapshot | cut -f 1` #add grep's here to limit
                                                     #the amount of deletes
do
zfs destroy $snapshot
done
```

``` bash List all snapshots
zfs list -H -t snapshot
```
