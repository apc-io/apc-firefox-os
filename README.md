APC + Firefox OS
==============

This is the official repository for Firefox OS on APC. Firefox OS is currently under heavy development. To learn more about the general state visit [Mozilla's Development site](https://developer.mozilla.org/en/docs/Mozilla/Firefox_OS). What follows is specific information about Firefox OS on APC.

## Change log
### Release 2014-01-13 (v1.03.01)
1. Updated to the new Mozilla code from 2013.12.25 (gecko & gaia).
2. Enabled hardware key repeating.
3. Supported NTFS external HDD/USB storage.
4. Fixed finished tutorial screen so we can swipe up to close the window.
5. Supported USB camera and USB camera hot plug. But, please note that: due to updating to the new Gecko from Mozilla (2013.12.25) the camera preview screen keep splashing when we moving the mouse.
6. Supported generic USB bluetooth dongle.
7. Integrated Realtek 8723 Bluetooth/WiFi combo dongle drivers. However, WiFi function does not work yet, you can only scan the available networks, but cannot connect to a network.

### Release 2013-11-22 (v1.02.01)
1. Updated firmware package to support HDMI hotplug as the solution from VIA
1. Switched to latest base from Mozilla and using master branch for all Mozilla repos
1. Support multiple hardware keyboard hot plug
1. Fixed so that Mozilla soft home button can be enabled via settings
1. Supports Ethernet cable hot plug
1. Enabled SNTP with Ethernet network
1. Set default display timeout to never
1. Fixed some orientation bug due to migration to master
1. Fixed WiFi connection bug due to migration to master
1. Supports Mouse wheel event


## Known Issues
Here is a list of known issues, from the perspective of an end-user:

1. Most web video (eg: Youtube, Vimeo) will not playback. Hardware video decoding is not working yet
1. *No scroll wheel mouse support [FIXED - v1.02.01]*
1. Limited WiFi support
1. Limited Ethernet support
1. No user interface for controlling volume
1. Peripherals (HDMI, LAN, ...) must be connected before powering on
1. Various layout issues with the main user interface (eg: overlapping text, ...)
1. *USB storage devices are not recognized [FIXED]*
1. VGA port is not supported (Rock only)
2. Camera preview screen keep splashing when moving the mouse cursor (v1.03.01)

## Get a Free APC
To speed up the development, this project is giving away an APC to any developer who fixes an issue with the label ["Free APC"](https://github.com/apc-io/apc-firefox-os/issues?labels=Free+APC&state=open).

If you're interested, just send us a pull request. When validated, we will send you a free APC.

## Build Instructions
See [APC 8950 Building Guide](https://github.com/apc-io/apc-firefox-os/blob/master/building-guide.md)

## Getting Help
Email [dev@apc.io](mailto:dev@apc.io)
