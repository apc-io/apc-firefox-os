#			FIREFOX OS TO APC 8950 - BUILDING GUIDE

I. INTRODUCTION
=================================

This document introduces step by step how to build Firefox OS for APC 8950.

We followed porting method of Mozilla. Details can be found at:
* https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Porting.

Building prerequisites can be found at:
* https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Firefox_OS_build_prerequisites.

Note that we used Ubuntu 10.04 x64 for build PC. Ubuntu 12.04 x64 is also 
proved to be work.

The building process follow official building process of Firefox OS, which can
be found here:
* https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Preparing_for_your_first_B2G_build.
* https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Building.


II. BUILDING STEPS
=================================

## II.1. PREPARE FOR YOUR FIRST BUILD

Assume that we already setup the build environment. So, here are the steps:

### II.1.1. CLONE B2G REPOSITORY

The first step, before you can start your first build, is to clone the B2G
repository. This will not fetch everything! Instead, it will fetch the B2G build
system and setup utilities.

To clone the repository, use git:

	$ git clone git@github.com:apc-io/apc_b2g_b2g.git B2G

After cloning (which should only take a minute with a fast connection), cd into
the B2G directory:

	$ cd B2G

Switch to device specific branch:

	$ git checkout apc8950

### II.1.2.  CONFIGURING B2G FOR YOUR DEVICE

Once you've retrieved the core B2G build system, you need to configure it for
the device on which you plan to install it.

Run the following command for that:

	$ ./config.sh wmid

For more details of using config.sh, see:
* https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Preparing_for_your_first_B2G_build#Configuring_B2G_for_your_device.

## II.2. START THE BUILD

To start building, run:

	$ ./build.sh

For more details about building process, see:
* https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Building.


III. FLASH TO THE DEVICE
=================================

## III.1. NOTES AND REQUIREMENTS

We use official flashing method of APC Rock (not the one from Mozilla), so
_flash.sh_ won't work. However, _flash.sh_ is still usable to flash specific modules
like __Gecko__ or __Gaia__. For more detail about using _flash.sh_, please see:
* https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Installing_on_a_mobile_device.

After building process is success, the result will be at __*out/target/product/wmid*__.
Here we'll need following files:

	- boot.img
	- recovery.img
	- rootfs.b2g_yymmdd.xxx.tgz

For the flashing method, we will need an SD card (1GB free storage would be 
fine, athough the actual firmware update package only takes about 200MB).

## III.2. FLASHING STEPS

Here are the steps:

- Clone the firmware update source:

>

	$ git clone git@github.com:apc-io/apc_8950_firmware_update.git

- Switch to B2G branch:

>

	$ git checkout B2G

- Copy the content of **apc_8950_update_firmware** to the root directory of the SD card.

- Copy new __boot.img__ & __recovery.img__ to __{SDCARD}/bspinst/__. They will replace the
old ones.

- Copy new **rootfs.b2g_yymmdd.xxx.tgz** to __{SDCARD}/bspinst/packages/__. Remember to
__remove__ the previous rootfs tarball there.

- Removed the SD card, put it in to the device.

- Reboot the device. The flashing process will start automatically.

