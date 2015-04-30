---
layout: post
title: Holy Smokes, Someone Just Put a Rocket Up My [2.2.2] Nexus One (INIT Android Process Lag/Slow Down Fix)

redirect_from:
  - /blog/holy-smokes-someone-just-put-a-rocket-up-my-2-2-2-nexus-one-init-android-process-lagslow-down-fix/
---

For many months now I’ve been experiencing varied periods of “lag” or “slow down” on my Nexus One Android phone (running FRG83G 2.2.2) . I’d never been able to attribute this slow down to any particular application even with the help of task managers and task killers and diagnostic tools… until now…

With some help from the “Watchdog” app (which continuously monitors all the process on your phone and notifies you if a given process has exceeded a given CPU threshold) I was finally able to attribute the problems to the “INIT” android system process.

Once I’d identified this process as the problem I did a bit of Googling. First, I found a lot of others complaining about this issue on the [Google forums](http://www.google.com/support/forum/p/android/thread?tid=7da0c666e8ffbc36&hl=en){: target="_blank" } but with no apparent solution. Then fortunately I came across an [XDA developers](http://forum.xda-developers.com/showthread.php?t=826507){: target="_blank" } thread that proposed to have the solution!

I am very pleased to confirm that enabling the following option…

{% highlight batch %}
Settings > Applications > Development > USB debugging
{% endhighlight %}

…has fixed the problem entirely. In fact, it has absolutely made my phone run like its on steroids. I’m staggered and absolutely elated by the difference.

Many thanks to “rixsta” @XDA for the fix.

For those wondering here’s a description of the “init” process…

> A key component of the Android bootup sequence is the program ‘init’, which is a specialized program for initializing elements of the Android system. Unlike other Linux systems (embedded or otherwise), Android uses its own initialization program. (Linux desktop systems have historically used some combination of /etc/inittab and sysV init levels – e.g. /etc/rc.d/init.d with symlinks in /etc/rc.d/rc.[2345]). Some embedded Linux systems use simplified forms of these — such as the init program included in busybox, which processes a limited form of /etc/inittab, or a direct invocation of a shell script or small program to do fixed initialization steps.

> The init program processes two files, executing the commands it finds in them, called ‘init.rc’ and ‘init..rc’, where is the name of the hardware that Android is running on. (Usually, this is a code word. The name of the HTC1 hardware for the ADP1 is ‘trout’, and the name of the emulator is ‘goldfish’.

> The ‘init.rc’ file is intended to provide the generic initialization instructions, while the ‘init..rc’ file is intended to provide the machine-specific initialization instructions.

UPDATE: I have since received a system update to gingerbread 2.3.3 GRI40 and this seems to have fixed the issue so the USB Debugging fix is no longer required.