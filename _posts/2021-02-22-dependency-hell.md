---
layout: post
published: false
title: Dependency Hell
---
![Photo By Asa Rodger]({{site.baseurl}}/img/asa-rodger-nezHaCwch2w-unsplash.jpg)


As an engineer i find the following frustrating:

Installation instructions that require you to jump through hoops to get through firewalls.
For example. 'pip install $package'
$package may need to be downloaded from pip so you need to get pip urls/IP addresses to proceed and raise a change to allow you to access the resources through the firewalls.
Once you step over that hurdle, you get stopped because $package from $packagehost has a dependency which requires $dependancy_package. Again, you need to find the source that $dependancy_package uses to then raise a change request to then change the firewall. Sometimes you can hit multiple dependancies and packages and it can take you a fair while to get the software installed.

Depending on the complexity of your network it can be enough to make you cry. But who is responsible and what can be done about it?

1, The software vendor?
Maybe. They choose the dependencies. They should document the URLs/IP addresses in their install documentation. They should also welcome feedback of this nature to improve their documents. This should be considered best practice though I am not sure anyone really considers it.

2, The Firewall
Not really, the firewall is just doing it's job. If you allow your servers the freedom to reach out to the Internet then you have a greater risk of your server downloading horrible/nasty things. A tight access-control list is appropriate. Even if you don't restrict on your dev network, you can potentially not know what repositories the $package requires so you end up in the same situation. Installing in production after your sucessful tests becomes problematic. You also can't just allow all traffic on the firewall for one server temporarily as $package may require some critical updates after you lock the server down. It gets more frustrating if the firewall doesn't do DNS and if the vendor is using a CDN... the IPs can change.

3, The user
For now, yes. I say this because the user should inform the vendor to document it otherwise others will also find this stumbling block.
