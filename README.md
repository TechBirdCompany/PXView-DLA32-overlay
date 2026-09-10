# PXView DLA32 Overlay

Minimal integration overlay for the FNIRSI DLA-32 captured USB protocol.

This repository does not fork PXView or the DLA32 project. It pins the upstream
repositories and stores only the patches needed to apply the integration.

## Upstreams

- PXView: https://github.com/PXLogic/PXView.git
- DLA32 protocol evidence: https://github.com/TechBirdCompany/sigrok-fnirsi-dla32.git

The DLA32 capture archive is kept outside this overlay because it is evidence,
not a runtime dependency. The driver uses the captured USB identity and command
sequence documented by that project.

## Apply

From a directory containing a PXView checkout:

```sh
./apply.sh /path/to/PXView
```

The script checks the pinned PXView and vendored libsigrok revisions, applies the
Linux build-script patch, and adds the libsigrok DLA32 driver.

## Build

```sh
cd /path/to/PXView
./build_linux.sh --no-deps
```

The current implementation supports the captured 32-channel, 50 MHz path and
forwards the captured stream as raw cross-channel logic data. Sample unpacking
and additional configuration modes remain intentionally unclaimed until the
capture evidence proves them.

## Pinned revisions

- PXView: `59263ff70602e40dc2f3e659b0b434aab30dd500`
- vendored libsigrok: `34362ac9120dbe124e74b1a8c0efd6611b9ecff1`
- DLA32 evidence: `cd4252ffe0bde8e1b49e83a4dfffcddf96c549ff`
