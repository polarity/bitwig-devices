# Polarity Bitwig Devices

This repository distributes finished Bitwig devices, modulators and Grid modules.
Keep source code, development history and test records in the private
`F:/GitHub/bitwig.devices` checkout. Public download pages describe what the
finished module does and link to its build and preview.

Before publishing, run the private checkout's `scripts/distribution_catalog.py`
and install its `--install-pre-push-hook` guard in each publishing checkout.
Every published filename needs a matching root README table row with a type,
description and panel column; prose alone does not populate launcher cards.
See the private checkout's export workflow for commands and hook integration.

| Task | Start here |
| --- | --- |
| Add, update or relocate a downloadable build | Follow the [shared packaging manifest](docs/patchbay-launcher.md#devices-modulators-and-grid-modules) and update the matching download links. |
| Install a build or check the supported Bitwig versions | [Installation guide](README.md#install) |
| Develop or test a Polarity device, modulator or Grid module | `F:/GitHub/bitwig.devices/AGENTS.md` |
| Build your own device | [Bitwig Device Blueprints](https://github.com/polarity/bitwig-devices-blueprint) |

For documentation changes, follow the shared standard at
`F:/GitHub/coding.defaults/documentation-standard.md` when available.

Update the launcher manifest in [bitwig-mods](https://github.com/polarity/bitwig-mods)
first and copy it verbatim to `docs/patchbay-launcher.md` here.
