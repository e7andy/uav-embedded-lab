# logs

Blackbox flight logs, stored with Git LFS.

## Conventions

- One folder per session: `YYYY-MM-DD-<platform>-<purpose>/`,
  for example `2026-11-02-cinewhoop-hover-baseline/`.
- Each folder contains the raw log files and a `NOTES.md` with:
  - firmware version and a link to the configuration used
  - battery, props and conditions
  - what was tested and what was observed
- Analysis results (plots, conclusions) go in `docs/`, linking back to the log folder.
