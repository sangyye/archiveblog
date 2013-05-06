---
layout: post
title: "Gedanken zum mobilen Bloggen"
date: 2012-06-03 15:54
comments: true
categories: [bloggen, s9y]
---
Hi zusammen,   
heute mache ich mir mal Gedanken zum Thema mobilen Bloggen. Ja, mobilen Bloggen.
Wie die meisten sicher gemerkt haben benutze ich [octopress](http://octopress.org).
Dadurch brauche ich eine installierte Version von ruby, rsync, git und ssh. Idealerweise
sogar einen Editor der Markdown unterstützt. Das ist natürlich nur für einen normalen Computer zu stemmen.
(Also ich meine einen Linux Computer, ich habe mein Setup noch nicht unter Windows getestet.) Bedingt
dadurch fällt es mir schwer "mal eben" unterwegs was zu bloggen was mehr als 140 Twitter Zeichen hat.

Was ist nun "mobiles Bloggen"?
------------------------------
Eigentlich ist das schnell und einfach erklärt, man wirft sein Handy an, macht ein Foto, und wirft das auf
seinen Blog. Es gibt verschiedene Anbieter im Internet, z.B. [Twitter](http://twitter.com). Ja auch 140 Zeichen sind eine Art
Bloggen auch wenn man sich kurz fasst, meist reichen 140. Leider nicht immer ;-) Ich labere halt zu gerne
und daher brauche ich auch unterwegs was mehr. Da bieten sich Anbieter wie [tumblr](http://tumblr.com) und [posterous](http://posterous.com)
an, um mal Zwei zu nennen die ich ausgiebig genutzt habe oder immer noch nutze.   
So die Idee ist das man ein App hat oder wie posterous am Anfang eine Mail Adresse in die man seine geistigen Ergüsse
die man unterwegs so hat rein werfen kann und die zimmern das zu einem Blog zusammen. Tumbr hat das sehr einfach gemacht.
Hirn auf, eben tippen, Blogeintrag raus. Mit einer großen Communtiy dadurch die Möglichkeit Inhalte andere auf seinen Blog anzuzeigen.
Das spielt hier aber keine Rolle. Worum es geht das tumblr sich als Twitter mit mehr als 140 Zeichen sieht und daher sich eben so simple
gibt wie Twitter.   
Auf der anderen Seite gab es posterous. Lange mein absoluter Liebling, zeitweise sogar mein einziger Blog. Wieso? Es war mehr als simple.
Mail rein, Blogeintrag raus. Dieses einfache Rezept hat es jedem ermöglicht von überall her einfach und effektiv zu bloggen.
Das war aber nicht der Hauptgrund warum ich es geliebt habe. Der wahre Grund war sein Verteilungs-Feature.   
Stellt euch das so vor, ihr schreibt einen Artikel und das was ihr Schreibt landet in allen Medien die ihr Vorher definiert habt. Cool oder?
Bei posterous war das möglich, ich trug meinen wordpress, meinen Twitter, mein Facebook und alles was ich sonst so hatte ein. Ein paar Regeln definiert wann was wo landet.
Und dann ging es los. Ich hämmere was in meinen Blog und posterous macht den nervigen Rest alle Medien darüber zu Informieren macht mein kleiner, dienstbereiter "Daemon" posterous.
Das ging auch lange zeit sehr gut. Bis posterous anfing irgendwelche Community-Features wie "Spaces" und Co. drüber bügeln wollte. Und dann wurde es von Twitter gekauft.

Okok, ich höre dir ja gerne zu, aber was soll das?
--------------------------------------------------
Wie gesagt ich labere gerne, worüber ich mir Gedanken gemacht habe ist, wieso kann ich das nicht selber Hosten? Was ich gerne will ist ein System dem ich
sagen kann, lies diesen rss-feed, twitter-stream, diese Mail oder was auch immer ein. Also ich hämmre was mit einem App oder welchen Weg auch immer rein.
Und das System packt sich die Daten, und hämmert die als Verteiler in einen wordpress, Twitter, youtube und facebook rein.
Die Idee ist also einen selber gehosteten Mittelsmann alla posterous. Das ist so ein kleiner Traum von mir :-) Kontrolle über die eignen Daten zurück zu bekommen
ist mein Antrieb. Mir gefällt nicht das ich meine Blogposts irgendwo rein haue und sie nachher nicht mehr raus bekomme wenn ich sie wieder haben will. So was nervt.
Deswegen muss die Grundlage frei sein, und so kam für mich [serendipity](http://s9y.org) ins Spiel.

Also s9y wurde gewählt weil ich glaube das wordpress zu komplex und mir persönlich zu "fett" ist. Das ist
natürlich nur meine persönliche Meinung und nicht irgendwie eine wissenschaftliche Meinung. Dadurch und weil ich die Communtiy von s9y sehr cool finde,
wurde es s9y. So, wir haben also unsere Grundlage und wie weiter. Ich kann kein PHP ( was sich ja noch ändern kann) und ich kenne s9y noch nicht intern (was ich gerade ändere), aber
ich habe etwas Kontakt zur Community bekommen und wollte mal gucken wie denen meine Ideen so gefallen. Wenn sich das ergibt kann mir sicher einen s9y und php erklären und wir rocken da
eine posterous Möglichkeit mit s9y raus.

Meine ersten Ziele sind eine einfache Import Möglichkeit von posterous zu s9y (wenn es was gibt dann muss das in die Standard Installation von s9y). Meiner Meinung nach ist die Möglichkeit
s9y als Ersatz für posterous zu nutzen genau die Lücke die s9y besetzten kann und dadurch vielleicht sogar wordpress irgendwann mal Konkurrenz machen kann.

So das waren mal so ein paar Gedanken von mir, mal sehen was sich da so tut :)
