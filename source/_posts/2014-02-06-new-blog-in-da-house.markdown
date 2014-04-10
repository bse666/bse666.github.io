---
layout: post
title: "New Blog in da House"
published: true
tags: [linux, jekyll, blog, github]
---

Welcome here in my little Blogging experience.
Since the last try's to blog more in the future failed i stumbled 
upon [github-pages](http://github.io).
Here you got

For a long time i *wanted to* get some cheat-sheets and tutorials up that i would
not always have to look up in the web for little things like bash programming
etc. 
Through the design of static pages and the ability to take your blog everywhere
you go i couldn't resist to take a tour in the all new jekyll.
And here we are.


### Plugins i use:
* [tags-in-jekyll](http://charliepark.org/tags-in-jekyll/)

### Why Jekyll when blogger.com is also not charging anything?

Hier kann ich den Tip geben mit der Ubuntu Variante:

* Exportieren des Contents von Blogger
 * [blogger] -> Blog auswählen.
 * Einstellungen -> Sonstiges
 * Blog-Extras -> Blog exportieren
 * blog-(datum).xml speichern
* Ab auf die Console.
* Installation von [nodejs]
{% highlight ruby %}
sudo npm install -g blogger2jekyll
# Konvertieren von altdaten in jekyll format
blogger2jekyll blog-(datum).xml meineAltenBlogPosts
{% endhighlight %}

Nun hat man in seinem Verzeichnis meineAltenBlogPosts alle Posts inklusive der Kommentare.

TODO: Die Bilder werden nicht mit exportiert. (wget?)


[nodejs]: http://nodejs.org
[CoolAJ86]: http://blog.coolaj86.com/articles/migrate-from-blogger-to-ruhoh-with-proper-redirects.html
[blogger]: http://blogger.com/home
