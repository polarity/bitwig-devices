# Bitwig Studio 6.1.7 and later

This folder contains the compressed Nitro builds for Bitwig Studio 6.1.7
and later. See the [installation guide](../README.md#install) for choosing
and registering the matching build.

| Name | Type |
| --- | --- |
| [Audio Buffer](Audio%20Buffer.bwmodule) | Grid module (tested on Windows x86-64, 6.1.7) |
| [Chord Arp](Chord%20Arp.bwdevice) | Note device |
| [FILAR](FILAR.bwdevice) | Instrument |
| [Gesture Loop](Gesture%20Loop.bwmodulator) | Modulator |
| [Halftime](Halftime.bwdevice) | Audio FX |
| [Key Quantizer](Key%20Quantizer.bwmodulator) | Modulator (Windows x86-64, offline-tested on 6.1.7) |
| [Multiband FX-4](Multiband%20FX-4.bwdevice) | Audio FX |
| [Normalizer](Normalizer.bwdevice) | Audio FX |
| [Orbit](Orbit.bwdevice) | Audio FX |
| [OTT](OTT.bwdevice) | Audio FX |
| [Prism](Prism.bwdevice) | Note device |
| [Rivet](Rivet.bwdevice) | Instrument |
| [SHARD](SHARD.bwdevice) | Audio FX |
| [Sonogram](Sonogram.bwmodule) | Grid module (Windows x86-64, offline-tested on 6.1.7) |
| [Step Sequencer](Step%20Sequencer.bwdevice) | Note device |
| [Stutter](Stutter.bwdevice) | Audio FX |
| [Vectorscope](Vectorscope.bwmodule) | Grid module (Windows x86-64, offline-tested on 6.1.7) |

Sonogram and Vectorscope include English live-help text. Keep their
[resources](resources/) directory beside the module files. For individual
downloads, place the [Sonogram help](resources/Sonogram/resources.properties)
and [Vectorscope help](resources/Vectorscope/resources.properties) in
their respective `resources/<module name>/` folders beside the binaries.

Key Quantizer revision 3 is a Windows **6.1.7** candidate with a native expanded
panel, polyphonic input/output and Global (Project) scale selected by default.
Input zero now centers on the selected tonic. Keep the target frequency on C3
and mapping depth at 60 semitones; the output supplies the tonic offset.
Offline mono/polyphonic DSP, document and panel-expression checks pass. Insert
a new instance after relaunching through Patchbay; live confirmation of this
revision and macOS compatibility are pending.

All 12 devices and the Gesture Loop modulator passed the offline Nitro
reader check with the Bitwig Studio 6.1.7 macOS arm64 toolchain. The Windows
6.1.7 Nitro reader also accepted the exact embedded payload from Stutter
revision 10. Insertion, controls, audio and project recall still need
verification in Bitwig.
