# Bitwig Studio 6.1.3 and 6.1.4

This folder contains uncompressed Nitro builds for Bitwig Studio 6.1.3 and
6.1.4. The Nitro reader checks passed on both versions. Full device
compatibility in 6.1.4 still needs a host test.

Select this folder in Patchbay under **Tools → Device Folders**. See the
[installation guide](../README.md#install) before switching between builds.

| Name | Type |
| --- | --- |
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

Stutter revision 10 passed the Windows 6.1.3 offline gate. The Windows
6.1.4 compiler produced the same Nitro AST, and both versions' readers
accepted the embedded payload. Revision 10 still needs a live host test.
