---

title: "Music your home with linux"
published: true
date: 2014-08-20
comments: true
tags: ["linux","windows","mpd","music"]

---

Musik zuhause. Das ist eigentlich das was man immer gern hat, aber sich nie
Gedanken zu macht. Und die wichtigste Frage: Wie kann Linux dabei helfen?
Im folgenden werde ich versuchen eine Übersicht über meine Erfahrung mit diesen
beiden Themen zu geben.

<!-- more -->

#### Die Idee

Ich hatte die Idee Musik nicht nur im Wohnzimmer sondern auch gleichzeitig 
im Garten abzuspielen. Gleichzeitig ist hierbei technisch übersetzt natürlich
das Wort Synchron. Man möchte nicht einen Beat verpassen beim Wechseln von 
Garten ins Wohnzimmer


##### Wiedergabe

Eine Wiedergabe soll von vielen Orten aus möglich sein. In erster Linie jedoch
von iOS und eventuell iTunes sowie im Nachgang von Linux und Windows.


With that criterias not many players are out there. The player of choice is mpd.
The Music Player Deamon is a tiny little program that runs on top of sort of all
OS's and can be controled by many clients.
mpd can put out a the sound direct onto a soundcard, http stream with internal
http server or onto another mp3 stream serving facility like icecast.

##### Transport Protocol

To get the Music out in the wild i would like to get multicasting for
synchronous play or some sort of that.
In case of http output stream i would have to get the stream out with another
program like VLC to create a multicast stream for the network.

#### Mediums

##### WLAN is not good for Audio abuse.

For me i have not a network cable in the garden and have to stick with wlan for
that purpose. So the Tests with this _over the air medium_ not as expected.
The lag was extraordinary big from lan to wlan so that you listened to the
refrain inside and when you got out it played again. That was so annoying that
i cut the multicast idea from here on.

##### LAN

LAN is fast, stable and the way to go with if you have cable connection.

#### The Future

    * metadatarized Database
    * multicast over the air without much lag

#### Configs

For i can not say what your preferenced settings are here are some of mine:

``` bash
"/etc/mpd.conf"
```

# Options
``` bash
restore_paused "yes"
auto_update "yes"

# Permissions
password            "password@read,add,control,admin"
default_permissions "read,add,control"

# Input
# for opening http streams
input {
   plugin "curl"
   #proxy "proxy.isp.com:8000"
   #proxy_user "user"
   #proxy_password "password"
   }

# Audio Output
audio_output {
   type "alsa"
   name "My Alsa Mixer"
   }
audio_output {
   type "httpd"
   name "My httpd Output"
   encoder "lame"
   port    "8000"
   bitrate "256"
   format  "44100:16:2"
   max_clients  "3"
   }
```

### Install

#### Ubuntu

    sudo apt install mpd

