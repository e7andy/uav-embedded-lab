# test-data

Bench measurements and captures that are not flight logs.

Examples:

- Logic analyser captures of UART (CRSF, GPS, MSP), SPI (gyro) and DShot
- Multimeter measurements of BEC voltages, battery cells and continuity checks
- Motor and ESC telemetry recorded on the bench

## Conventions

- One folder per test: `YYYY-MM-DD-<subject>/`, for example `2026-11-05-dshot600-capture/`.
- Each folder contains the raw data and a `NOTES.md` describing setup, instruments,
  sample rate and the result.
- Captures are saved in the analyser's native format (`.sr` for sigrok/PulseView),
  plus a PNG screenshot of the relevant part for use in `docs/`.
