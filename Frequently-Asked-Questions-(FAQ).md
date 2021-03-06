Here are some answers to the most asked questions about GSIs and Project Treble in general:

### What is Google’s Project Treble?

A good overview of Project Treble is provided in [this](https://www.xda-developers.com/googles-project-treble-modularize-android-so-oems-can-update-devices-faster/) XDA article by M. Rahman.

For a more technical discussion of Treble, you can listen to [Episode 75 of the Android Developers Backstage podcast](http://androidbackstage.blogspot.ca/2017/08/episode-75-project-treble-for-hal-of-it.html).

### Why is it called "treble"?

It might be a play on the Meghan Trainor song [All About That Bass](https://youtu.be/7PCkvCPvDXk). That's  because Project Treble is all about standardizing the **base** of Android; i.e. it's about standardizing the APIs that allow the Android framework to communicate with hardware components.

### How can I check if my device is treble-enabled?

[Method 1 (preferred)](https://play.google.com/store/apps/details?id=tk.hack5.treblecheck) - [Method 2](https://www.xda-developers.com/project-treble-android-oreo/)

Note that any device that launched with Android Oreo must be treble-enabled.

You can find an updated list with supported devices here: [[Home]].

### What's a GSI?

GSI stands for Generic System Image. It's a file-system image that you flash to your device's system partition.  It's generic because it accesses hardware using the new standardized hardware APIs (so it should work on any treble-enabled device).

You can find an updated list for available GSIs here: [[Generic System Image (GSI) list]].

### What does "AB" and "A-only" mean? Should I use an "AB" GSI or an "A-only" GSI?

phh has provided "AB" and "A-only" GSIs.  The terms "AB" and "A-only" (or just "A") refer to the partition style used by a device.

The AB partition style was introduced in Android N to support [seamless OTA updates](https://source.android.com/devices/tech/ota/ab/).

A-only, A, or non-AB refers to the [legacy partition style](https://source.android.com/devices/tech/ota/nonab/).

If you have an AB device, then you must flash it with an AB GSI. Note that if an AB GSI works it does not mean that your phone supports seamless upgrades, and likewise, if your phone does not support seamless upgrades, it might still use AB. However, if it supports seamless upgrades, it definitely uses AB. You can check for sure using [this app](https://play.google.com/store/apps/details?id=tk.hack5.treblecheck). The "System-as-Root" section represents A/B support.

### What is the difference between FLOSS, GAPPS, GO and Vanilla?

GAPPS versions include the proprietary Google apps from [Open GApps](http://opengapps.org) nano package (see [Package Comparison](https://github.com/opengapps/opengapps/wiki/Package-Comparison)) and the following additional packages:
* [Google Chrome](https://play.google.com/store/apps/details?id=com.android.chrome)
* [Calculator](https://play.google.com/store/apps/details?id=com.google.android.calculator)
* [Clock](https://play.google.com/store/apps/details?id=com.google.android.deskclock)
* [Calendar](https://play.google.com/store/apps/details?id=com.google.android.calendar)

GO versions include proprietary [Android (Go edition)](https://www.android.com/versions/go-edition/) alternatives to Google apps (see [here](https://github.com/phhusson/gapps-go/blob/master/gapps-go.mk#L8)).

FLOSS versions include the following open source alternatives to GAPPS:
* [phh's Superuser](https://f-droid.org/en/packages/me.phh.superuser/)
* [NewPipe](https://f-droid.org/en/packages/org.schabi.newpipe/)
* [Silence](https://f-droid.org/en/packages/org.smssecure.smssecure/)
* [OsmAnd~](https://f-droid.org/en/packages/net.osmand.plus/)
* [Lightning](https://f-droid.org/en/packages/acr.browser.lightning/)
* [Etar](https://f-droid.org/en/packages/ws.xsoh.etar/)
* [Transportr](https://f-droid.org/en/packages/de.grobox.liberario/)
* [MuPDF viewer](https://f-droid.org/en/packages/com.artifex.mupdf.viewer.app/)
* [AnySoftKeyboard](https://f-droid.org/en/packages/com.menny.android.anysoftkeyboard/)
* [Yalp Store](https://f-droid.org/en/packages/com.github.yeriomin.yalpstore/)
* [K-9 Mail](https://f-droid.org/en/packages/com.fsck.k9/)
* [Riot.im](https://f-droid.org/en/packages/im.vector.alpha/)
* [DAVdroid](https://f-droid.org/en/packages/at.bitfire.davdroid/)
* [Nextcloud](https://f-droid.org/en/packages/com.nextcloud.client/)
* [F-Droid](https://f-droid.org/en/packages/org.fdroid.fdroid/)

Vanilla versions do not include any of the above.

### How do I flash a GSI?

First, you must unlock your bootloader (this is a capability your device manufacturer may or may not offer to end-users).
To flash a GSI, you can use fastboot ```fastboot flash system <gsiname.img>``` or TWRP ```Install > System Image```.

If you need a more detailed guide, read [this article](https://www.xda-developers.com/flash-generic-system-image-project-treble-device/) by M. Rahman.


### How to bypass certified device after first boot?

- Reboot to recovery

```
adb root
adb shell 'sqlite3 /data/data/com.google.android.gsf/databases/gservices.db'
```

- Select * from main where name = \"android_id\";"
- Then register [here](https://www.google.com/android/uncertified/) and reboot

### How to build a GSI?

Follow [this guide](https://github.com/phhusson/treble_experimentations/wiki/How-to-build-a-GSI%3F)

### Why do latest GSI packages have xz file extension? How to install it?

Starting from v19 (2018-06-03), releases are now compressed with xz. Uncompress before flashing.

***

this page will be updated soon with more....