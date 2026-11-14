# MPC Standalone SDK — Feasibility Checklist

## Current finding

The inMusic Software GitHub organization publishes an official repository named `mpc-plugin-builder-sdk`:

https://github.com/inmusic-software/mpc-plugin-builder-sdk

Its README states that it builds third-party instrument and effect plugins for MPC standalone hardware, including MPC Live III, and requires MPC OS 3.10.1 or later with **Enable Enhancements** and **External Plugin Support** enabled.

The SDK describes plugins as Linux shared libraries using the VST 2.4 binary interface, packaged with a `plugin.json` manifest and optional JSON UI skins. It provides a C++ framework, examples, a host simulator, validation tools, and a build script. The build script fetches the Zig cross-compiler when needed. Python 3.9+, and macOS, Windows, or Linux are listed as requirements.

## Important support caveat

There is conflicting public information. An inMusic support article titled “How To Use 3rd Party VST's With Your MPC” says that installing additional third-party plugins in standalone mode is not possible. The newer inMusic SDK repository says it enables third-party standalone plugins on supported devices.

Therefore, treat the SDK repository as the technical development path, but verify the feature on the actual MPC Live III running OS 3.10.1. Check that the device exposes **Preferences → Enhancements → Enable Enhancements → External Plugin Support**. Do not assume that every general support article has been updated to describe this newer SDK feature.

## Environment status

The current Codespace reports:
- Ubuntu Linux x86-64.
- Python 3.14.2.
- CMake installed.
- GCC 13.3.0.
- Git 2.56.0.

The SDK README requires Python 3.9 or newer and supports Linux. These checks suggest the environment meets the stated basic requirements, but the SDK's own build and validation scripts still need to be run. The SDK downloads its Zig cross-compiler on first build; a separate ARM cross-compiler installation should not be assumed necessary.

## Required next verification

- [ ] Clone the official SDK into the Codespace.
- [ ] Inspect the SDK getting-started instructions and examples.
- [ ] Build the official StereoDelay example using the SDK build script.
- [ ] Confirm the build produces the expected ARM64 artifact for MPC Live III.
- [ ] Run the SDK host simulator and validator.
- [ ] Confirm External Plugin Support is present and enabled on the actual MPC Live III.
- [ ] Install and test the example on hardware before implementing FRACTURE DSP.

## Development constraints

The owner currently has an iPhone available for project management and editing. GitHub repository files can be inspected and edited remotely. Commands that run inside the Codespace terminal still need to be initiated there unless a supported remote execution path is established.

## Decision gate

Do not begin FRACTURE's full DSP implementation until the official SDK example builds and the device can load it. If the example cannot be loaded on the target MPC, stop and resolve the compatibility or firmware issue first.

## Sources

- Official SDK: https://github.com/inmusic-software/mpc-plugin-builder-sdk
- SDK getting started: https://github.com/inmusic-software/mpc-plugin-builder-sdk/blob/main/GETTING_STARTED.md
- inMusic support article (conflicting general guidance): https://support.inmusicstore.com/en/support/solutions/articles/69000876025-akai-mpc-series-how-to-use-3rd-party-vst-s-with-your-mpc
