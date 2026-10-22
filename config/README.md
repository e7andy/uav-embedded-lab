# config

Configuration snapshots, one folder per platform.

```
config/
├── five-inch/
└── cinewhoop/
```

## Conventions

- **Betaflight:** save with `diff all` from the CLI (not `dump`), as
  `betaflight-<version>-<description>.txt`. Overwrite the file when the configuration
  changes and let git keep the history, instead of creating new files for every change.
- **INAV / ArduPilot:** `diff all` for INAV, `.param` files for ArduPilot.
- **Radio:** EdgeTX model files exported from the transmitter.
- Commit messages describe *why* a setting changed, for example
  "Lower D-term LPF to reduce motor heat after hover test".
