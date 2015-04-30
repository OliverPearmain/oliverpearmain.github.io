---
layout: post
title: Changing a Websites Site Name in IIS 7

redirect_from:
  - /blog/changing-a-websites-site-name-in-iis-7/
---

Rather inconveniently there doesn’t seemed to be a way to rename your websites in the IIS Manager UI.  Everywhere the “Site Name” appears its greyed out and unchangable; I guess Microsoft have their reasons.

Fortunately you don’t have to delete and recreate your entire site to be able to rename, this task can be performed from the command line using the appcmd.exe utility.

Run the windows command processor but ensure you “Run as Administrator” and use the following commands:

{% highlight batch %}
cd C:\Windows\SysWOW64\inetsrv\
appcmd set site ExistingSiteName -name:NewSiteName
{% endhighlight %}

Thats it you’re done!

Also after discovering the above I found a requirement to rename a virtual directory (adding a number on the end to remove any possibility of client caching) using the same utility…

{% highlight batch %}
appcmd set VDIR "Default Web Site/oldVDirName" -path:/newVDirName
{% endhighlight %}

Plus if you had any Applications living under that virtual directory then you’ll need to move them also else they’ll be lost in oblivion….

appcmd set APP "Default Web Site/oldVDirName/MyApplication" -path:/newVDirName/MyApplication