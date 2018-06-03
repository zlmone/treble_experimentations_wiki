# Pixel (Sailfish)

## Hardware

Has been tested on:
* Sailfish US 128Go
* Sailfish ROW 32Go

## GSI tested

[phh](https://forum.xda-developers.com/project-treble/trebleenabled-device-development/experimental-phh-treble-t3709659) and [LineageOS](https://forum.xda-developers.com/project-treble/trebleenabled-device-development/lineage-phh-treble-t3767690). Both work.

## Procedure used

1. Download latest Google image available [here](https://developers.google.com/android/images#sailfish). For me it was 8.1.0 (OPM2.171019.029, Apr 2018).
2. `./flash-all.sh`
3. Reboot to fastboot, then flash the image: `fastboot flash system system-arm64-ab-vanilla-nosu.img` (phh v18 2018-05-14, sha256: `302d2dc6dc55bce68f1ac1216fc05dd49eba3bab29bc3fef4d591bffd050dbcb`) or `fastboot flash system system-arm64-ab.img` (LineageOS v4 2019-05-19, sha256: `3f67636ba164d1c0f7b750070b6db16349e761e1e4dea2ee193b176477152b91`)
4. Erase the data partition: `fastboot -w`
5. Boot the phone

## Notes

It was not tested in depths, but all majors functionalities seems to work: camera, flash, wifi, bluetooth, sounds. Phone call not tested.

# Pixel XL (Marlin)

Not tested.