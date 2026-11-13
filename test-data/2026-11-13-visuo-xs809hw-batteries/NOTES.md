# 2026-11-13 – Visuo XS809HW batteries, intake check

First inspection of the batteries belonging to the Visuo XS809HW toy drone (bought 2018),
before any charging. Part of the [teardown](../../docs/00-teardown-visuo-xs809hw.md).

## Setup

- **Instrument:** digital multimeter, DC voltage range
- **Method:** resting voltage measured on the pack's output contacts, after opening the packs
- **Condition:** packs not charged or used before the measurement

## Batteries

All packs are single-cell (1S) LiPo pouch cells, labelled 3.7 V, in a plastic case with a
small circuit board carrying a micro-USB charging port and the connector to the drone.

| Pack | Cell marking | Size code | Capacity | Date code |
| --- | --- | --- | --- | --- |
| #1 | HW 752560P | 7.5 × 25 × 60 mm | 900 mAh | 180601 (2018-06-01) |
| #2–#6 | HW 852560P | 8.5 × 25 × 60 mm | 1200 mAh | 20221214 (2022-12-14) |

The size code follows the usual pouch-cell convention: thickness, width and length in tenths of
millimetres for the first digit pair and millimetres for the rest.

## Results

| Pack | Capacity | Voltage | Condition | Decision |
| --- | --- | --- | --- | --- |
| #1 | 900 mAh | 3.91 V | **Slightly swollen** | Retired, to be recycled |
| #2 | 1200 mAh | 4.03 V | OK | In use |
| #3 | 1200 mAh | 4.09 V | OK | In use |
| #4 | 1200 mAh | 3.94 V | OK | In use |
| #5 | 1200 mAh | 3.93 V | OK | In use |
| #6 | 1200 mAh | 3.76 V | OK | In use |

## Observations

- #1 is the original pack from 2018. #2–#6 are replacement packs made in December 2022.
- All packs held 3.76–4.09 V after long storage. None were deeply discharged, and
  none had a tripped protection circuit (which would read 0 V).
- The voltages are close to fully charged rather than at storage voltage (3.80–3.85 V), which
  ages a LiPo cell faster during long storage.
- Pack #1 is swollen despite a normal voltage. Voltage alone says nothing about the condition
  of a cell; a visual check is always needed.
- #1 (900 mAh) matches the drone's specified battery. #2–#6 (1200 mAh) are thicker,
  higher-capacity cells in the same case size.

## Charge board

The board on each pack is marked `HJ-XS806DC` with the date 2017-08-13. It carries:

- a micro-USB connector for charging
- solder pads marked `B+` and `B-` for the cell
- a three-pin connector to the drone
- a small SOT-23-sized device, presumably the charge controller (marking not yet read)

The board is a 1S charger with protection, so the packs are charged over USB and never on the
balance charger. Identifying the charge IC and measuring the charge current and the cut-off
voltages are left for the teardown.

## Actions

- #1: connectors taped, stored on a non-flammable surface, handed in for battery recycling.
- #2–#6: inspected for swelling at every charge, kept at storage voltage when not in use.
  Handled according to [battery handling](../../docs/battery-handling.md).

## Photos

![All six packs, numbered](../../docs/images/00-teardown-battery-overview.jpg)

*The six packs, numbered #1–#6. #1 has a different case and the 900 mAh cell.*

![Pack #1 opened](../../docs/images/00-teardown-battery-1-swollen.jpg)

*Pack #1 out of its case: HW 752560P, 3.7 V 900 mAh, date code 180601. Slightly swollen.*

![Charge board, component side](../../docs/images/00-teardown-battery-charger-bottom.jpg)

*Charge board marked HJ-XS806DC 2017-08-13, with the micro-USB connector and the cell leads.*

![Charge board, connector side](../../docs/images/00-teardown-battery-charger-top.jpg)

*The other side of the board: B+ and B- pads, the three-pin connector to the drone and the
small charge controller.*
