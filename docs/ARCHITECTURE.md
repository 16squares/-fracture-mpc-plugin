# FRACTURE — Architecture

## 1. Product behavior

FRACTURE is designed around one effect engine with two simultaneous control sources:

- **Sequencer:** sends time-based parameter targets on selected steps.
- **Performance controls:** manipulate selected parameters live while the sequencer continues.

Both systems remain active at the same time.

## 2. Proposed signal flow

`Audio input → input stage → effect processing → dry/wet mix → output protection → audio output`

The sequencer and performance controls feed parameter targets into the effect engine. The exact implementation must follow the official MPC SDK once its interfaces are verified.

## 3. Effect modules

| Module | Proposed controls |
|---|---|
| STUTTER | Repeat rate, gate, slice size |
| REVERSE | Slice length, direction, wet mix |
| CRUSH | Bit depth, sample rate, drive |
| ECHO | Time, feedback, filter, mix |
| SPACE | Size, decay, damping, mix |
| WARP | Pitch, speed, grain size, mix |
| GLITCH | Density, randomness, probability |
| FREEZE | Capture, hold, texture, mix |

## 4. Sequencer concept

- 16 steps per pattern, with adjustable pattern length.
- Eight effect lanes, one for each proposed module.
- Per-step enable, intensity, probability, and optional parameter override.
- Pattern memory and swing/shuffle.
- Randomize controls must be bounded and reversible.

The exact pattern length, timing source, and synchronization behavior must be confirmed against the MPC plugin API.

## 5. Performance-control concept

Four assignable macro controls are proposed. Initial mappings:

1. STUTTER rate / GLITCH amount
2. REVERSE length / WARP pitch
3. ECHO time / feedback
4. SPACE size / FREEZE amount

These are conceptual mappings. The available MPC UI controls and host automation interfaces must be checked before deciding how they appear on screen.

## 6. Parameter priority

Proposed priority, from highest to lowest:

1. Safety limits and parameter bounds.
2. Active live performance control.
3. Sequencer value.
4. Preset default.

When a live control is released, the user should be able to choose whether the parameter returns to the current sequencer value or holds its last live value.

## 7. Technical requirements

- No memory allocation, disk access, or blocking locks in the real-time audio callback.
- Smooth parameter changes to avoid clicks and zipper noise.
- Bounded feedback and output levels.
- Predictable behavior when transport starts, stops, or changes tempo.
- State save/restore behavior must match the MPC host's documented expectations.

## 8. Open questions

- What exact standalone plugin format and SDK are supported by MPC OS 3.10.1?
- What CPU architecture, compiler, and build environment are required?
- Which UI widgets and host controls are available?
- Can third-party effects access the required audio buffers and transport timing?
- What are the official packaging, signing, and installation steps?
