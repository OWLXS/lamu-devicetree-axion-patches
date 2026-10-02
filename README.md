# lamu-devicetree-axion-patches

AxionOS-specific device tree patches for `motorola/lamu`, kept out of the
base device tree repos so those stay clean enough to build any ROM.

Base repos (clean, structural-only):
- [OWLXS/android_device_motorola_lamu](https://github.com/OWLXS/android_device_motorola_lamu) — apply `lamu/*.patch` on top of commit `863481d`
- [OWLXS/android_device_motorola_mt6768-common](https://github.com/OWLXS/android_device_motorola_mt6768-common) — apply `mt6768-common/*.patch` on top of commit `d6838c4`

## Apply

```bash
cd device/motorola/lamu && git am /path/to/lamu-devicetree-axion-patches/lamu/*.patch
cd device/motorola/mt6768-common && git am /path/to/lamu-devicetree-axion-patches/mt6768-common/*.patch
```

Also requires `device/axion/common` in the manifest (BoardConfigAxion.mk +
defaults_common.mk) and `packages/apps/AxionFx` for the audio effect to do
anything.

## Contents

- `lamu/0001-*.patch` — AXION_MAINTAINER/PROCESSOR/CAMERA_*_INFO identity,
  `defaults_common.mk` inherit
- `lamu/0002-*.patch` — `BoardConfigAxion.mk` include
- `mt6768-common/0001-*.patch` — Axion Kernel Manager GPU range-limiter
  (chown+sepolicy), AxDiagnostics GPU tab support, AxionFx effect library
  registration, window blur enable, AxMemoryManager per-app swappiness
  sepolicy
