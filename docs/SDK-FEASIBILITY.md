# MPC Standalone SDK — Feasibility Checklist

## Why this document exists

A plugin that runs as a desktop VST does not automatically run inside an MPC in standalone mode. FRACTURE must use the plugin format and SDK explicitly supported by the target MPC firmware.

## Required verification

Do not begin platform-specific implementation until these questions are answered from official documentation or a working official example.

- [ ] Is a third-party standalone effect plugin SDK publicly available?
- [ ] Does it explicitly support MPC Live III?
- [ ] Does it support MPC OS 3.10.1?
- [ ] What operating system / CPU architecture is the plugin built for?
- [ ] Which compiler, SDK version, and build tools are required?
- [ ] What audio callback and buffer interfaces are provided?
- [ ] Is host tempo and transport information exposed?
- [ ] How are plugin parameters declared and automated?
- [ ] What UI framework and controls are supported?
- [ ] How are presets and plugin state saved?
- [ ] How is the plugin packaged, installed, and loaded on the MPC?

## Development constraints

The owner currently has an iPhone available for project management and editing. The iPhone can be used to review documents and make simple repository edits, but it should not be assumed to provide the native toolchain required to compile and validate an MPC plugin.

A compatible desktop or remote build environment may be needed once the official toolchain is known.

## Decision gate

If no official third-party standalone plugin SDK exists for the target MPC firmware, pause native plugin implementation. Investigate supported alternatives before investing in a desktop VST or another format that the MPC cannot load standalone.
