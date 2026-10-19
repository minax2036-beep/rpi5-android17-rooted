# Raspberry Pi 5 — Android 17 Rooted

An experimental project to investigate building and adapting **Android 17 (AOSP) for Raspberry Pi 5**, with a longer-term goal of evaluating recovery and root solutions.

> **Status: planning / bring-up.** This repository is a project scaffold, not a claim that Android 17, TWRP, or KernelSU Next already works on Raspberry Pi 5. Hardware support, boot flow, device trees, kernel compatibility, recovery support, and root integration must be verified independently.

## Goals

- Document a reproducible Android 17 AOSP build environment for Raspberry Pi 5.
- Track device-specific configuration, kernel integration, and build notes.
- Investigate whether a compatible recovery can be built or ported.
- Investigate KernelSU Next compatibility with the selected kernel and Android build.
- Keep scripts and project documentation version-controlled without committing generated build output or proprietary blobs.

## Current status

- [x] Create public project repository.
- [x] Add initial project documentation and ignore rules.
- [ ] Verify the upstream Android 17 source tree and Raspberry Pi 5 device configuration.
- [ ] Record host OS, disk-space, RAM, and package requirements.
- [ ] Complete a baseline build before attempting root or recovery changes.
- [ ] Boot-test the baseline image on Raspberry Pi 5.
- [ ] Evaluate recovery options; TWRP support is **not confirmed**.
- [ ] Evaluate KernelSU Next support for the exact kernel and boot image.

See [the roadmap](docs/roadmap.md) for staged work and [build environment notes](docs/build-environment.md) for the initial checklist.

## Upstream research

These are starting points for research, not guarantees of Android 17 compatibility:

- [Raspberry Vanilla — Raspberry Pi 5 device repository](https://github.com/raspberry-vanilla/android_device_brcm_rpi5)
- [Raspberry Vanilla — kernel manifest, Android 17 branch](https://github.com/raspberry-vanilla/android_kernel_manifest/tree/android-17.0)
- [KonstaKANG — Raspberry Pi 5 Android builds](https://konstakang.com/devices/rpi5/)

Always check the upstream branch, build instructions, license, and last update before using a source tree. Do not assume a build for a different Android version can be reused unchanged.

## Repository layout

```text
.
├── .gitignore
├── README.md
├── docs/
│   ├── build-environment.md
│   └── roadmap.md
├── manifests/
│   └── README.md
└── scripts/
    └── README.md
```

## Safety and integrity notes

- Keep a known-good, restorable OS image and backup before testing experimental builds.
- Never flash an image or recovery unless its target device and partition layout are confirmed.
- Do not publish signing keys, access tokens, private credentials, or personal backup images.
- Root and recovery changes can prevent a device from booting or erase data. Test one change at a time and document the exact source revision.

## License

No license has been selected yet. Until one is added, do not assume others have permission to reuse this repository's original content.
