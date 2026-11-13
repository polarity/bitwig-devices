# Polarity Bitwig Devices

Native devices for Bitwig Studio by [Polarity](https://polarity.me/). Put the `.bwdevice` files in a folder scanned by Patchbay Mod Loader.

## Install

1. Download the [Patchbay Mod Loader tester release with the Nitro fix](https://github.com/shaboogen-dev/BML/releases/tag/0.36.0-dev.9%2Bnitro-1.2.0-dev.5) and follow `INSTALL.md` in the ZIP. The [Patchbay Mod Loader repository](https://github.com/shaboogen-dev/BML) and its downloads currently require tester access. The release includes **Custom Nitro Registration** `1.2.0-dev.5`, which fixes project recall for scanned devices.
2. Open a device file below and choose **Download raw file**. To get both at once, use **Code → Download ZIP** and extract the `devices` folder. Keep the `.bwdevice` files in a folder of your choice.
3. Close Bitwig. In Patchbay, enable **Framework: Custom Nitro Registration**, then open **Tools → Device Folders** and add the folder containing the files. Click **Load** to launch Bitwig with the framework enabled.
4. In Bitwig, search for the device by name. Place Chord Arp before an instrument and OTT on an audio or instrument track.

## Devices

| Device | Type | What it does |
| --- | --- | --- |
| [Chord Arp](devices/Chord%20Arp.bwdevice) | Note FX | Turns held chords into tempo-synced arpeggios with a 16-step note-rank pattern. |
| [OTT](devices/OTT.bwdevice) | Audio FX | Uses three-band upward and downward compression to lift quiet details and control peaks. |

**Chord Arp panel preview**

![Chord Arp panel with a 16-step rank matrix](previews/chord-arp.png)

**OTT panel screenshot**

![OTT panel with three-band compressor controls and meters](previews/ott.png)

## Compatibility and updates

Both downloads registered through Custom Nitro Registration `1.2.0-dev.5` in Bitwig Studio **6.1.3 on Windows x64**. A saved project containing both reopened and reached engine ready. That session logged Nitro input warnings and an engine error at shutdown. Audio playback, macOS, Linux and other Bitwig versions are unverified for these files through Patchbay.

This folder includes Chord Arp revision 1. A later revision changed how loop endpoints are stored and failed to reopen a revision 1 project. Keep a copy of the `.bwdevice` files used by your saved projects before updating. Store backups outside the scanned folders, keep one file per device in the scan, and relaunch Bitwig through Patchbay after replacing a file.
