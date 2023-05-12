---

layout: post
title: "Cannonball (the OutRun Engine)"
date: "2014-02-07"
published: true
tags:       [linux, windows, games]

---

How to install cannonball the outrun engine on your own PC for the ultimate
Retro Experience on Ubuntu/Debian Derivates. With Windows the Process is defined on the [github page](https://github.com/djyt/cannonball.git).

{% highlight bash %}
DIRRECTORY=~/git
mkdir $DIRRECTORY
git clone https://github.com/djyt/cannonball.git $DIRRECTORY/cannonball
cd $DIRRECTORY/cannonball
# could not get it to target debian
cp cmake/debian.cmake cmake/default.cmake
mkdir build
cd build
sudo apt-get install cmake libsdl1.2-dev libboost1.53-dev -yy
cmake ../cmake
make
ln -s ../roms roms
# now put your "OutRun Rev.B romset in the roms dir.
# and off you go by

./cannonball

{% endhighlight %}


Navigate to the options menu with the Arrow keys and "1" as "Enter".
Edit your keys to your behaviours.
And Blast off to one of the coolest Gaming Machine Games
of the last Century.
