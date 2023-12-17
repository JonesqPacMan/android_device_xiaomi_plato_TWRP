### TWRP device tree for Xiaomi 12T (plato)

=========================================

The Xiaomi 12T (codenamed _"plato"_) is a high-end, mid-range smartphone from Xiaomi.

It was released in October 2022.

## Device specifications

Basic   | Spec Sheet
-------:|:-------------------------
CPU     | Octa-core CPU with 4x Arm Cortex-A78 up to 2.85GHz
Chipset | Mediatek Dimensity 8100
GPU     | Mali-G610 MC6
Memory  | 8 GB RAM (LPDDR5 6400Mbps)
Shipped Android Version | 12
Storage | 128/256 GB (UFS 3.1)
Battery | Li-Po 5000 mAh, non-removable
Display | 1220 x 2712 pixels, 6.67 inches, 60/120hz

![Xiaomi 12T](https://i02.appmifile.com/898_operator_sg/26/08/2022/fc94660da1d6dd006f7589327bb72813.png)

## Features

Works:

- [X] ADB
- [X] Decryption (Android 13)
- [X] Display
- [X] Fasbootd
- [X] Flashing
- [X] MTP
- [X] Sideload
- [X] USB OTG
- [X] Vibrator

## Compile

First checkout minimal twrp with aosp tree:

```
repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1
repo sync -j$(nproc --all)
```

Then add these projects to .repo/manifest.xml:

```xml
<project path="device/xiaomi/plato" name="JonesqPacMan/android_device_xiaomi_plato_TWRP" remote="github" revision="TWRP-12.1_A13" />
```

Finally execute these:

```
source build/envsetup.sh
repopick <needed patch>
lunch twrp_plato-eng
mka vendorbootimage -j$(nproc --all)
```
## To use it:

```
fastboot flash vendor_boot twrp-3.7.0-12.1_A13-vendor_boot-plato.img
```
