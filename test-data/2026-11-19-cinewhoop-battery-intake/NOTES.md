# 2026-11-19 – Cinewhoop batteries, intake check

Intake check of the four flight packs for the cinewhoop, before the first charge, following
[battery handling](../../docs/battery-handling.md#receiving-new-batteries).

## Setup

- **Instrument:** digital multimeter, DC voltage range, 0.01 V resolution
- **Method:** total pack voltage on the XT30 discharge connector, then cumulative voltages on the
  JST-XH balance lead (black wire to the first and second cell taps)
- **Condition:** new packs as delivered, never charged

## Batteries

| ID | Label | Marking on pack |
| --- | --- | --- |
| B3-01 | 3S LiHV, 11.4 V, 580 mAh, 95C, 6.61 Wh, XT30 | 1 |
| B3-02 | same | 2 |
| B3-03 | same | 3 |
| B3-04 | same | 4 |

![The four packs, numbered 1–4](../../docs/images/cinewhoop-batteries-b3-01-04.jpg)

## Measurements

| ID | Cell 1 | Cells 1–2 | Pack (XT30) |
| --- | --- | --- | --- |
| B3-01 | 3.81 V | 7.63 V | 11.45 V |
| B3-02 | 3.81 V | 7.62 V | 11.43 V |
| B3-03 | 3.81 V | 7.63 V | 11.45 V |
| B3-04 | 3.80 V | 7.62 V | 11.43 V |

## Result

Cell voltages derived from the cumulative readings (cell 2 = cells 1–2 minus cell 1, cell 3 =
pack minus cells 1–2):

| ID | Cell 1 | Cell 2 | Cell 3 | Spread | Verdict |
| --- | --- | --- | --- | --- | --- |
| B3-01 | 3.81 V | 3.82 V | 3.82 V | 0.01 V | OK |
| B3-02 | 3.81 V | 3.81 V | 3.81 V | 0.00 V | OK |
| B3-03 | 3.81 V | 3.82 V | 3.82 V | 0.01 V | OK |
| B3-04 | 3.80 V | 3.82 V | 3.81 V | 0.02 V | OK |

- All cells are at storage voltage (3.80–3.85 V), as expected for new packs.
- The largest spread within a pack is 0.02 V, well below the 0.05 V limit. With 0.01 V
  resolution the differences are close to the measurement uncertainty.
- No swelling or damage seen.

## Internal resistance

Measured with the balance charger at the start of a balance charge (LiHV, 3S, 0.6 A = 1C). The
charger shows internal resistance only during balance charging, not in standby or storage mode,
and the value appears some seconds after the charge has started. Values in mΩ per cell.

| ID | Reading | Cell 1 | Cell 2 | Cell 3 |
| --- | --- | --- | --- | --- |
| B3-01 | 1 | 36 | 29 | 30 |
| B3-01 | 2 | 43 | 36 | 37 |
| B3-02 | 1 | 43 | 52 | 37 |
| B3-02 | 2 | 45 | 50 | 48 |
| B3-03 | 1 | 28 | 47 | 40 |
| B3-04 | 1 | 25 | 29 | 37 |

Baseline used in the battery log (mean of the readings per cell):

| ID | Cell 1 | Cell 2 | Cell 3 | Pack mean |
| --- | --- | --- | --- | --- |
| B3-01 | 40 | 33 | 34 | 35 |
| B3-02 | 44 | 51 | 43 | 46 |
| B3-03 | 28 | 47 | 40 | 38 |
| B3-04 | 25 | 29 | 37 | 30 |

### Observations

- Repeated readings of the same pack differ by up to about 10 mΩ per cell (B3-01 read about
  7 mΩ higher on every cell the second time; one cell of B3-02 moved from 37 to 48 mΩ).
- The difference between packs (30–46 mΩ pack mean) is of the same order as the repeatability,
  so no pack can be singled out as weaker from these readings. B3-02 read highest both times
  and is the first one to watch.
- 25–52 mΩ per cell is a normal range for small 3S packs measured by a charger through the
  balance lead, which includes lead and connector resistance.
- The charger's reading is useful for trends rather than as an absolute value. A pack is
  considered worn when its resistance has risen 50–100 % from this baseline, or when one cell
  drifts clearly away from the others.

### Method for later readings

To keep readings comparable:

- same charger and channel, pack at room temperature
- balance lead firmly seated
- read once the value has settled, about 20–30 s after the charge has started
- take two readings and use the mean

## After the check

The charge was stopped at about 3.85 V per cell, so the packs stay at storage voltage until the
first flight. Packs are charged in LiHV mode only (4.35 V per cell).
