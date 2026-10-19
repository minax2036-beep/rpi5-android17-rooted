# Project roadmap

This roadmap is a plan, not a statement that any stage has already succeeded.

## Stage 0 — Establish sources and constraints

- [ ] Identify a maintained Android 17 source tree and exact branch/tag.
- [ ] Confirm the Raspberry Pi 5 device configuration supports that Android version.
- [ ] Record upstream repository URLs, commit IDs, licenses, and build instructions.
- [ ] Decide which host OS will be used and estimate required storage.

**Exit condition:** source revisions and a documented build environment are pinned.

## Stage 1 — Build an unmodified baseline

- [ ] Sync the documented source tree.
- [ ] Install required host packages and configure build variables.
- [ ] Run the upstream build command without root/recovery modifications.
- [ ] Record failures, build duration, output artifact names, and checksums.

**Exit condition:** a baseline image builds reproducibly.

## Stage 2 — Boot and validate

- [ ] Verify the image format and boot procedure against Raspberry Pi 5 documentation.
- [ ] Test boot with a spare storage device where possible.
- [ ] Record display, input, networking, audio, USB, and thermal behavior.
- [ ] Keep a known-good recovery path.

**Exit condition:** baseline boot and essential hardware checks are documented.

## Stage 3 — KernelSU Next investigation

- [ ] Identify the exact kernel source, version, configuration, and boot image format.
- [ ] Check KernelSU Next's current supported integration methods.
- [ ] Make changes on a separate branch and preserve the baseline artifacts.
- [ ] Verify root status and basic stability after boot.

**Exit condition:** compatibility is demonstrated on the exact build, or blockers are documented.

## Stage 4 — Recovery investigation

- [ ] Check whether an existing recovery explicitly supports Raspberry Pi 5 and the chosen Android build.
- [ ] If not, research the requirements for a port; do not label an untested image as TWRP.
- [ ] Document partition mapping, boot flow, display/input support, and recovery/restore procedure.
- [ ] Test only with a verified device-specific image and a known-good restore path.

**Exit condition:** support is verified, a port is validated, or the project records that no usable recovery is available.

## Stage 5 — Reproducibility and release

- [ ] Document exact source revisions and commands.
- [ ] Add checksums for published artifacts.
- [ ] Add build/test automation only after the baseline workflow is reliable.
- [ ] Review licenses and distribution requirements for every included component.
