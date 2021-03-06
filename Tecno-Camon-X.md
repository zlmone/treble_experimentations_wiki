# Tecno Camon X

I had to install magisk in my boot.img file for it to boot because it kept on restarting

**Android 8.1**
***

Almost all the roms from [here](https://github.com/phhusson/treble_experimentations/releases) worked with little to no modifications


**Android 9**
***

I had a problem where the device would boot once and then after a reboot it would be stuck in a bootloop however there is a fix which requires you to have a PC, what you have to do is enter `adb root & adb shell setprop ro.audio.ignore_effects true` using adb to fix the bootloop, and after you boot you should enter this in adb while your device is still connected to make it a permanent fix (note this is a series of commands)  `adb shell<enter>phh-su<enter>mount -o remount,rw /<enter>mount -o remount,rw /system<enter>echo ro.audio.ignore_effects=true >> /system/build.prop`. If you do that bootloop will be fixed

**Android 10**
***
To be able to boot android 10 you'll need to manually disable verity or use phh-magisk,
if there is a bootloop use this command `adb root & adb shell setprop ro.audio.ignore_effects true`

## Steps to install
Since there is no working version of TWRP on this device, I used adb and fastboot to flash the rom

Edit: TWRP for this device is found [here](http://www.mediafire.com/file/5lqwu35xlrnf9wo/TWRP_for_Tenco_Camon_X_%2528CA7%2529.zip/file)

* Step 1
While you are still on your stock rom, you need to patch boot.img with magisk otherwise it'll not boot
Download adb and fastboot from [here](https://androidmtk.com/download-minimal-adb-and-fastboot-tool)
i used  rom to run pie
I ran AOSP v119 with gapps
* Step 2
After getting the necessary files i used the this [guide](https://www.xda-developers.com/flash-generic-system-image-project-treble-device/) to flash the .img from the rom i had and dont forget to wipe data if you dont want to run into a problem while booting.

## Hardware support

| Component                 |      Comment                                                       |
|---------------------------|--------------------------------------------------------------------|
| Camera                    | Works                                                              |
| Speaker / Mic             | Works                                                              |
| Bluetooth                 | Works                                                              |
| WiFi                      | Works                                                              |
| SIM / Mobile Data / Voice | Works                                                              |
| VoLTE                     | havent tested                                                      |
| Fingerprint               | Works                                                              |
| NFC                       | Doesn't have                                                       |
| Offline Charging          | Not working                                                        |
| Other feature             | Status                                                             |
---

Tested By: Tashi 
Model-Number(region): International
Firmware Version - 
Date tested - 30 October 2019
Edited and Updated By: Racka98 (23 January 2019)
Template created by @zguithues and @hackintosh5
