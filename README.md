# uav-embedded-lab

Embedded systems lab built around two custom FPV drones.

This repository documents the build, configuration, testing and analysis of two
small unmanned aircraft, used as a hands-on platform for embedded software work:
real-time control, sensor fusion, serial protocols, motor control and
firmware development on STM32 microcontrollers.

Everything is documented as it happens: build notes, configuration snapshots,
flight logs, bench measurements and the conclusions drawn from them.

## Platforms

| Platform | Role |
| --- | --- |
| 5" freestyle quad | Main build. Full build from components, GPS and compass, outdoor flying, PID tuning and autonomous flight modes. |
| 2.2" cinewhoop | Prop-guarded quad for indoor flying and frequent, low-risk testing of firmware and configuration changes. |

A detailed hardware list will be added once the component choices are final.

## Learning goals

1. **Regulations and certification.** EASA open category, operator registration and remote pilot certificates.
2. **Build.** Soldering, wiring and bring-up of flight controller, ESCs, receiver and video system.
3. **Firmware.** Building Betaflight, INAV and ArduPilot from source and flashing custom builds.
4. **Simulation.** Stick training in an FPV simulator and software-in-the-loop (SITL) testing of firmware changes.
5. **Control.** PID tuning and filter analysis based on blackbox logs.
6. **Image stabilisation.** Gyro-based stabilisation with Gyroflow compared to in-camera stabilisation.
7. **Debugging.** UART, SPI and DShot analysis with a logic analyser, plus electrical measurements.
8. **Custom development.** Own modules or changes in firmware, for example sensor handling or telemetry.
9. **Summary.** Lessons learned and how they apply to professional embedded work.

## Repository layout

```
docs/        Build notes, analyses and write-ups (Markdown), images in docs/images/
config/      Configuration snapshots per platform (Betaflight "diff all", INAV, EdgeTX)
logs/        Blackbox flight logs, stored with Git LFS
test-data/   Logic analyser captures, multimeter measurements and other bench data
sitl/        Software-in-the-loop setup and test scenarios
```

Each folder has its own README describing conventions for what goes there.

## Conventions

- **Configuration as code.** Flight controller settings are saved as Betaflight `diff all`
  (not `dump`), so the history shows only intentional changes.
- **Large files in Git LFS.** Blackbox logs, logic analyser captures, video and large images
  are tracked with Git LFS (see `.gitattributes`). Run `git lfs install` once before cloning.
- **Every test has a note.** Logs and measurements are paired with a short Markdown note
  describing setup, firmware version, configuration and result.
