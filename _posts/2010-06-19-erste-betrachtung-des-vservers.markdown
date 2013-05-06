--- 
layout: post
title: Erste Betrachtung des vServers
date: 2010-6-19
comments: true
categories: 
- ingate
- Uncategorized
- vserver
---
<p>Hallo zusammen,<br />also ich habe den vServer schon ein paar Tage und wollte da jetzt mal das ein oder andere zu sagen.<br />Mein vServer entspricht dem Basic-Paket von ingate für 4€ im Monate. Dies Umfasst Folgendes:</p>
<ul>
<li>5GB Speicher im RAID1 (obwohl ich nicht sicher bin was die mit RAID1 meinen)</li>
<li>200MB Ram garantiert</li>
<li>200MB Swap</li>
<li>Traffic Flatrate (In der Webverwaltung werden nur 500GB angezeigt)</li>
<li>Voller SSH-Zugriff</li>
<li>und eine IP-Addresse</li>
</ul>
<p>Als erstes habe ich mir das Webinterface angeschaut. Ist ziemlich nett das Teil. Man kann dort den Server neustarten, runterfahren und auch neuinstallieren. Sie haben eine nette Auswahl an Images, worunter auch das sehr alte Sarge ist. Naja, muss mal einer aufräumen. Mit dem Gentoo-Image gibt es ein kleines ssh-Problem, wie ein Kollege von mir <a href="http://subforge.org/blogs/show/12">hier</a> schreibt (Warnung, Englisch-Alarm).<br /> Ich bin beim Debian Lenny Image geblieben. Und habe erstmal folgende Software installiert:</p>
<ul>
<li>lighttpd</li>
<li>mysql</li>
<li>postfix</li>
<li>php</li>
<li>vsftpd</li>
<li>mercurial (die version aus den backports)</li>
<li>phpmyadmin</li>
<li>und noch ein paar Kleinigkeiten</li>
</ul>
<p>Bisher muss ich sagen läuft das System rund, bisher bin ich nicht wirklich in Speicher- oder Platz-Probleme gekommen. Ich würde sagen für 4€ bekommt man ein relative einfaches System das für kleine Server-Belangen sicher vollkommende ausreichend ist. Das einzige was ich nicht so gelungen finde ist die 1 Jahr Vertragslaufzeit darüber sollte ingate nochmal nachdenken.<br /> Also ich bin bisher ziemlich zufrieden mit dem Angebot, habe aber meine Tests noch nicht abgeschlossen.<br />Als nächstes steht die Installation eines VPN-Servers und einer Monitoring-Software, mal sehen wie sich das System danach verhält.<p /> Bis dahin,<br />Christian</p>
