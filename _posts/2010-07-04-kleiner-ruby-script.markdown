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

<div class="CodeRay">
  <div class="code">require <span class="s"><span class="dl">'</span><span class="k">rubygems</span><span class="dl">'</span></span>
require <span class="s"><span class="dl">'</span><span class="k">xmlsimple</span><span class="dl">'</span></span>

f = <span class="co">File</span>.open(<span class="co">ENV</span>[<span class="s"><span class="dl">'</span><span class="k">HOME</span><span class="dl">'</span></span>] + <span class="s"><span class="dl">&quot;</span><span class="k">/.purple/accounts.xml</span><span class="dl">&quot;</span></span>, <span class="s"><span class="dl">&quot;</span><span class="k">r</span><span class="dl">&quot;</span></span>)
data = <span class="co">XmlSimple</span>.xml_in(f.read())
f.close()

data[<span class="s"><span class="dl">'</span><span class="k">account</span><span class="dl">'</span></span>].each <span class="r">do</span> |item|
        print item[<span class="s"><span class="dl">'</span><span class="k">protocol</span><span class="dl">'</span></span>][<span class="i">0</span>].split(<span class="s"><span class="dl">'</span><span class="k">-</span><span class="dl">'</span></span>)[<span class="i">-1</span>] + <span class="s"><span class="dl">&quot;</span><span class="ch">n</span><span class="dl">&quot;</span></span>
        <span class="r">if</span> item[<span class="s"><span class="dl">'</span><span class="k">name</span><span class="dl">'</span></span>]
          print <span class="s"><span class="dl">&quot;</span><span class="ch">t</span><span class="k">Name: </span><span class="dl">&quot;</span></span> + <span class="s"><span class="dl">&quot;</span><span class="ch">t</span><span class="dl">&quot;</span></span> + item[<span class="s"><span class="dl">'</span><span class="k">name</span><span class="dl">'</span></span>][<span class="i">0</span>] + <span class="s"><span class="dl">&quot;</span><span class="ch">n</span><span class="dl">&quot;</span></span>
        <span class="r">end</span>
        <span class="r">if</span> item[<span class="s"><span class="dl">'</span><span class="k">password</span><span class="dl">'</span></span>]
          print <span class="s"><span class="dl">&quot;</span><span class="ch">t</span><span class="k">Pass: </span><span class="dl">&quot;</span></span> + <span class="s"><span class="dl">&quot;</span><span class="ch">t</span><span class="dl">&quot;</span></span> + item[<span class="s"><span class="dl">'</span><span class="k">password</span><span class="dl">'</span></span>][<span class="i">0</span>] + <span class="s"><span class="dl">&quot;</span><span class="ch">n</span><span class="dl">&quot;</span></span>
        <span class="r">end</span>
<span class="r">end</span></div>
</div>


<p>So, das ist der Skript, bitte nicht hauen ich lernen ja gerade erst.</p>

<p>Have fun</p>
