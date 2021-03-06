Here is a quick and dirty list of what are the changes in master/Q that impacts Treble:
- logical volumes (like LVM2 but re-made from scratch)
   - fastbootd (a SECOND fastboot, which will run inside recovery)
   - dynamically resizable/deletable/creatable partitions
   - does it include userdata?
- gsid. Systems will be able to boot GSI instead of themselves
   - GSIs will be "flashable" from (rooted?) shell ( https://android-review.googlesource.com/c/platform/system/gsid/+/863812 )
   - there will be a separated userdata_gsi partition ( https://android-review.googlesource.com/c/platform/system/core/+/863889 )
- apex: loadable system modules, basically ext4 dm-verity loopback. Used for instance to have out-of-firmware upgradable libart
   - com.android.runtime (art)
   - com.android.resolv
   - com.android.conscrypt
   - com.android.tzdata

- dm-verity signed GSI? ( https://android-review.googlesource.com/c/platform/build/+/782877 )
- overlayfs
  - /system or /product can overlay /vendor ( https://android-review.googlesource.com/c/platform/system/core/+/804834 )
- SELinux policy read from /product and /odm additionally ( https://android-review.googlesource.com/c/platform/system/core/+/851068 ) 
- fastbootd: In addition to bootloader fastboot support, there is an additional fastboot support in recovery. Both are complementary and won't do the same things. fastbootd is meant to handle logical partitions