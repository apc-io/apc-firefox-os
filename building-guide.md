
# 1. INTRODUCTION

This document introduces step-by-step instructions to build Firefox OS for APC 8950.

Porting method comes from Mozilla. Details can be found at:
* https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Porting

Building prerequisites can be found at:
* https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Firefox_OS_build_prerequisites

We are using Ubuntu 10.04 x64 for the build PC. Ubuntu 12.04 x64 is however proved to be working.

Building process follows official building guidelines for Firefox OS, which can be found here:
* https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Preparing_for_your_first_B2G_build
* https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Building


# 2. BUILDING STEPS

## 2.1. PREPARE FOR YOUR FIRST BUILD

Assume that we already setup the build environment, below are the steps:

### 2.1.1. CLONE B2G REPOSITORY

The very first step, before you can start your first build, is to clone the B2G repository. This
will not fetch everything, but only the B2G build system and setup utilities.

To clone the repository, use git:

	$ git clone git@github.com:apc-io/apc_b2g_b2g.git B2G

After cloning (which should only take a minute with a fast connection), change into the B2G directory:

	$ cd B2G

Switch to device specific branch:

	$ git checkout apc8950

### 2.1.2.  CONFIGURE B2G FOR YOUR DEVICE

Once you've retrieved the core B2G build system, you need to configure it for
the device on which you plan to install it.

Run the following command for this purpose:

	$ ./config.sh wmid

For more details on using config.sh, see:
* https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Preparing_for_your_first_B2G_build#Configuring_B2G_for_your_device

## 2.2. START THE BUILD

To start building, run:

	$ ./build.sh

For more details about building process, see:
* https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Building


# 3. FLASH TO THE DEVICE

## 3.1. NOTES AND REQUIREMENTS

As we use the official flashing method of APC 8950 (which is different from the one by Mozilla),
_flash.sh_ won't work. However, _flash.sh_ is still required to flash some specific modules, such
as __Gecko__ or __Gaia__. For more details about using _flash.sh_, please see:
* https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Installing_on_a_mobile_device

After building process is successful, the output will be available at __*out/target/product/wmid*__.
From here we'll need the following files:

	- boot.img
	- recovery.img
	- rootfs.b2g_yymmdd.xxx.tgz

For flashing steps, we will need an SD card (with at least 1GB free storage, even though the actual
firmware update package takes only about 200MB).

## 3.2. FLASHING STEPS

Here are the steps:

- Clone the firmware update source:

>

	$ git clone git@github.com:apc-io/apc_8950_firmware_update.git

- Switch to B2G branch:

>

	$ git checkout B2G

- Copy the content of **apc_8950_update_firmware** to the root directory of the SD card.

- Copy new __boot.img__ & __recovery.img__ to __{SDCARD}/bspinst/__ and accept to overwrite existing files.

- Copy new **rootfs.b2g_yymmdd.xxx.tgz** to __{SDCARD}/bspinst/packages/__. Remember to __remove__ the previous rootfs tarball there.

- Remove the SD card, put it into the device.

- Reboot the device. The flashing process will start automatically.
