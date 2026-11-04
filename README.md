<img src="docs/logo.svg" alt="CNE" width="56" align="right">

# StemDock 0.9 (BETA)

Free helper tool for the **Pioneer CDJ-2000NXS**.

- Builds an **update file** with the stem mod from **your own** original firmware 1.44.
- Prepares your **USB stick**: **4 layers** per track (Vocal, Melody, Bass, Drums).
- Runs **locally**, nothing is uploaded.

> **BETA, at your own risk:** flashing can **damage** the player. Not everything is tested on real hardware. **Keep your original 1.44 file.**

## What you need

- **Mac** with Apple chip (Windows untested)
- Your **original 1.44 file** (`C2KNXS.UPD` or `C2KNXSM.UPD`) from Pioneer
- **FAT32** USB stick
- **rekordbox** export (folder `PIONEER/rekordbox`)
- Only for separating: **Python 3.10 to 3.12** and internet (once)

## Install (macOS)

- Put `StemDock.app` into **Applications**.
- The app is **not notarized**: first start via **right-click > Open > Open**.
- Alternatively: **System Settings > Privacy & Security > Open Anyway**.
- Confirm the **notice** on first start.

The **?** on every card shows a short help.

## 1. Firmware: create the update file

![Firmware flow](docs/flow-firmware.svg)

![Choose original](docs/screenshots/firmware-1-pick.png)

1. **Choose Original**: your 1.44 file.
2. **Check result**: StemDock rejects wrong or already modified files.
3. Tick the box, **Create Update File** (about 15 s).

![Short help](docs/screenshots/firmware-2-help.png)

1. **?** opens the short help (also by keyboard).
2. It contains **flashing** and **way back**.

![Done](docs/screenshots/firmware-3-done.png)

1. The file is named **`C2KNXSM.UPD`**.
2. The flashing steps are shown in the app.

**Flashing:**

- **Order:** hold **USB + RELOOP/EXIT** while switching on the CDJ-2000NXS
- Wait for the message **"Connect the USB storage device"**, **then** plug in the stick
- Wait, **do not switch off**, power must not be lost
- **Stick:** empty or the **rekordbox stick**, always **FAT32**; file in the root folder
- **Back to the original firmware including GUI:** hold **USB STOP + USB + RELOOP/EXIT** while switching on.

**Way back:**

- The mod sets the version number from **1.44 to 1.43**.
- So you can **switch back to the original firmware 1.44 at any time**: same method, your original file.

## 2. Split tracks into 4 layers (PREP)

![Stems flow](docs/flow-stems.svg)

![Stick and tracks](docs/screenshots/stems-1-stick.png)

1. **Choose stick or export**.
2. Choose a **playlist**.
3. Tick **tracks** (already split ones are marked).

![Method](docs/screenshots/stems-2-method.png)

1. **Separate with StemDock**: needs the add-on package (see Settings).
2. **Use my own layer files**: 4 files per track, StemDock matches and checks them.

![Separate](docs/screenshots/stems-3-separate.png)

1. **Separate**: one track after another, **Cancel** at any time.

![Write](docs/screenshots/stems-4-write.png)

1. **Write to the stick**: music and export stay **unchanged**, `exstem.pdb` is kept as `.bak`.

- Tracks with layers are in the playlist folder **STEMS**.
- **Remove** deletes only the layers of one track.
- **Space:** about **53 MB per minute** of music on the stick (measured: 270 MB for 5:06).

## 3. Settings

![General and add-on](docs/screenshots/settings-1-general.png)

1. **Appearance:** System, Light or Dark.
2. **Language:** Deutsch or English.
3. **Add-on package:** installs Demucs for separating (**about 0.8 GB** + model **about 86 MB**), only after confirmation, **Remove** deletes it again. Code: MIT, licence of the model weights **not clearly settled**, please check it yourself.

![Single layers](docs/screenshots/settings-2-single-layers.png)

1. **Also save single layers:** saves the 4 layers as WAV for listening (default **off**, never onto the stick).
2. **Choose target folder:** where the WAV files go.

![Info and updates](docs/screenshots/settings-3-info.png)

1. **Manual on GitHub:** opens this page.
2. **Check for updates at start:** default **off**.
3. **Check for updates:** only asks **github.com** for the latest version (betas included), downloads nothing.
4. **Version** of the app.

## On the player

- **Loop Mode 3x:** control layers via **faders**.
- **Loop Mode 2x (pads):** **work in progress**.

## Known limits

- **BETA**, not everything tested on hardware
- Always exactly **4 layers** per track
- Separating needs the add-on package, Python 3.10 to 3.12 and time
- Windows untested, app only ad-hoc signed

## Thanks

- **Demucs** and Alexandre Défossez: https://github.com/adefossez/demucs
- Emulators: [CDJ-2000 Emulator](https://github.com/cdj2k-revival/cdj2000-emulator) (cdj2k-revival), [cdj-nxs2-qemu](https://github.com/Stijn-Jacobs/cdj-nxs2-qemu) (Stijn-Jacobs)

## Donation and contact

- StemDock is free, its development was not (lots of paid AI tokens): [donate on Ko-fi](https://ko-fi.com/cne_dj)
- Contact: http://cne-dj.com · http://cne-lab.de

## Disclaimer

- Hobby project, **at your own risk**, no warranty, no promise of support
- Private, non-commercial use only
- Independent, **not affiliated** with Pioneer DJ or AlphaTheta

---

[LICENSE.txt](LICENSE.txt) · [THIRD-PARTY.md](THIRD-PARTY.md) · [CHANGELOG.md](CHANGELOG.md)
