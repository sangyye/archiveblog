---
layout: post
title: "cgit on uberspace"
date: 2012-04-02 10:31
comments: true
categories: [uberspace, git]
---

Update: Eine aktualisierte Anleitung gibt es in meinem [Wiki](http://wiki.sangyye.de/howto/cgit_on_uberspace)!

Hallo zusammen,
ich will in diesem kurzen HowTo eben die Installation des Git Webinterface [cgit](https://web.archive.org/web/20141226015418/http://hjemli.net/git/cgit/)(*Link geht zu archive.org, benutze das Update oben*) auf einem [uberspace](https://uberspace.de) erklären. Ich danke Jonas von uberspace für seine Hilfe als ich nicht mehr weiter kam :-)
<!-- more -->

Also zuerst muss ich sagen die Installation von cgit ist nicht ganz einfach, weil es das Kompilieren von Code und arbeiten auf der Shell verlangt. Daher sind minimale Kenntnisse schon nötig und jeder der sich das nicht zutraut sollte ehr Abstand von der Installation nehmen.

Der erste Schritt ist wir beschaffen uns den Quellcode von cgit und legen ein Verzeichnis an in dem wir dann weiterverarbeiten können.
{% highlight bash %}
mkdir -p ~/tmp && cd ~/tmp/
curl --silent http://hjemli.net/git/cgit/snapshot/cgit-0.9.0.3.tar.gz | tar -xzf -
cd cgit-0.9.0.3/
{% endhighlight %}

Im nächsten Schritt brauchen wir einmal den Editor nano oder vim, je nach dem wo die Vorlieben sind. Wir müssen nämlich die Makefile anpassen da cgit drauf ausgelegt ist unter root-Rechten Konfiguriert und Installiert zu werden. Da wir die bei uberspace nicht haben müssen wir die Makefile ändern mit `nano Makefile` z.B. rufen wir die auf und ändern die ab das sie so aussieht, wobei `%ubernaut` gegen deinen Username bei uberspace getauscht werden muss.
{% highlight bash %}
CGIT_VERSION = v0.9.0.3
CGIT_SCRIPT_NAME = cgit.cgi
CGIT_SCRIPT_PATH = /home/%ubernaut/cgi-bin
CGIT_DATA_PATH = $(CGIT_SCRIPT_PATH)
CGIT_CONFIG = /home/%ubernaut/etc/cgitrc
CACHE_ROOT = /home/%ubernaut/cache/cgit
prefix = /usr
libdir = $(prefix)/lib
...
{% endhighlight %}

Danach die Makefile speichern und schließen. Danach muss nur noch eine passende Version von git installiert werden, cgit kompiliert werden und an die richtigen Stellen kopiert werden, in diesem Fall `~/html/git/`

{% highlight bash %}
make get-git
make
{% endhighlight %}

Dadurch werden die benötigten Dateien erstellt, wir müssen sie nur noch an dir richtigen Orte Kopieren. Da Cgit leider etwas, naja sagen wir mal "kaputt" ist verlangt er für die css und die png immer den root Pfad, und ich habe noch keine Möglichkeit gefunden das zu unterbinden. Daher kopieren wir die css und die png ins root Verzeichnis wo sie hoffentlich nicht stören. Wenn jemand eine andere Lösung kennt, her damit. Dies ist bei einer eignen Subdomain nicht nötig, dazu später mehr.

{% highlight bash %}
cp cgit /home/$ubernaut/cgi-bin/cgit.cgi
chmod 755 /home/%ubernaut/cgi-bin/cgit.cgi
cp cgit.css /home/%ubernaut/html/
cp cgit.png /home/%ubernaut/html/
{% endhighlight %}

Jetzt fehlt nur noch die Grundconfig und die htaccess. Wir legen also eine mit z.B. `nano /home/%ubernaut/html/git/.htaccess` eine an und zwar mit diesem Inhalt.

{% highlight bash %}
RewriteEngine on
Options +ExecCGI

RewriteRule (.*) /cgi-bin/cgit.cgi/$1 [PT]
{% endhighlight %}

Dann brauchen wir noch eine einfach cgitrc zur Steuerung von cgit. Also wieder z.B. `nano /home/%ubernaut/etc/cgitrc` und dort mit diesem Inhalt

{% highlight bash %}
virtual-root=/git
enable-index-links=1
enable-log-filecount=1
enable-log-linecount=1
enable-commit-graph=1
snapshots=tar.gz tar.bz zip
{% endhighlight %}

So jetzt sollte unter eurer uberspace Adresse (z.B. http://%ubernaut.%server.uberspace.de/git) euer leeres cgit ohne jede Repos zu sehen sein. Wie ihr eigne Repos hinzufügt könnt ihr nun in der [manpage zu cgitrc](https://web.archive.org/web/20120630160800/http://hjemli.net/git/cgit/tree/cgitrc.5.txt)(*Link geht zu archive.org, benutze das Update oben*) nachlesen.

Cgit als subdomain
------------------
Wer seine eigne Domain auf uberspace aufgeschaltet hat und nun gerne ein git.domain.tld haben will muss eigentlich nur Folgendes anders machen.

{% highlight bash %}
cp cgit /home/%ubernaut/cgi-bin/cgit.cgi
chmod 755 /home/%ubernaut/cgi-bin/cgit.cgi
mkdir /var/www/virtual/$ubernaut/git.domain.tld
cp cgit.css /var/www/virtual/$ubernaut/git.domain.tld
cp cgit.png /var/www/virtual/$ubernaut/git.domain.tld
{% endhighlight %}

Dann nur noch eine htaccess mit folgendem Inhalt in dem git.domain.tld anlegen

{% highlight bash %}
RewriteEngine on
Options +ExecCGI

RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule (.*) /cgi-bin/cgit.cgi/$1 [PT]
{% endhighlight %}

Dann noch in der cgitrc das `virtual-root=/git` mit `virtual-root=/` und fertig ist git.domain.tld.
Viel Spass mit dem eignem Cgit!
