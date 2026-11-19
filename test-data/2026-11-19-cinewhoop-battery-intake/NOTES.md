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

## Next

- Internal resistance per cell to be measured with the charger at the first charge and added to
  the battery log.
- Charge in LiHV mode only (4.35 V per cell).
