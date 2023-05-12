---

title: "Silverlight Videos on Linux"
published: true
date: "2014-02-21"
tags: ["silverlight","linux","monolight","pipelight"]

---

### Silverlight and linux are not friends.

This is the Tutorial from which i could watch movies for silverlight successfully on my Ubuntu Machine.
[Pipelight Installation](http://fds-team.de/cms/pipelight-installation.html)

So for Ubuntu you have to do some little things ...
For my personal recommends i added chromium to split the usage of a normal
browser and a dedicated one.

``` bash
 sudo add-apt-repository ppa:pipelight/stable
 sudo apt-get update
 sudo apt-get install --install-recommends pipelight-multi
 sudo pipelight-plugin --enable silverlight
 sudo apt-get install chromium-browser
```

go out there and
Happy Silverlighting...
