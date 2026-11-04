# Omarchy Pad for the OnePlus Pad 4 (iceland)

The device packages of [Omarchy Pad](https://github.com/samyn92/omarchy-pad) for the OnePlus Pad 4 (codename
iceland, SM8850), as a signed pacman repository: the kernel, the firmware, the sensor hub and the device's own files.
Omarchy Pad's core is device-neutral; each tablet's packages have a repository of their own, and this is the Pad 4's.
The site is the `gh-pages` branch; this branch only describes it.

```
[iceland]
SigLevel = Required DatabaseRequired
Server = https://samyn92.github.io/omarchy-pad-iceland/$repo/stable/$arch
```

The packages and the database are signed with Omarchy Pad's key (`A9EDDCA320FC25A5EC8B7F3790104B1A1337F4A9`), which
comes in `omarchy-pad-keyring` from the `[omarchy-pad]` repository. An Omarchy Pad image for the Pad 4 has both.

## The packages and their sources

| Package | What | Source | Licence |
|---|---|---|---|
| `iceland-device` | the boot chain, the `iceland` initramfs hook, the first boot's growth and provisioning, the battery, thermal, sound and sensor services | the package's files are themselves its source | GPL-2.0-or-later |
| `linux-iceland-bin` | the kernel: mzakamin-hub's prebuilt q90r kernel, repackaged | [mzakamin-hub/iceland-linux](https://github.com/mzakamin-hub/iceland-linux), tag `q90r` (its patch queue on linux-next 20261020) | GPL-2.0-only |
| `iceland-firmware` | the Pad 4's firmware from stock 11.A.38 (DSPs, GPU, video, Wi-Fi and Bluetooth, touch, the sensor registry), no unit-specific data | [mzakamin-hub/iceland-firmware](https://github.com/mzakamin-hub/iceland-firmware), release `11.A.38-6`, repackaged as published there | proprietary (Qualcomm, OnePlus) |
| `hexagonrpc` | the FastRPC daemon for the Hexagon DSPs | [linux-msm/hexagonrpc](https://github.com/linux-msm/hexagonrpc) `598b591`, with the patches in [iceland-mainline](https://github.com/mzakamin-hub/iceland-mainline/tree/5ff7672866bdb7c943d14a69a015090a6e12a31f/docs/sensors/patches/hexagonrpc) | GPL-3.0-or-later |
| `libssc` | the library for the sensor hub (SSC) | [DylanVanAssche/libssc](https://codeberg.org/DylanVanAssche/libssc) `54dd13e` | GPL-3.0-or-later |
| `iio-sensor-proxy-ssc` | iio-sensor-proxy with its SSC backend: rotation and ambient light | [iio-sensor-proxy](https://gitlab.freedesktop.org/hadess/iio-sensor-proxy) 3.9, with the patches in [iceland-mainline](https://github.com/mzakamin-hub/iceland-mainline/tree/5ff7672866bdb7c943d14a69a015090a6e12a31f/docs/sensors/patches/iio-sensor-proxy) | GPL-3.0-or-later |
| `qbootctl` | the A/B slot flags, marked after a good boot | [linux-msm/qbootctl](https://github.com/linux-msm/qbootctl) `39a6e6d` | GPL-3.0-or-later |

Everything here stands on [mzakamin-hub](https://github.com/mzakamin-hub)'s port of mainline Linux to the Pad 4: the
kernel, U-Boot, the firmware and the device bring-up.
