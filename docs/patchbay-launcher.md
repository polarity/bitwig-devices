# Patchbay Launcher packaging for devices

This is the publishing contract for this repository. The discovery and update
behavior below was verified against [Patchbay Launcher 0.9.1][launcher].
The launcher catalogs files from the default branch of enabled GitHub sources.
This document is for maintainers and fork authors.

## Publish a device build

1. Commit the downloadable binary directly under a top-level
   `Bitwig-<version>/` directory. Use the lowercase extension `.bwdevice`,
   `.bwmodulator` or `.bwmodule` for the corresponding file type. The
   launcher downloads these files individually from the repository.
2. Put every file offered for a given build in that build's directory. Include
   the compatible files users should continue to see when adding a new build
   directory. The launcher displays one selected build at a time and does not
   fill gaps from older builds. Within each repository, once it finds supported
   files in a top-level `Bitwig-*` directory, it ignores supported files outside
   those directories.
3. Keep the file's name and path stable when updating it in place. The launcher
   compares the downloaded file's Git blob hash to the hash in the GitHub tree.
   When the contents change at the same path, it shows an update. Use unique
   filenames within each build because the launcher downloads into a single
   local directory for that repository and build.
4. Check the [supported Bitwig builds](../README.md#install), preserve the
   device UUID across compatible variants, and update the corresponding
   download links. For manual setup, register only the matching build folder
   in Patchbay's **Tools → Device Folders**.

Examples of paths in this repository:

~~~text
Bitwig-6.1.3-6.1.4/Chord Arp.bwdevice
Bitwig-6.1.7/Chord Arp.bwdevice
Bitwig-6.1.7/Gesture Loop.bwmodulator
~~~

The original [Gesture Loop for 6.1.3 and 6.1.4][legacy-gesture-loop] is a
manual download at its legacy path. Launcher 0.9.1 omits it from the catalog.
A launcher-discoverable build for those versions belongs at
`Bitwig-6.1.3-6.1.4/Gesture Loop.bwmodulator`.

## How the build is selected

On first load, the launcher selects the build with the newest starting version
at or below the detected Bitwig version. It reads the first version number in
the folder name. For example, a detected 6.1.6 selects
`Bitwig-6.1.3-6.1.4` with this repository's current folders, even though that
build is documented for 6.1.3 and 6.1.4. For a detected version below all builds
the launcher chooses the oldest build. If detection fails, it chooses the newest.
Users can choose a build manually. The [installation guide](../README.md#install)
states which builds this repository supports.

## Add a fork or a separate device repository

Push the artifacts to the fork's default branch. In the launcher, open
**Sources → Add source**, choose **Devices**, and enter `owner/repo`.
Leave the folder filter empty to expose all builds. Use a repository-relative
folder such as `Bitwig-6.1.7` to expose only that build.

Refresh **Devices**, select the intended build and check that the expected
files appear. Disable the original source when testing a fork that distributes
the same device UUIDs. The launcher adds its selected downloads to Patchbay's
Device Folders list. Enable **Framework: Nitro Devices** in Patchbay to load
the files.

Implementation references: [file discovery][tree], [build selection][builds],
and [download and folder registration][downloads].

[launcher]: https://github.com/arius77R/patchbay-launcher/tree/v0.9.1
[tree]: https://github.com/arius77R/patchbay-launcher/blob/v0.9.1/src/Devices.java#L40-L130
[builds]: https://github.com/arius77R/patchbay-launcher/blob/v0.9.1/src/Devices.java#L133-L155
[downloads]: https://github.com/arius77R/patchbay-launcher/blob/v0.9.1/src/Devices.java#L160-L263
[legacy-gesture-loop]: ../modulators/Gesture%20Loop.bwmodulator
