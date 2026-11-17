# Patchbay Launcher packaging manifest

Publishing rules for Bitwig mods and native Bitwig devices. The launcher
behavior described here was verified against [Patchbay Launcher 0.9.1][launcher].

- [Mods](#mods)
- [Devices, modulators and Grid modules](#devices-modulators-and-grid-modules)
- [Device catalog descriptions](#device-catalog-descriptions)
- [Device preview images](#device-preview-images)
- [Add a fork or another source](#add-a-fork-or-another-source)

## Mods

1. Keep the source manifest at `<mod-id>/mod.json` on the default branch. Use
   the same stable ID for the directory and `mod.id`. The launcher can read
   this manifest for the display name, author, description and requirements.
2. Build one ZIP per mod. The ZIP must have exactly one top-level directory
   named for `mod.id`. Put `mod.json`, the built helper JAR and the mod's
   resources in that directory. The launcher reads this manifest on install.
3. Name the asset `<mod-id>-<version>.zip` using the exact `mod.version` from
   the packaged manifest. Use `major.minor.patch` with an optional suffix
   such as `-dev.9`. Launcher 0.9.1 accepts letters, digits and dots after
   the hyphen. Omit a `v` prefix and `+build` metadata from the asset version.
4. Attach the built ZIP to a published GitHub Release. Prereleases work.
   Multiple mods can share a release because the launcher uses each asset name
   independently of the tag. GitHub's generated **Source code** ZIP lacks the
   built helper.
5. Increase the manifest and asset versions together for each update. The
   launcher keeps the highest asset version per mod ID across enabled sources.
   It offers an update when that version exceeds the installed `mod.version`.

For example, `note-intervals-0.1.0-dev.8.zip` contains
`note-intervals/mod.json` with `mod.id` set to `note-intervals` and
`mod.version` set to `0.1.0-dev.8`.

Launcher 0.9.1 requests one page of 30 GitHub Releases per source. Older
assets can fall out of the catalog as new releases are published.
The launcher chooses a single ZIP per mod ID based on version, irrespective
of the Bitwig version, OS and architecture in `built_against`. Publish one
asset per mod version and document its compatibility.

Declare dependencies in the manifest's `requires` list. The launcher can
queue missing dependencies available in the catalog and reports ones it
cannot find. Verify the required frameworks and versions in Patchbay.

## Devices, modulators and Grid modules

1. Commit the downloadable binary directly under a top-level
   `Bitwig-<version>/` directory on the default branch. Use the lowercase
   extension `.bwdevice`, `.bwmodulator` or `.bwmodule` for that file type.
   The launcher discovers these files in the repository tree and downloads
   each file individually.
2. Include every compatible file offered for that build. Once the launcher
   finds supported files in a repository's top-level `Bitwig-*` directories,
   it skips files outside them. It shows one selected build at a time and
   does not fill gaps from older builds.
3. Use unique filenames within a build. The launcher stores downloads in a
   local directory per repository and build. Keep the path stable for
   in-place updates. The launcher compares the local Git blob hash to the
   hash in the repository tree to detect changed bytes.
4. Preserve the device UUID across compatible variants. Document the supported
   Bitwig versions and update the download links. Register only the matching
   build in Patchbay and enable **Framework: Nitro Devices**.
5. Add or update the [catalog description](#device-catalog-descriptions) and
   [device preview image](#device-preview-images). Verify both before pushing.

Example paths include `Bitwig-6.1.3-6.1.4/Chord Arp.bwdevice`,
`Bitwig-6.1.7/Chord Arp.bwdevice` and
`Bitwig-6.1.7/Gesture Loop.bwmodulator`.

### Build selection

The launcher reads the first version number in each folder name. It selects
the newest starting version at or below the detected Bitwig version. A name
like `Bitwig-6.1.3-6.1.4` starts at 6.1.3, so the launcher also selects it
for 6.1.6 when the next build starts at 6.1.7. Check the documented
compatibility for the selected build. The launcher selects the oldest build
if the detected version is below all available builds, or the newest build
if version detection fails. Users can choose a build manually.

## Device catalog descriptions

The launcher reads types and descriptions only from single-line table rows
in the repository's root `README.md`. It matches the linked display name
exactly to the artifact filename without its extension. Use at least four
columns, with the linked name, type and description as the first three:

```markdown
| Module | Type | What it does | Panel |
| --- | --- | --- | --- |
| [Audio Buffer](Bitwig-6.1.7/Audio%20Buffer.bwmodule) | Grid module | Records stereo audio with variable-rate playback and loop regions. | [Preview](previews/audio-buffer.png) |
```

This applies equally to `.bwdevice`, `.bwmodulator` and `.bwmodule` files.
Builds sharing a filename share one metadata row. Prose sections, workspace
manifests and version-folder READMEs do not supply launcher descriptions.
Without a matching row, the file still appears with a fallback type and an
empty description. A successful build or offline DSP gate does not validate
this public catalog metadata.

Before publication, check every artifact in every `Bitwig-*` build against
the root README table and its derived preview path. For Polarity's collection,
the private `bitwig.devices` checkout owns `scripts/distribution_catalog.py`
and its local pre-push guard; see that checkout's export workflow. Install the
guard separately on each publishing checkout. It checks the pushed commit,
so an uncommitted README correction cannot hide missing published metadata.
It is a local guard, not GitHub branch protection.

## Device preview images

Commit a PNG to the top-level `previews/` directory on the default branch
of the same repository as the device. The launcher takes the artifact's
filename without the directory or extension, converts it to lowercase,
replaces each space with a hyphen, and appends `.png`. Existing punctuation
stays as written.

| Artifact filename | Preview path |
| --- | --- |
| `Chord Arp.bwdevice` | `previews/chord-arp.png` |
| `Multiband FX-4.bwdevice` | `previews/multiband-fx-4.png` |
| `Gesture Loop.bwmodulator` | `previews/gesture-loop.png` |

Builds with the same filename share one preview. The launcher derives the path
from the filename, independently of the README's image links. It preserves
the aspect ratio and scales larger images down to fit within 282 × 280 pixels
in the details pane. Smaller images stay at their original size. Devices with
missing or unreadable previews still appear in the catalog.

## Add a fork or another source

In **Sources → Add source**, enter the GitHub repository as `owner/repo`.

- For **Mods**, publish the built ZIPs as assets in the fork and use `*.zip`
  as the source's file filter. Refresh **Mods** and check the ID and version.
  Disable the original source when testing a fork that shares a mod ID.
  For an independently installable fork, use its own ID consistently in the
  source directory, manifest, ZIP directory and asset filename.
- For **Devices**, push the artifacts and previews to the fork's default
  branch. Leave the folder filter empty to expose every build or enter a
  repository-relative folder such as `Bitwig-6.1.7`. Refresh **Devices**,
  select the intended build and check the files and previews. Disable the
  original source when testing a fork that shares device UUIDs. The launcher
  adds its selected download folders to Patchbay's Device Folders list.

## Launcher implementation

- Mods use [asset naming and repository metadata][mod-metadata], the
  [release catalog and installed versions][mod-catalog], and
  [ZIP validation and installation][mod-install].
- Devices use [file discovery][device-tree], [build selection][device-builds],
  [download and folder registration][device-downloads],
  [preview naming][preview-path] and [preview loading][preview-loading].

[launcher]: https://github.com/arius77R/patchbay-launcher/tree/v0.9.1
[mod-metadata]: https://github.com/arius77R/patchbay-launcher/blob/v0.9.1/src/Mods.java#L28-L76
[mod-catalog]: https://github.com/arius77R/patchbay-launcher/blob/v0.9.1/src/Mods.java#L235-L315
[mod-install]: https://github.com/arius77R/patchbay-launcher/blob/v0.9.1/src/Mods.java#L331-L468
[device-tree]: https://github.com/arius77R/patchbay-launcher/blob/v0.9.1/src/Devices.java#L40-L130
[device-builds]: https://github.com/arius77R/patchbay-launcher/blob/v0.9.1/src/Devices.java#L133-L155
[device-downloads]: https://github.com/arius77R/patchbay-launcher/blob/v0.9.1/src/Devices.java#L160-L263
[preview-path]: https://github.com/arius77R/patchbay-launcher/blob/v0.9.1/src/Devices.java#L32-L36
[preview-loading]: https://github.com/arius77R/patchbay-launcher/blob/v0.9.1/src/Devices.java#L512-L547
