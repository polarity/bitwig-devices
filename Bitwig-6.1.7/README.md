# Bitwig Studio 6.1.7

This folder contains macOS arm64 test builds for Bitwig Studio 6.1.7.
All 11 devices and the Gesture Loop modulator passed the offline Nitro
reader check. Insertion, controls, audio and project recall still need
verification in Bitwig.

| Audio FX | Instruments | Note devices |
| --- | --- | --- |
| [Halftime](Halftime.bwdevice) | [FILAR](FILAR.bwdevice) | [Chord Arp](Chord%20Arp.bwdevice) |
| [Multiband FX-4](Multiband%20FX-4.bwdevice) | [Rivet](Rivet.bwdevice) | [Prism](Prism.bwdevice) |
| [Normalizer](Normalizer.bwdevice) | | [Step Sequencer](Step%20Sequencer.bwdevice) |
| [Orbit](Orbit.bwdevice) | | |
| [OTT](OTT.bwdevice) | | |
| [SHARD](SHARD.bwdevice) | | |

Modulator: [Gesture Loop](Gesture%20Loop.bwmodulator).

Select this folder in Patchbay under **Tools → Device Folders**. Patchbay
scans subfolders recursively, so select only this folder for the test.
