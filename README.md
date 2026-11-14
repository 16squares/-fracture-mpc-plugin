# FRACTURE

An original audio-effects concept for standalone Akai MPC hardware.

- **Target:** Akai MPC Live III
- **MPC OS reported by project owner:** 3.10.1
- **Stage:** Design and technical-feasibility phase
- **Core idea:** One effect engine controlled simultaneously by a step sequencer and live performance controls.

> This is a design starter, not a working plugin. Native MPC standalone support, SDK access, supported languages, build tools, and packaging requirements must be verified before implementation. A desktop VST is not automatically compatible with standalone MPC hardware.

## Proposed effect modules

| Module | Purpose |
|---|---|
| STUTTER | Rhythmic repeats and gating |
| REVERSE | Reverse slices |
| CRUSH | Bit-depth and sample-rate reduction |
| ECHO | Delay, feedback, filtering |
| SPACE | Reverb and ambience |
| WARP | Pitch, speed, granular texture |
| GLITCH | Probability-driven disruptions |
| FREEZE | Capture and sustain a moment |

These are proposed features, not implemented functionality.

## Design documents

- [Architecture](docs/ARCHITECTURE.md)
- [Roadmap](docs/ROADMAP.md)
- [SDK feasibility checklist](docs/SDK-FEASIBILITY.md)

## Development principles

1. Verify the official MPC standalone plugin SDK and target requirements first.
2. Separate audio processing from UI code where the SDK permits.
3. Keep real-time audio processing deterministic and avoid blocking work in the audio callback.
4. Define predictable priority between sequencer automation and live controls.
5. Build and test in small stages on a supported development environment.

No license has been selected. All rights reserved by default until the project owner chooses a license.
