--- 
layout: post
title: "Wunderlist unter Archlinux"
date: 2011-9-20
comments: true
categories: 
- archlinux
- Linux
- wunderlist
---
Hey zusammen,

es gibt nun <a title="Wunderlist für Linux" href="http://www.6wunderkinder.com/blog/2011/09/20/two-new-members-join-the-family-assistly-and-wunderlist-for-linux/" target="_blank">Wunderlist für Linux</a>. Ich wollte das Teil direkt mal testen, aber unter Archlinux tat sich da nix. Supi, also ich das Ding mal in der Konsole gestartet und gesehen woran es liegt. Wenn es also laufen sollt müsst ihr in den wunderlist Ordner wechseln. Ein
{% highlight bash %}
cd runtime/1.2.0.RC3
{% endhighlight %}
dann müssen mit <em>ln -s</em> die entsprechenden libs verknüpft werden.
{% highlight bash %}
ln -s /usr/lib/libgnutls.so.28.1.0 libgnutls.so.26
rm  gio/libgiognutls.so
ln -s /usr/lib/gio/modules/libgiognutls.so gio/libgiognutls.so
ln -s /usr/lib/libnotify.so libnotify.so.1
{% endhighlight %}
Danach nur noch die Wunderlist datei im hauptordner ausführen und es läuft. Viel Spass.
