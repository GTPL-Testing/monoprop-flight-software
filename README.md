# monoprop-flight-software

The **Monoprop-specific integrated flight software** — the real-time stack that
wires the vehicle-agnostic GN&C libraries into a running vehicle. Unlike the
[`navigation`](../navigation) / [`control`](../control) / [`guidance`](../guidance) /
[`dynamics`](../dynamics) libraries, this repo is *not* plug-and-play: it is the
Monoprop vehicle integration.

> **Provenance:** Carved out of the monolithic
> [`Propulsive-Landers-GT/MonopropUAV`](https://github.com/Propulsive-Landers-GT/MonopropUAV)
> repo in July 2026. `ControlLoop/`, `Lander/`, and `Monoprop/` are kept whole
> because each is a cohesive buildable unit. Full commit history is preserved.
> See the [GTPL-test root README](../README.md) for the full mapping.

## Contents

| Path | What it is |
|------|------------|
| `ControlLoop/` | The integrated real-time control loop (C++): `Loop/`, `LQR/`, `Filters/` (EKFs, Madgwick), `CustomLinear/`, `IntegratedDynModel/`, bundled `lapack/`, `Data/` + `data_creators/`, CMake/Make build |
| `Lander/` | Rust flight software: `src/algorithms/` (control, guidance, navigator, rcs) + `src/fsm/` (flight state machine) |
| `Monoprop/` | Rust Cargo workspace: `Common/`, `Drone/` (onboard), `GroundControl/` (ground station + MPC) |
| `ControlLoopMPC/` | MPC control-loop design notes |
| `docs/` | Original top-level MonopropUAV README (with the project Google Drive links) |

> **Note:** `ControlLoop/` contains integrated *runtime* copies of LQR, EKF, and the
> `CustomLinear` math that also appear as standalone designs in the library repos.
> They are kept here as part of this build unit; deduplicating them into shared
> dependencies is a good future refactor.

## Related repos

Libraries this integrates: [`navigation`](../navigation), [`control`](../control), [`guidance`](../guidance), [`dynamics`](../dynamics).
Hardware it runs on: [`monoprop-firmware`](../monoprop-firmware), [`monoprop-electronics`](../monoprop-electronics).
