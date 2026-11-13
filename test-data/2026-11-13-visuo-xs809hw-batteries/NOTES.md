# 2026-11-13 – Visuo XS809HW batteries, intake check

First inspection of the batteries belonging to the Visuo XS809HW toy drone (bought 2018),
before any charging. Part of the [teardown](../../docs/00-teardown-visuo-xs809hw.md).

## Setup

- **Instrument:** digital multimeter, DC voltage range
- **Method:** resting voltage measured on the pack's output contacts, after opening the packs
- **Condition:** packs not charged or used before the measurement

## Batteries

All packs are single-cell (1S) LiPo, labelled 3.7 V, with a built-in charge and protection
circuit and a micro-USB charging port on the pack.

## Results

| Pack | Capacity (label) | Voltage | Condition | Decision |
| --- | --- | --- | --- | --- |
| #1 | 900 mAh | 3.91 V | **Slightly swollen** | Retired, to be recycled |
| #2 | 1200 mAh | 4.03 V | OK | In use |
| #3 | 1200 mAh | 4.09 V | OK | In use |
| #4 | 1200 mAh | 3.94 V | OK | In use |
| #5 | 1200 mAh | 3.93 V | OK | In use |
| #6 | 1200 mAh | 3.76 V | OK | In use |

## Observations

- All packs held 3.76–4.09 V after several years of storage. None were deeply discharged, and
  none had a tripped protection circuit (which would read 0 V).
- The voltages are close to fully charged rather than at storage voltage (3.80–3.85 V), which
  ages a LiPo cell faster during long storage.
- Pack #1 is swollen despite a normal voltage. Voltage alone says nothing about the condition
  of a cell; a visual check is always needed.
- #1 (900 mAh) matches the drone's specified battery. #2–#6 (1200 mAh) are higher-capacity
  packs.

## Actions

- #1: connectors taped, stored on a non-flammable surface, handed in for battery recycling.
- #2–#6: inspected for swelling at every charge, kept at storage voltage when not in use.
  Handled according to [battery handling](../../docs/battery-handling.md).

## Photos

To be added: the packs and the charge and protection circuit, saved as
`docs/images/00-teardown-battery-<n>.jpg`.
