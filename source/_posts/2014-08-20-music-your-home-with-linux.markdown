---
layout: post
title: "Music your home with linux"
published: true
date: 2014-08-20 18:49
comments: true
tags: linux,windows,mpd,music
categories: linux,windows,music
---

What can you do to bring Music to your home and how can Linux help you with
that?
In the following i will try to give you an overview from my experience point.

### The Idea
I had the idea to have the same music playing in the living room as out in the
garden and to be as perfect as it can to have it synchronized playing so that
you can walk out and hear the music as it plays inside.

##### Database
Database is with many format's and not synchronized with anything like iTunes or
other Media Organizers.

##### Player
The player has to be controllable from many System's i use Linux, Windows
and Android.
With that criterias not many players are out there. The player of choice is mpd.
<!-- more -->
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

### The Future
    * metadatarized Database
    * multicast over the air without much lag

### Configs
For i can not say what your preferenced settings are here are some of mine:

{% codeblock lang:bash "/etc/mpd.conf" %}
# Options
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
{% endcodeblock %}

### Install
#### Ubuntu
    sudo apt install mpd

