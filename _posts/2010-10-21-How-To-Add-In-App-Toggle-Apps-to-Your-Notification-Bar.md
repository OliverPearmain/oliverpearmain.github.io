---
layout: post
title: How To Add In-App Toggle Apps to Your Notification Bar

redirect_from:
  - /blog/how-to-add-in-app-toggle-apps-to-your-notification-bar/
---

I have a lot of Android phone users who cannot use my “In-App” Android applications because either their phone doesn’t have the necessary hard keys available or because their phone manufacturer has retardedly hard coded their hard keys, not mentioning any names… Motorolla!!!

I have come up with a solution to this issue, which is to add the application as a shortcut in your notification bar.  With the help of another couple of well respected applications this is possible as below.  (This at present isn’t something you can do with the “In-App” applications alone I’m afraid although I plan to add it in future releases).

1. Install “Bar Tender Lite” (available free from the Android Market, author “PinkVenture”)
2. Install “Any Cut” (available free from the Android Market, author “Jeff Hamilton”)
3. Open “Bar Tender Lite” from your application tray
4. Press the “+ Item” button
5. Select “Any Cut”
6. Select “Make your own”
7. In the “Action” text field type exactly (ensure you get the case correct):
			android.intent.action.VOICE_COMMAND
8. Do NOT type anything for “Data” or “Type”, leave them blank
9. Press “OK”
10. Enter a name of your choice for the shortcut, I suggest “Toggle Wifi” or “Toggle Bluetooth”
11. Press “OK”
12. Back in “Bar Tender Lite” application, press “Save” and exit the application

Now you’re done. You should be able to drag down your notification bar from any context and you should always have a In-App shortcut available.  Note, once you’ve set-up the shortcut you can actually uninstall “Any Cut” if you want to save some space.

The original point of the “In-App” apps was to be able to enable/disable in a single press however I feel a swipe followed by a press isn’t a bad compromise, heh?

I would welcome any feedback on whether this has assisted people (or not)!

###Troubleshooting:

- If you receieve an “Application is not installed on your phone” Message

    Make sure you typed the “Action” exactly as above, the case has to be exactly the same, it can’t have spaces, the first character should NOT be a capital.

- If you encounter other errors with “Any Cut”

    Instead of Installing “Any Cut”, try installing “Manual Intent Shortcuts”, at step 5) select “Manual Intent Shortcuts”, type “Toggle Wifi” for the “Shortcut Name” and “android.intent.action.VOICE_COMMAND” for the “Action”, press OK. 

