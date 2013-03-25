--- 
status: publish
layout: post
tags: 
- security
meta: 
  dsq_thread_id: "1119237643"
type: post
published: true
title: DDoS Ping Flood Attacks
summary: Anonymous hactivist group is becoming popular all around the world, mainly for the reason that they are against Internet censorship, and they attack govt. websites. Because many ISPs in India had blocked file and video sharing websites, A new operation under Anonymous known as Op_India started working. They shut down
---
_---This article is just for educational purposes---_

Anonymous hactivist group is becoming popular all around the world, mainly for the reason that they are against Internet censorship, and they attack govt. websites :P

Because many ISPs in India had blocked file and video sharing websites, A new operation under Anonymous known as <i>Op_India </i>started working.
They shut down Indian Judiciary and Congress Websites, and after a few days of this attack they made a new webpage on BJP's website and spread its link of which BJP was totally unaware till a few hours.
This makes us wonder **How Do They Do It?**

These are done by DDoS (Distributed Denial-of-Service) attacks. Like Ping Flooding, Teardrop etc.

**Ping Flooding -**>It is basically sending overwhelming amounts of ICMP packets through various computers to the victim (which is generally a small-website) using Bot-Nets. If the attacker sends too many packets the victim's machine would crash, thus setting the website down.
The command for Ping Flood is <code>ping -f &lt;ipaddress&gt;</code>
You can try this (on your own responsibility) on this address <b>127.0.0.1 </b>which is your own computer (localhost).
The output will be something like this
<pre><code>darkapex@xyz:~$ sudo ping -f 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
^C
--- 127.0.0.1 ping statistics ---
66955 packets transmitted, 66955 received, 0% packet loss, time 1325ms
rtt min/avg/max/mdev = 0.003/0.003/5.499/0.021 ms, ipg/ewma 0.019/0.003 ms</code></pre>
Just remember to press Ctrl+C otherwise it wont stop and you would keep sending packets to yourself!!

The Attackers' bandwidth, CPU speed and Memory should be higher than the website servers'.You will need many computers on various networks to attack at the same time to damage a small website.

If you think that using only your pc to attack will work then I can't assure you because generally when servers get too much packets from the same host, they BLOCK it temporarily  or sometimes permanently.

**Layer 4/ Layer 7 DoS Attacks -** Commented below by Drarqua Storm "The SYN flood attacks are outdated . A simple firewall can prevent them .
But a more powerful one are the layer 4 DoS attacks .
You just open the webpage and you send unlimited get requests + with
a great number of threads .
Despite these attacks , the most powerful attacks at the moment
are the layer 7 Dos ones . You attack straight the web server (Apache)
with a tool like slowloris ."

I hope you will make good use of the info in protecting your own website from such attacks. These attacks seem simple, but taking actual control of many computers, and pinging from all of them together is not an easy job. You shouldn't worry! **Do not perform any illegal act.**
