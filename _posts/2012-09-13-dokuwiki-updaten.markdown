---
layout: post
title: "Dokuwiki updaten"
date: 2012-09-13 22:45
comments: true
categories: [dokuwiki, howto, shortie]
---

Kleine Erinnerung für mich selbst um ein Dokuwiki zu updaten. (Lange Form [hier](https://www.dokuwiki.org/install:upgrade))

Download der aktuellen Version von [hier](http://www.splitbrain.org/projects/dokuwiki)
{% highlight bash %}
[christian@fuffy ~]$ cp -ar wiki backup #Erst mal ein Backup machen
[christian@fuffy ~]$ cd wiki
[christian@fuffy ~]$ cp -r ~/tmp/dokuwiki-*/* . #Überschreiben der alten Dateien/Neue hinzufügen
[christian@fuffy ~]$ grep -Ev '^($|#)' data/deleted.files | xargs -n 1 rm -f #Unnötige Dateien entfernen
{% endhighlight %}

Wenn nötig noch Templates und Plugins updaten. Das war es, nun ist alles Aktuell :-) (wenn was schief gegangen ist, kein Ding, wir haben Backup)
