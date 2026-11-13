# Polarity Bitwig Devices

Native Bitwig Studio devices and modulators by [Polarity](https://polarity.me/), loaded through [Patchbay Mod Loader](https://github.com/shaboogen-dev/Patchbay).

## Install

1. Download the [Patchbay Mod Loader release](https://github.com/shaboogen-dev/Patchbay/releases/tag/0.36.0-dev.9%2Bbitwig-6.1.7) and follow `INSTALL.md` in the ZIP. This release supports Bitwig Studio 6.1.3 and includes **Custom Nitro Registration** `1.2.0-dev.5`.
2. Open a file below and choose **Download raw file**. To get the collection, use **Code → Download ZIP** and extract it to a folder of your choice.
3. Close Bitwig. In Patchbay, enable **Framework: Custom Nitro Registration**, open **Tools → Device Folders**, and add the extracted collection folder or the folder containing your downloads. Patchbay also scans its subfolders. Click **Load** to launch Bitwig.
4. Find devices by name in Bitwig's device browser. Add Gesture Loop from a device's modulator panel. Place Chord Arp, Prism and Step Sequencer before an instrument.

## Devices

| Device | Type | What it does | Panel |
| --- | --- | --- | --- |
| [Chord Arp](devices/Chord%20Arp.bwdevice) | Note FX | Turn held chords into song-synced arpeggios with a 16-step rank matrix, bounded randomization, and velocity scaling. | [Preview](previews/chord-arp.png) |
| [FILAR](devices/FILAR.bwdevice) | Instrument | An additive synthesizer with 32 editable sine partials, per-partial attack and decay, and 32 generated upper partials. | [Preview](previews/filar.png) |
| [Halftime](devices/Halftime.bwdevice) | Audio FX | Captures tempo-synced audio loops and changes their tape speed for half-time, pitch-shift and stutter effects. | [Preview](previews/halftime.png) |
| [Multiband FX-4](devices/Multiband%20FX-4.bwdevice) | Audio FX | Splits audio into four adjustable bands, each with its own device chain, and shows the band spectra. Optional linear-phase crossover. | [Preview](previews/multiband-fx-4.png) |
| [Normalizer](devices/Normalizer.bwdevice) | Audio FX | Measures short-term loudness and applies one-shot gain correction to a LUFS target, with an optional hard clipper. | [Preview](previews/normalizer.png) |
| [Orbit](devices/Orbit.bwdevice) | Audio FX | Turns audio or internal strikes into ringing textures with modal, sympathetic-string and nonlinear-string resonators. | [Screenshot](previews/orbit.png) |
| [OTT](devices/OTT.bwdevice) | Audio FX | Three-band upward and downward compression that lifts quiet details and controls peaks for a dense, bright sound. | [Screenshot](previews/ott.png) |
| [Prism](devices/Prism.bwdevice) | Note generator | Generates tempo-synced melodies from weighted scale degrees, with looping patterns, rests, swing and motif variation. Place an instrument after it. | [Screenshot](previews/prism.png) |
| [Rivet](devices/Rivet.bwdevice) | Instrument | A monophonic synthesizer with three oscillators, a driven mixer, ladder filter, envelopes, noise and feedback. | [Preview](previews/rivet.png) |
| [SHARD](devices/SHARD.bwdevice) | Audio FX | Shapes audio with 3 to 63 logarithmically spaced spectral gain bands, from broad tonal changes to detailed sculpting. | [Preview](previews/shard.png) |
| [Step Sequencer](devices/Step%20Sequencer.bwdevice) | Note generator | A tempo-synced 16-step note sequencer with per-step gate, velocity, pressure and note rows. Place an instrument after it. | [Preview](previews/step-sequencer.png) |
| [SVF Lab](devices/SVF%20Lab.bwdevice) | Audio FX | A stereo filter research device with low-pass, band-pass and high-pass modes. | — |

## Modulators

[Download Gesture Loop](modulators/Gesture%20Loop.bwmodulator) to record a macro movement and repeat it as a free-running modulation loop. Captured gestures are cleared when you reopen the project.

![Gesture Loop panel from an earlier build](previews/gesture-loop.png)

## Grid modules

[Grid modules](grid-modules/README.md) has the current download status.

## Device gallery

### Chord Arp

![Chord Arp panel showing the 16-step note-rank matrix](previews/chord-arp.png)

### FILAR

![FILAR panel showing the additive synthesizer partial editor](previews/filar.png)

### Halftime

![Halftime panel showing the tempo-synced loop and tape-speed controls](previews/halftime.png)

### Multiband FX-4

![Multiband FX-4 panel showing the four band chains, spectra and crossover controls](previews/fx-4.png)

### Multiband FX-4 preview

![Multiband FX-4 preview panel showing the four-band container panel preview](previews/multiband-fx-4.png)

### Normalizer

![Normalizer panel showing the loudness measurement and gain correction controls](previews/normalizer.png)

### Orbit

![Orbit panel showing the resonator controls](previews/orbit.png)

### OTT

![OTT panel showing the three-band compressor controls and meters](previews/ott.png)

### Prism

![Prism panel showing the weighted melody generator controls](previews/prism.png)

### Rivet

![Rivet panel showing the monophonic synthesizer controls](previews/rivet.png)

### SHARD

![SHARD panel showing the spectral gain controls](previews/shard.png)

### Step Sequencer

![Step Sequencer panel showing the 16-step note sequencer panel](previews/step-sequencer.png)

## Compatibility and updates

All 12 device files passed their Windows x64 Bitwig Studio **6.1.3** offline build checks. The **Custom Nitro Registration** `1.2.0-dev.5` folder scanner also found all 12 and read distinct UUIDs using Bitwig 6.1.3's document reader. This test ran outside the Bitwig application. Live insertion, audio and project recall are still unverified for most of these exact builds. The current OTT file also loaded in a saved project through Patchbay on Windows 6.1.3. Gesture Loop passed its offline build checks, and the same scanner recognized it as a modulator. The panel was tested in Bitwig 6.1.3 through Extension Manager. Live loading through Patchbay is unverified for this file. macOS, Linux and other Bitwig versions are unverified for this collection.

The current **Chord Arp** is revision 4. Its loop endpoints use a different saved-value type from revision 1. A project saved with revision 1 failed to reopen with revision 4. For a project saved with revision 1, use its matching file from your backup or this repository's first commit. Keep a copy of the files used by your saved projects outside the scanned folders, and relaunch Bitwig through Patchbay after replacing a file.
