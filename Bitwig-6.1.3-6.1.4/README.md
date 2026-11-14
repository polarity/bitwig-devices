# Bitwig Studio 6.1.3 and 6.1.4

This folder contains uncompressed Nitro builds for Bitwig Studio 6.1.3 and
6.1.4. The Nitro reader checks passed on both versions. Full device
compatibility in 6.1.4 still needs a host test.

Select this folder in Patchbay under **Tools → Device Folders**. See the
[installation guide](../README.md#install) before switching between builds.

| Audio FX | Instruments | Note devices |
| --- | --- | --- |
| [Halftime](Halftime.bwdevice) | [FILAR](FILAR.bwdevice) | [Chord Arp](Chord%20Arp.bwdevice) |
| [Multiband FX-4](Multiband%20FX-4.bwdevice) | [Rivet](Rivet.bwdevice) | [Prism](Prism.bwdevice) |
| [Normalizer](Normalizer.bwdevice) | | [Step Sequencer](Step%20Sequencer.bwdevice) |
| [Orbit](Orbit.bwdevice) | | |
| [OTT](OTT.bwdevice) | | |
| [SHARD](SHARD.bwdevice) | | |
| [Stutter](Stutter.bwdevice) | | |

The original [Gesture Loop modulator](../modulators/Gesture%20Loop.bwmodulator)
is available separately.

Stutter revision 10 passed the Windows 6.1.3 offline gate. The Windows
6.1.4 compiler produced the same Nitro AST, and both versions' readers
accepted the embedded payload. Revision 10 still needs a live host test.
