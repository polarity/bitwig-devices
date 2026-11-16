# Bitwig Studio 6.1.7 and later

This folder contains the compressed Nitro builds for Bitwig Studio 6.1.7
and later. See the [installation guide](../README.md#install) for choosing
and registering the matching build.

| Audio FX | Instruments | Note devices |
| --- | --- | --- |
| [Halftime](Halftime.bwdevice) | [FILAR](FILAR.bwdevice) | [Chord Arp](Chord%20Arp.bwdevice) |
| [Multiband FX-4](Multiband%20FX-4.bwdevice) | [Rivet](Rivet.bwdevice) | [Prism](Prism.bwdevice) |
| [Normalizer](Normalizer.bwdevice) | | [Step Sequencer](Step%20Sequencer.bwdevice) |
| [Orbit](Orbit.bwdevice) | | |
| [OTT](OTT.bwdevice) | | |
| [SHARD](SHARD.bwdevice) | | |
| [Stutter](Stutter.bwdevice) | | |

Modulator: [Gesture Loop](Gesture%20Loop.bwmodulator).

All 12 devices and the Gesture Loop modulator passed the offline Nitro
reader check with the Bitwig Studio 6.1.7 macOS arm64 toolchain. The Windows
6.1.7 Nitro reader also accepted the exact embedded payload from Stutter
revision 10. Insertion, controls, audio and project recall still need
verification in Bitwig.

## Grid modules

[Audio Buffer](Audio%20Buffer.bwmodule) records up to 30 seconds of stereo
audio with variable-rate playback, loop regions and external phase control.
Revision 4 fixes idle noise and distorted playback by processing all four
stereo frames per Grid port. Idle silence, sine capture and loop playback were
verified in monophonic FX Grid on Windows Bitwig Studio 6.1.7 through Patchbay.
Revision 5 adds Bitwig's native top and bottom panel gradients.
Revision 6 fits four Grid cells by two and adds a waveform with loop bounds,
a captured-length strip and record and playback heads. Phase switches to
external control when connected. The recorded stereo peaks shape abstract
strands across the gray background. Revision 10 smooths shape changes during
capture and animates the strands at a speed proportional to Rate during
playback. It passed the offline gate. Host animation cadence and project recall
still need a host check.

For a first take, wire `Button → Record` and `Button → NOT → Play`. Leave
**Rate** and **Phase** unpatched. Turn the Button on to record, then off to
play.

![Offline Audio Buffer panel preview](../previews/audio-buffer.png)
