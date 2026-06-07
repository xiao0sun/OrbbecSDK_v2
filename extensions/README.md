
# Orbbec SDK Extensions

This directory contains the binaries file for the Orbbec SDK extensions. The extensions are developed by the Orbbec SDK team or partners and are not open source. The extensions are under the MIT license, feel free to use them in your projects.

- filters： Contains the private filters library for the Orbbec SDK.
- frameprocessor： Contains the private frame processor library for the Orbbec SDK.
- firmwareupdater： Contains the private firmware updater library for the Orbbec SDK.
- depthengine： Contains the private depth engine library for the Orbbec SDK of the Femto Bolt device.

## macOS Femto Bolt depth engine

`depthengine/macOS/libdepthengine.dylib` is an experimental, unofficial macOS depth engine for Femto Bolt. It is included so this fork can exercise the macOS Femto Bolt depth pipeline end to end.

This binary is built for macOS arm64 and currently supports Apple Silicon Macs only.

This binary is not an official Orbbec depth engine, and its output quality, accuracy, and compatibility should not be treated as equivalent to the official Windows or Linux depth engine binaries.

# license

The license for those files can be found in license.txt in extensions directory.
