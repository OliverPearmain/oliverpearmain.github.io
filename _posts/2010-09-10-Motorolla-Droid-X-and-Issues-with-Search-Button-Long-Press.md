---
layout: post
title: Motorolla Droid X and Issues with Search Button Long Press

redirect_from:
  - /blog/motorolla-droid-x-and-issues-with-search-button-long-press/
---

>UPDATE: You may now be able to get my “In-App” applications working on your Droid X handset. Please see [How To Add In-App Toggle Apps to Your Notification Bar]({% post_url 2010-10-21-How-To-Add-In-App-Toggle-Apps-to-Your-Notification-Bar %}).

It has been brought to my attention by a number of Droid X users that my “In-App” Android applications aren’t working for them when performing a search key long press. Instead of launching my app or presenting the user with a choice of apps to launch, the “Voice Search” application is ALWAYS launched.

I have done some investigtion into this problem and it would appear the issue lies with the Droid X handset and not with my applications. Unfortunately for now this means that all of my “In-App” applications are incompatible with the Droid X handset, sorry for the inconvenience.

On a typical Android handset when the user long presses the search key the “android.intent.action.VOICE_COMMAND” intent is launched. This doesn’t appear to happen on the Droid X. Motorolla must have hard wired the long press to the “Voice Search” application. All other Android applications in the market that subscribe to this intent will have this issue, another example is “Button Shortcut” (take a look at some of the comments). 