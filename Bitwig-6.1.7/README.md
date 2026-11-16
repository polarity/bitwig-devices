# Bitwig Studio 6.1.7 and later

This folder contains the compressed Nitro builds for Bitwig Studio 6.1.7
and later. See the [installation guide](../README.md#install) for choosing
and registering the matching build.

| Name | Type |
| --- | --- |
| [Audio Buffer](Audio%20Buffer.bwmodule) | Grid module |
| [Chord Arp](Chord%20Arp.bwdevice) | Note device |
| [FILAR](FILAR.bwdevice) | Instrument |
| [Gesture Loop](Gesture%20Loop.bwmodulator) | Modulator |
| [Halftime](Halftime.bwdevice) | Audio FX |
| [Multiband FX-4](Multiband%20FX-4.bwdevice) | Audio FX |
| [Normalizer](Normalizer.bwdevice) | Audio FX |
| [Orbit](Orbit.bwdevice) | Audio FX |
| [OTT](OTT.bwdevice) | Audio FX |
| [Prism](Prism.bwdevice) | Note device |
| [Rivet](Rivet.bwdevice) | Instrument |
| [SHARD](SHARD.bwdevice) | Audio FX |
| [Step Sequencer](Step%20Sequencer.bwdevice) | Note device |
| [Stutter](Stutter.bwdevice) | Audio FX |

All 12 devices and the Gesture Loop modulator passed the offline Nitro
reader check with the Bitwig Studio 6.1.7 macOS arm64 toolchain. The Windows
6.1.7 Nitro reader also accepted the exact embedded payload from Stutter
revision 10. Insertion, controls, audio and project recall still need
verification in Bitwig.
