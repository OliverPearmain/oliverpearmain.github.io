---
layout: post
title: Dropbox and Tortoise SVN (Subversion) Icon Overlays in Harmony

redirect_from:
  - /blog/dropbox-and-tortoise-svnsubversion-icon-overlays-in-harmony/
---

If you’ve been using both [Dropbox][dropbox_referral_URL]{: target="_blank" } & [Tortoise SVN][tortoise_SVN_website_URL]{: target="_blank" } simultaneously on Windows then you may have come across some irritating issues with the icon overlays used by both programs in Windows explorer.

##Fix Missing Icon Overlays

Some users may be experiencing issues with their overlay icons simply not appearing at all. This is probably due to the lame Windows restriction which only allows a maximum of 15 icon overlays to be used.

1) 	Run “regedit” and locate:

	{% highlight batch %}

    "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\
    Explorer\ShellIconOverlayIdentifiers\"
    
	{% endhighlight %}

At this level you will see a number of registry folders each representing a particular icon overlay. This list doesn’t show the 4 icon overlays used by the Windows system and so actually only 11 of the folders shown will actually be used, the others are just abandoned by Windows, nice one Bill!

Luckily for us the way Windows decides which 11 to use is by simply taking the first 11 in alphabetical order. Luckily again Windows doesn’t care what the folders are named in the registry and in this way we can rename the folders to ensure that the 11 icons we want to work are the first 11 alphabetically.

Ultimately however this means you’ve got to decide which icons to bin. Personally I’ve chosen “Offline Files” (some icon used by Windows sync which I’ve never seen), and “TortoiseReadOnly”. You may however have to ditch more depending on what programs you’ve got installed and so the decision is up to you, sorry peeps you’re on your own here.

NOTE: At this point I must stress its always advisable to backup before editing the registry.

2) Rename the folders so they're in the order you want (mine looked like below):

![Fix Missing Icon Overlays](/images/tortoise-icons/FixMissingIconOverlays.png)

3) Restart the “explorer.exe” process by killing in it task manager and then restarting (using File – “New task” – explorer)

And bingo, any icons you were previously missing should have re-appeared.

##Getting Tortoise SVN Icons to Take Priority Over Dropbox Icons

The most annoying gripe for me was that when I had a SVN project checked out to my [Dropbox][dropbox_referral_URL]{: target="_blank" } folder I had no idea what files when modified, added, removed etc because all Windows Explorer would ever display was the [Dropbox][dropbox_referral_URL]{: target="_blank" } icon overlays instead of the [Tortoise SVN][tortoise_SVN_website_URL]{: target="_blank" } ones.

Using the same technique as described above you can rename the icon overlay registry folders so that the [Tortoise SVN][tortoise_SVN_website_URL]{: target="_blank" } icons appear before the [Dropbox][dropbox_referral_URL]{: target="_blank" } icons and thus they take priority.

I renamed mine (as below left), restarted the “explorer.exe” process and now the [Tortoise SVN][tortoise_SVN_website_URL]{: target="_blank" } icons take precedence (see below right):

![Tortoise Icons Take Priority Over Dropbox Icons](/images/tortoise-icons/TortoiseIconsTakePriorityOverDropboxIcons.png){: style="display: inline-block" }
![Tortoise Icons Take Priority Explorer](/images/tortoise-icons/TortoiseIconsTakePriorityExplorer.png){: style="display: inline-block" }

##Optionally: Disable the Dropbox “Green Tick” Overlay

Whilst searching the [Dropbox][dropbox_referral_URL]{: target="_blank" } forums I saw alot of users moaning that they wanted to remove the default “green tick” icon overlay used by [Dropbox][dropbox_referral_URL]{: target="_blank" } altogether. This can be achieved as follows:

- Within the “DropboxExt1″ registry folder (or whatever you named it earlier)
- Right click the “(Default)” value and select “Modify”
- Prefix the existing value with any text so that Windows can’t find it, e.g.
	{% highlight batch %}
		"MANUALLY_EDITED_{FB314EDA-A251-47B7-93E1-CDD82E34AF8B}"
	{% endhighlight %}
- Restart the “explorer.exe” process.

Voila, any [Dropbox][dropbox_referral_URL]{: target="_blank" } files/folders that aren’t sync’ing or error’ed will display their regular icon.


[dropbox_referral_URL]: http://www.dropbox.com/referrals/NTEyODcyNzI3OQ
[tortoise_SVN_website_URL]: http://tortoisesvn.net/