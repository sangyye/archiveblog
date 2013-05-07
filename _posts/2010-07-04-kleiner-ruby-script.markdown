--- 
layout: post
title: Kleiner Ruby-Script
date: 2010-7-4
comments: true
categories: 
- ruby
- script
- Uncategorized
---
<p>Ich wollte mal ruby testen, da ich die Sprache ja ganz nett finde.
Und jetzt habe ich einen kleinen skript geschrieben der mir meine
Accounts mit passwörter aus pidgin ausliest. Habe ich gerade einfach
gebraucht und ich hasse es xml lesen zu müssen :-D</p>

{% highlight ruby %}
require 'rubygems'
require 'xmlsimple'

f = File.open(ENV['HOME'] + "/.purple/accounts.xml", "r")
data = XmlSimple.xml_in(f.read())
f.close()

data['account'].each do|item|
	print item['protocol'][0].split('-')[-1] + "/n"
	if item['name']
        	print "/tName: " + "/t" + item['name'][0] + "/n"
        end
        if item['password']
        	print "/tPass: " + "/t" + item['password'][0] + "/n"
	end
end
{% endhighlight %}

<p>So, das ist der Skript, bitte nicht hauen ich lernen ja gerade erst.</p>

<p>Have fun</p>
