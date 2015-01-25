--- 
layout: post
title: Ingate und das Gentoo Image
date: "2010-12-13"
comments: true
categories: 
- gentoo
- ingate
- Server
- vserver
---
So,
ich habe heute mal meinen vserver von <a title="Ingate" href="http://www.ingate.de/" target="_blank">Ingate</a> neu aufgesetzt. Dauerte ein paar Minuten dann stand dort Server gestartet und ich wollte mich via SSH einloggen. Ging nicht. Moment, das kam mir bekannt vor. Mein Kollege <a title="Christophs Eintrag" href="http://subforge.org/blogs/show/12" target="_blank">Christoph</a> hatte das Problem, vor knapp 6 Monaten. Und nun hatte ich das selbe Problem, war kein Ding das zu lösen. Server aus, ftp modus an, eingeloggt, sshd_config gesucht und die Zeile "<span style="font-size: 15px; color: #222222; font-family: 'Courier 10 Pitch', Courier, monospace; line-height: 21px; white-space: pre;">ListenAddress </span>0.0.0.0" hinzugefügt, ftp aus und server gestartet. Siehe da es ging.

Ich habe nun eine Email mit dem Fehler an Ingate angeschickt, mal sehen was die sagen. Aber das sowas 6 Monate nicht repariert wird ist schon sehr blöd.

Christian
