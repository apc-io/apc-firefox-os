APC + Firefox OS
==============

This is the official repository for Firefox OS on APC. Firefox OS is currently under heavy development. To learn more about the general state visit [Mozilla's Development site](https://developer.mozilla.org/en/docs/Mozilla/Firefox_OS). What follows is specific information about Firefox OS on APC.

## Change log
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
1. USB storage devices are not recognized
1. VGA port is not supported (Rock only)

## Get a Free APC
To speed up the development, this project is giving away an APC to any developer who fixes an issue with the label ["Free APC"](https://github.com/apc-io/apc-firefox-os/issues?labels=Free+APC&state=open).

If you're interested, just send us a pull request. When validated, we will send you a free APC.

## Build Instructions
See [APC 8950 Building Guide](https://github.com/apc-io/apc-firefox-os/blob/master/building-guide.md)

## Getting Help
Email [dev@apc.io](mailto:dev@apc.io)
