---
layout: post
title: "Ein bisschen Ruby - Atom2RSS"
date: 2012-06-12 14:52
comments: true
categories: [ruby, sinatra]
---
Hi,    
also ich hatte aktuell das Problem das mein Blog mit octopress nur einen Atom-feed
erstellt. Was nicht weiter schlimm wäre wenn ich nicht ein Tool hätte was leider nur einen
RSS-feed verarbeiten könnte. Statt einen externen Dienst zu benutzen und weil ich wissen wollte
wie komplex das so ist, habe ich das mal eben selbst gemacht.

{% highlight ruby %}
require 'sinatra'
require 'simple-rss'
require 'builder'
require 'open-uri'

get '/*' do
  rss = SimpleRSS.parse open('http://' + params[:splat][0].to_s)
  builder do |xml|
    xml.instruct! :xml, :version => '1.0'
    xml.rss :version => "2.0" do
      xml.channel do
        xml.title rss.channel.title
        #xml.description 
        xml.link rss.channel.link

        rss.channel.entries.each do |post|
          xml.item do
            xml.title post.title
            xml.link post.link
            xml.description post.content
            xml.pubDate Time.parse(post.updated.to_s).rfc822()
            xml.guid post.link
          end
        end
      end
    end
  end
end
{% endhighlight %}

Wie sich raus stellte war es wirklich nicht schwer. Eine halbe Stunde später war das Ding fertig. Gut hier und da fehlen noch Dinge. Sicherheitsteile und Co. Aber es funktioniert soweit und ist ein eigener Webdienst, dank [sinatra](http://www.sinatrarb.com). Man gibt die URL in der Form `atom2rss.de/blog.sangyye.de/atom.xml` und bekommt seinen RSS-feed. atom2rss.de ist in dem Fall nur ein Beispiel auf welchem der Dienst laufen kann ;)
