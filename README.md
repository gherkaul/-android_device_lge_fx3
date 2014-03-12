-android_device_lge_fx3
=======================

LS720 and VM720 device tree

Optimus F3 Recovery


Place in /device/lge/fx3

assuming you did repo sync in ~/android

~/android/device/lge/fx3

$ . build/envsetup.sh

$ breakfast fx3


if you're building recovery only:

$ make recoveryimage

Contents will output into the $out directory:

/home/.../.../out/target/product/fx3/recovery.img

&&

/home/.../.../out/target/product/fx3/ramdisk.img

kernel is from jmztaylor

Source:

https://github.com/jmztaylor/android_device_lg_ls720

To pull blobs off of phone, Turn on USB Debugging, connect phone via usb and connect as (MTP)

$ cd ./device/lge/fx3

$ chmod 755 extract-files.sh

$ chmod 755 setup-makefiles.sh

$ extract-files.sh


To flash recovery.img copy to /sdcard or /storage/externel_SD
I would recomend using adb to push the files. Much much quicker that way.

Using adb shell:
$ adb shell

$ su


Make a backup to the sdcard first with:
dd of=/sdcard/original.img if=/dev/block/platform/msm_sdcc.1/by-name/recovery



When you are ready:
dd of=recovery.img if=/dev/block/platform/msm_sdcc.1/by-name/recovery

To restore the original version, assuming you are in the folder where original.img is, use
dd if=original.img of=/dev/block/platform/msm_sdcc.1/by-name/recovery
