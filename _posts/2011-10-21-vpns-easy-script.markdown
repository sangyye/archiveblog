---
layout: post
title: "VPNs Easy Script"
date: 2011-10-21 17:06
comments: true
categories: [openvpn, skript, cli]
---
Hey zusammen,

auf meinem Server habe ich nun mal ein VPN laufen. Und weil ich den Aufruf von VPN auf der Konsole immer doof fand, habe ich mir einen kleinen alias geschrieben. Das war mir aber zu doof. Muss doch irgendwie cooler gehen und mehrere VPNs verwalten können, am besten auf der Konsole. Gibts nicht? Nun, jetzt schon!

Ich präsentiere meinen kleinen VPN Skript:

{% highlight bash %}
#!/bin/bash

confdir='/home/abakus/.openvpn'

function start_vpn()
{
	if [ ! -e /var/run/openvpn.pid ] ; then
		openvpn --daemon --writepid /var/run/openvpn.pid --cd $2/$1 --script-security 2 --config $2/$1/*.conf
	else
		return 1
	fi
}
function stop_vpn()
{
	if [ -e /var/run/openvpn.pid ] ; then
		kill -SIGTERM `cat /var/run/openvpn.pid`
		rm -f /var/run/openvpn.pid
	else
		return 1
	fi
}
function toggle()
{
	if [ -e /var/run/openvpn.pid ] ; then
		stop_vpn
	else
		start_vpn $1 $2
	fi
}

[ -d $confdir/$1 ] || echo "Profile doesn't exist"

if [ $2 ]; then
	choice=$2
else
	choice='toggle'
fi

case $choice in
	start)
		start_vpn $1 $confdir || echo "Already up"
		;;
	stop)
		stop_vpn || echo "Not up"
		;;
	*)
		toggle $1 $confdir
		;;
esac
{% endhighlight %}

Die Bedienung ist eigentlich einfach. Ihr ladet euch den Skript runter. Dann passt ihr den ConfigPfad oben an. Dieser kann auf einen Ort eurer Wahl zeigen. Bei mir ist es ~/.openvpn. In diesen Ordner legt ihr pro VPN zu dem ihr euch verbinden wollt einen Ordner an mit dem Name eures VPN. In meinem Beispiel nun "tollesvpn". In den Ordner packt ihr eurer client.conf und die keys von dem VPN.

Nun müsst ihr als root oder mit sudo den Skript aufrufen. Ein "vpn tollesvpn" startet das VPN und der selbe Aufruf beendet es wieder. Das ist cool oder? Natürlich kann man auch gezielt mit "vpn tollesvpn stop" den Skript beenden wo bliebe aber da der Spass.

Zurzeit ist der Skript in Bash geschrieben (Was rückblickend betrachtet eine blöde Idee war, vielleicht mal in Ruby neu schreiben). Ich werde den noch was erweitern und sehen was da noch geht, aber aus meiner Sicht zurzeit die beste und einfachste Lösung für die Kommandozeile.

Have fun
