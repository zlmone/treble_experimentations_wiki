# [Nokia 1] - [frt]

[OEM's support](#oems-support-vendor-and-kernel)

[Android's support](#android-raw-build-support)
# Android RAW build support
## Overview

> These Android builds only works and works best with 00WW_0_39L up to 00WW_1_550 Vendor/Kernel builds.

> It would probably works with Android 9's Vendor/Kernel too if there is System-as-Root build for ARM-A phones. But the screen probably will not work since it blanked out in Android 8.1's last Maintain release (00WW_1_550_SP1, not 00WW_1_550).

## Common bugs in All builds
~~- Builds with Google Play Services crashes a lot. Install OpenGapps with the vanilla builds to fix this.~~ (Only true with older builds)

- You should skip setup wizard because it took a lot of time to complete the "additional" installations.

~~- SMS permission is allowed for Google Play Services app by default but it was faked to be allowed and need to manually switch on/off in settings.~~ (Edit the gapps permissions properly and this won't happen again)

- Edit the device's fingerprint property in /system/etc/prop.default, /system/build.prop, /vendor/default.prop and /vendor/build.prop to stop Google screaming out that this ROM isn't a legit ROM.

- TWRP formats the /data folder in ext4. While we need f2fs to make system work. So only Stock recovery or "fastboot -w" (Only works when bootloader unlocked) can wipe the phone's user data properly.

- USSD incoming message without replies will get fixed in Android 9.

- 1st SIM slot will never get incoming call notification. Android will ignore it completely.

## Android 10
- Very unstable.
- Wi-Fi will kinda hang system. Sometimes will not work at all.
- Quickstep/SystemUI lock screen will hang the system and shows blank screen with System UI bar after a long while (Usually overnight sleep).
- Don't set a lock screen. Will hang system and no password has been set after that. (Encryption issues)
- That means you can't even use your existing user data from Android 8.1 or 9 to upgrade it. It will ask for Non-existent password when done with the upgrade. So backup before doing stuff.
- Video codec is kinda broken (As seen in Google's looped static videos in Pixel Setup Wizard, Gesture settings illustration video)
- If system freaked out and got a Soft-reboot. Modem software will never work again until a full reboot is initiated.
## Android 9
- Wi-Fi hotspot will always broken with any form of Google Apps installed. In older builds without Google Apps it would work, but newer builds will completely break this feature. (Except Android 8.1 has the Wi-Fi hotspot working perfectly. Android 10 will have some sort of problems with Wi-Fi or Wi-Fi tethering)
- Used to has storage limitation to be flashed with v107. So far can flashed with v119 (With no built-in gapps).
- Technically you can downgrade 9 to 8.1. But you can't get pass the lock screen. Because keyguard won't respond to your touches.
## Android 8
- Nothing, except some quirks like internal thermal values like battery capacity or its health and voltage? Though it's literally Android 8.1 so this one will get the best compatibilty.


# OEM's support (Vendor and Kernel)
## Overview
> Build since 00WW_1_550_SP1 will break the screen. Still works though.
> Build 00WW_1_550 will work the best of all Kernel/Vendor builds.
## Build since 00WW_0_39L and above (Android 8.1)
> Won't mention the perfectly working features or known bugs (See older builds below).

| Component                 | Is it working?                                                                                          |
|---------------------------|---------------------------------------------------------------------------------------------------------|
| SIM / Mobile Data / Voice | ✓/✕                                                                                                     |

Bugs that automatically fixed in newer Android or Vendor builds:
- The RIL works fine again in any Android. Except some quirks like in known bugs. (Vendor)
- MediaTek's DocumentsUI overlay (/vendor/overlay) won't break Files app anymore.
## Build since 00WW_1_33A and up (Android 8.1)

| Component                 | Is it working?                                                                                          |
|---------------------------|---------------------------------------------------------------------------------------------------------|
| Camera                    | ✓                                                                                                       |
| Speaker / Mic             | ✓                                                                                                       |
| Bluetooth / Hotspot       | ✓                                                                                                       |
| Wi-Fi                     | ✓                                                                                                       |
| Wi-Fi Hotspot             | ✓/✕ (Gapps somehow break it in Android 9)                                                               |
| USB Tethering             | ✓                                                                                                       |
| SIM / Mobile Data / Voice | ✓/✕ (No signal on SIMs, modem software crashes, LTE/WCDMA broken)                                       |
| VoLTE                     | ✕ (Can't confirm it will work or not)  			                                                      |
| Thermal Sensors           | ✕ (For example: Battery's temp, Battery's voltage) 										              |
| GPS				        | ✓                                                                                                       |
| Camera		            | ✓/✕ (Low light with Camera2 app, Use Google Camera 2.7 or 2.5)                                                                          |
| Adaptive Brightness		| ✕                                                                                                       |
| Night lights      		| ✕                                                                                                       |
| Doze screen       		| ✕                                                                                                       |
| Screen            		| ✓                                                                                                       |

Bugs that automatically fixed in newer Android:
- The RIL works fine again in Android 10. Also true with Network band. Except some quirks like in known bugs.

Known bugs/Workarounds:
- The main purpose of MediaTek's DocumentsUI overlay (/vendor/overlay) is to hide the Files AOSP app in order to prevent duplication of Google's Files (Go) app that is pre-installed with the phone. It also breaks Files app when trying to show Internal Storage. Delete it.
- Secure boot: Broken in Android 9 and up. For Android 9 will sort of works properly while Android 10 will broken completely (And don't even try to upgrade the OS from Android 9. It won't work and will ask you for "non-existent password".
)
- In Android 9. If you pre-lock and enabled lock on boot and happen to enter the wrong password in the first place. System will forced you to press Reset Phone button because you entered the wrong password "too much". Reboot the phone and try again.
- You can't set any form screen locking in Android 10.
- RIL modem: 1st SIM slot will never get incoming call and is the only slot that work as Data SIM with All networks like 4/3/2G. No proper network band selecting.
- 2nd SIM slot will only work as a Non data SIM with 2G only. Forcing system choosing this slot as data SIM will freaks out the modem software (no network on both SIMs, system hangs)
- Prelocking SIM with a PIN will make the phone bootlooped while the phone is completing the initial setup process.
- Wi-Fi in Android 10: Probably unstable.
- Wi-Fi Hotspot in Android 9+: Can't figured out yet. But at least Android 10 won't freak out the OS and soft reboot.
- Booting into Android causes screen went out for a few secs.
- The phone will reboot a few times after reboot (Sometimes, not always).
- For Adaptive Brightness, Night Lights, Doze Screen. You need to edit the framework-res or make an overlay app overlays framework-res to enable them in res/bools.xml.
- Flashing a very different Vendor/Kernel will make Bluetooth crashes.
- Camera: Low light in newer Camera2 app. Use Android 6 or 5's Camera2. Or Google Camera from 2.7 or 2.4 (Android 9+). This feature slowly broken in newer Android incrementals.

## Tested by:
- Kutiz w/ Nokia 1 (TA-1047 Dual-SIM)

## Tested builds:
- Android 8.1 build v26 w/ Google apps and OpenGapps.
- Android 9.0 build v107 w/ no Google apps and OpenGapps.
- Android 9.0 build v119 w/ no Google apps and OpenGapps.
- Android 10 build v200.d w/o Google apps and OpenGapps.
- Android 10 build v204.d w/o Google apps and OpenGapps.

_**Last update:** 7:10 PM; December 22nd, 2019_