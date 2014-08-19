Beaglebone-Black-Cape-Fixes
===========================

This is a place for me to put a few Beagle Bone Black Cape fixes for the 3.12 version kernels. This dtbo file shouldn't be needed on 3.8 versions of the kernel. The first (and maybe only) cape is the 7" LCD Touchscreen cape from 4D!

Using this dtbo file
====================

To use this cape, make sure you are running a 3.12 version of the kernel. I haven't tried other versions. All you should need to do is place the BB-BONE-LCD7-01-00A0.dtbo file from this repo into this directory on the Beaglebone Black:

/lib/firmware

Once that's done, and the cape is installed on the BBB, run this line to configure the LCD:

echo BB-BONE-LCD7-01 > /sys/devices/bone_capemgr.*/slots

This should load the cape's device layer mappings and the LCD should start. Note: When I ran this through an SSH terminal, the terminal kicked me out. I was able to log right back in but don't get too scared if this happens to you).

Compiling the dtbo file
=======================

To compile the dts into a useable dtbo file, you'll need an up to date version of DTC. I patched the existing version on github and did a pull request but it hasn't been accepted yet. You can find that here:

https://github.com/JamesHagerman/dtc

Once you have a good, working version of dtc on your beaglebone, you should be able to compile the BB-BONE-LCD7-01-00A3.dts file into it's respective dtbo file using this line:

dtc -O dtb -o BB-BONE-LCD7-01-00A3.dtbo -b 0 -@ -I BB-BONE-LCD7-01-00A3.dts

Don't mind the change from 00A3 to 00A0. For some reason the Beaglebone tries to load the 00A0 file even if it doesn't exist and the 00A3 version does. I have no idea how to tell the cape manager to load a specific version of the dtbo file. Any hints would be nice in this regards.

I hope someone finds this a bit useful!

Any suggestions or fixes would be awesome!

