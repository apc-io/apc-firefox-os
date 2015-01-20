# 1. INTRODUCTION

This document introduces step-by-step instructions to build Firefox OS for APC 8880 (aka ROCK II).

Porting method comes from Mozilla. Details can be found at:
* https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Porting

Building prerequisites can be found at:
* https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Firefox_OS_build_prerequisites
* http://source.android.com/source/initializing.html#installing-the-jdk for JDK installation since we need it to support OTA

Building process follows official building guidelines for Firefox OS, which can be found here:
* https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Preparing_for_your_first_B2G_build
* https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Building


# 2. BUILDING STEPS

## 2.1. PREPARE FOR YOUR FIRST BUILD

Assume that we already setup the build environment, below are the steps:

### 2.1.1. CLONE B2G REPOSITORY

The very first step, before you can start your first build, is to clone the B2G repository. This
will not fetch everything, but only the B2G build system and setup utilities.

**Notes**: 
> * We use GitHub ssh access method, so please make sure to setup your ssh key first.
> * The guide to setting up your ssh key can be found here: https://help.github.com/articles/generating-ssh-keys

To clone the repository, use git:

    $ git clone git@github.com:apc-io/apc_b2g_b2g.git B2G

After cloning (which should only take a minute with a fast connection), change into the B2G directory:

    $ cd B2G

Switch to device specific branch (**apc8880-master**):

    $ git checkout apc8880-master

### 2.1.2.  CONFIGURE B2G FOR YOUR DEVICE

Once you've retrieved the core B2G build system, you need to configure it for
the device on which you plan to install it.

Run the following command for this purpose:

    $ ./config.sh vixen

For more details on using config.sh, see:
* https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Preparing_for_your_first_B2G_build#Configuring_B2G_for_your_device

## 2.2. START THE BUILD

To start building, run:

    $ ./build.sh

For more details about building process, see:
* https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Building


# 3. FLASH TO THE DEVICE

## 3.1. NOTES AND REQUIREMENTS

As we use the official flashing method of APC 8880 (which is different from the one by Mozilla),
_flash.sh_ won't work. However, _flash.sh_ is still required to flash some specific modules, such
as __Gecko__ or __Gaia__. For more details about using _flash.sh_, please see:
* https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Installing_on_a_mobile_device

## 3.2. FIRMWARE PACKAGE

Since we use the flashing method of APC 8880, we need to have its firmware package. The firmware package can be found at: https://github.com/apc-io/vixen_firmware_update, it is the FirmwareInstall folder.

This method also require creating a rootfs package in a special way. We will use a script for this. The script is *prepare_android_rootfs.sh* and can be found at: https://github.com/apc-io/vixen_firmware_update, inside __scripts__ folder.

## 3.3. PREPARE THE PACKAGE

- Copy *prepare_android_rootfs.sh* script to your **B2G** directory.
- After building process is ok. Run the script:
```sh
$ ./prepare_android_rootfs.sh
```
This script will create a bunch of stuff under __{B2GROOT}/FirmwareInstall__. The files under __{B2GROOT}/FirmwareInstall/firmware/__ is what we need to care about. Among of them, there's a file name __android4.2.tar__, that is the rootfs package.

## 3.4. FLASHING STEPS

- Extract the firmware package to the root of your sdcard.
- Copy rootfs package to __{SDCARD}/FirmwareInstall/firmware/__. This will replace the old file.
- Be sure to unmount/eject your sdcard correctly so there's no error with the filesystem!
- Insert the sdcard to the board and start it up. The flashing process will be started automatically!
