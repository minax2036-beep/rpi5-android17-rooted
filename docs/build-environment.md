# Build environment notes

Fill this in after choosing the actual build host. Do not treat the checklist as a tested recipe yet.

## Host details

- Host OS and version: TBD
- CPU architecture: TBD
- RAM: TBD
- Free disk space: TBD
- Filesystem: TBD
- Android source branch/tag: TBD
- Device configuration repository and revision: TBD
- Kernel source and revision: TBD

## Pre-build checklist

- [ ] Confirm the host OS is supported by the selected AOSP branch.
- [ ] Confirm the required JDK, Python, compiler, and build tools from upstream documentation.
- [ ] Ensure enough free storage for the source tree, build output, and cache.
- [ ] Use a stable network connection for source sync.
- [ ] Record the exact manifest and source revisions.
- [ ] Keep build output and caches outside version control.

## Build log template

For each attempt, record:

- Date:
- Host OS:
- Source manifest/revision:
- Device tree revision:
- Kernel revision:
- Command used:
- Result:
- First meaningful error:
- Output artifact(s):
- SHA-256:
- Notes:

## Important

The correct commands depend on the upstream project and branch. Do not copy build commands from another Android release without verifying them against the selected source tree.
