---
layout: post
published: false
title: SaltStack - In the begining
---
<a style="background-color:black;color:white;text-decoration:none;padding:4px 6px;font-family:-apple-system, BlinkMacSystemFont, &quot;San Francisco&quot;, &quot;Helvetica Neue&quot;, Helvetica, Ubuntu, Roboto, Noto, &quot;Segoe UI&quot;, Arial, sans-serif;font-size:12px;font-weight:bold;line-height:1.2;display:inline-block;border-radius:3px" href="https://unsplash.com/@mishalibrahim?utm_medium=referral&amp;utm_campaign=photographer-credit&amp;utm_content=creditBadge" target="_blank" rel="noopener noreferrer" title="Download free do whatever you want high-resolution photos from Mishal Ibrahim"><span style="display:inline-block;padding:2px 3px"><svg xmlns="http://www.w3.org/2000/svg" style="height:12px;width:auto;position:relative;vertical-align:middle;top:-1px;fill:white" viewBox="0 0 32 32"><title>unsplash-logo</title><path d="M20.8 18.1c0 2.7-2.2 4.8-4.8 4.8s-4.8-2.1-4.8-4.8c0-2.7 2.2-4.8 4.8-4.8 2.7.1 4.8 2.2 4.8 4.8zm11.2-7.4v14.9c0 2.3-1.9 4.3-4.3 4.3h-23.4c-2.4 0-4.3-1.9-4.3-4.3v-15c0-2.3 1.9-4.3 4.3-4.3h3.7l.8-2.3c.4-1.1 1.7-2 2.9-2h8.6c1.2 0 2.5.9 2.9 2l.8 2.4h3.7c2.4 0 4.3 1.9 4.3 4.3zm-8.6 7.5c0-4.1-3.3-7.5-7.5-7.5-4.1 0-7.5 3.4-7.5 7.5s3.3 7.5 7.5 7.5c4.2-.1 7.5-3.4 7.5-7.5z"></path></svg></span><span style="display:inline-block;padding:2px 3px">Mishal Ibrahim</span></a>


In the begining, I had attended the OSS Summit and achieved a level of enlightenment from a talk by @supertylerc. The subject was Network Automation. His demostration provided the use of Saltstack, proxy minions and some networking devices and how after taking a port down, managed to get the OSPF matric changed almost instantly.

Since then, I have trying to find the time to create a simplistic lab with a Salt-Master, Salt-Minion & Salt-Proxy. I have a test Cisco 3560 as1.test running a recent version of ios and Cisco ASR903 pe1.test running a recent version of ios-xe.

So after defining my pillar_roots on my master, I have created a top.sls file & a as1.test.sls file in the pillar_roots

```cat top.sls as1_test.sls 

base:
  'as1.test':
    - as1_test
  'pe1.test':
    - pe1_test
    
proxy:
  proxytype: napalm
  driver: ios
  host: as1.test
  username: mcparty
  passwd: WordUp
```

There is a lot of talk about Cisco devices but it took 6 hours of searching to find that if you are using ios-xe you can use the NAPALM ios driver.


```

##

NAPALM
In a nutshell NAPALM is a python library which you can query without the use of Saltstack which is a good troubleshooting tool.


