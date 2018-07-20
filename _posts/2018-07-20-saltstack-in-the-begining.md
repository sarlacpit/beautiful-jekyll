---
layout: post
published: false
title: SaltStack - In the begining
---
In the begining, I had attended the OSS Summit and achieved a level of enlightenment from a talk by @supertylerc. The subject was Network Automation. His demostration provided the use of Saltstack, proxy minions and some networking devices and how after taking a port down, managed to get the OSPF matric changed almost instantly.

After a hard sell in the office, I have trying to attain a simplistic lab with a Salt-Master, Salt-Minion & Salt-Proxy. I have a test Cisco 3560 from which to try things out on. I am still very new to Saltstack.

So after defining my pillar_roots on my master, I have created a top.sls file & a as1.test.sls file in the pillar_roots

```cat top.sls as1.test.sls 
base:
  'as1.test':
    - as1.test
proxy:
  proxyauth: ssh
  proxytype: napalm
  driver: ios
  host: as1.test
  username: mcparty
  password: WordUp
```

After trying to bring up the proxy-minion, i receive an error which has bamboozled me as my YAML is valid and they syntax is apprently correct (according to the networktocode folks on Slack) so something else must be a little wrong.:

```salt-run pillar.show_pillar 'as1.test'
[ERROR   ] Specified SLS 'as1.test' in environment 'base' is not available on the salt master
[ERROR   ] Template was specified incorrectly: False
[CRITICAL] Pillar render error: Specified SLS 'as1.test' in environment 'base' is not available on the salt master
_errors:
    - Specified SLS 'as1.test' in environment 'base' is not available on the salt master
    ```