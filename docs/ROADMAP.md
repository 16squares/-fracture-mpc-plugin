# FRACTURE — Roadmap

This roadmap is provisional. Dates and implementation milestones should be set only after the official MPC SDK and build process are confirmed.

## Phase 0 — Feasibility

- [ ] Locate official Akai MPC standalone plugin SDK documentation.
- [ ] Confirm MPC Live III and MPC OS 3.10.1 compatibility.
- [ ] Confirm supported processor architecture, language, compiler, and packaging.
- [ ] Build and run the smallest official example plugin, if available.
- [ ] Confirm available parameter, automation, transport, and UI APIs.

## Phase 1 — Audio engine prototype

- [ ] Establish a clean audio pass-through.
- [ ] Add parameter smoothing and output protection.
- [ ] Implement one low-risk effect prototype.
- [ ] Verify CPU use, latency, and stability on target hardware.

## Phase 2 — Core effects

- [ ] STUTTER
- [ ] CRUSH
- [ ] ECHO
- [ ] REVERSE
- [ ] SPACE
- [ ] WARP
- [ ] GLITCH
- [ ] FREEZE

## Phase 3 — Sequencer

- [ ] 16-step pattern model.
- [ ] Eight effect lanes.
- [ ] Per-step intensity and probability.
- [ ] Host transport and tempo synchronization.
- [ ] Pattern save/restore.

## Phase 4 — Live performance

- [ ] Four assignable macro controls.
- [ ] Live control priority and release behavior.
- [ ] Parameter bounds and smoothing.
- [ ] Preset save/restore.

## Phase 5 — Validation

- [ ] Test on actual MPC Live III hardware.
- [ ] Test project save/reload and plugin state recall.
- [ ] Test transport start/stop and tempo changes.
- [ ] Stress-test CPU, feedback limits, and long sessions.
- [ ] Document installation and recovery steps.
