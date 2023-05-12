---

layout: post
title: "New Blog in da House"
date: "2014-02-06"
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
Jekyll could be less vurnable to attacks because of it's relatively static
generated sites. This could be a huge plus in the next time.

The second best plus for Jekyll is that you can take your blog and information
with you and you are able to write and show all posts offline until a little
internet is available for you.

#### Altdaten
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


[nodejs]: http://nodejs.org
[CoolAJ86]: http://blog.coolaj86.com/articles/migrate-from-blogger-to-ruhoh-with-proper-redirects.html
[blogger]: http://blogger.com/home
