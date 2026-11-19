# Battery handling

Rules for charging, storing, transporting and disposing of the lithium batteries used in this lab.
They apply to every pack, from the radio's cells to the flight packs. The manufacturer's
instructions for a specific battery or charger always take precedence over this document.

## Battery types in use

| Use | Chemistry | Cells | Notes |
| --- | --- | --- | --- |
| 5" quad flight packs | LiPo | 6S | XT60 discharge connector, JST-XH balance lead |
| Cinewhoop flight packs | LiHV | 3S | XT30 discharge connector, JST-XH balance lead |
| Radio transmitter | Li-ion (18650) | 2 cells | Charged in the radio over USB-C |
| Toy drone (teardown) | LiPo | 1S | Charged over micro-USB on the pack itself (built-in charge and protection circuit), not with the balance charger. Inspected and measured before any charging. |
| Goggles and other devices | Li-ion, built in | | Charged over USB-C as specified by the manufacturer |

### Voltages per cell

| Chemistry | Full | Storage | Lowest after a flight (rested) | Absolute minimum |
| --- | --- | --- | --- | --- |
| LiPo | 4.20 V | 3.80–3.85 V | 3.50 V | 3.30 V |
| LiHV | 4.35 V | 3.80–3.85 V | 3.50 V | 3.30 V |
| Li-ion (18650) | 4.20 V | about 3.6–3.7 V | 3.0 V | 2.5 V |

A LiHV pack can be charged in LiPo mode (it will just hold less charge), but a LiPo pack must
**never** be charged in LiHV mode.

## Labelling and log

Every flight pack gets an ID written on the pack, for example `B6-01` for the first 6S pack and
`B3-01` for the first 3S pack. The log below records each pack's history, so that a pack that
degrades can be identified and retired.

| ID | Chemistry | Cells | Capacity | Bought | Cycles | Internal resistance per cell (new) | Status |
| --- | --- | --- | --- | --- | --- | --- | --- |
| B3-01 | LiHV | 3S | 580 mAh | 2026-11 | 0 | 40 / 33 / 34 mΩ | In use |
| B3-02 | LiHV | 3S | 580 mAh | 2026-11 | 0 | 44 / 51 / 43 mΩ | In use |
| B3-03 | LiHV | 3S | 580 mAh | 2026-11 | 0 | 28 / 47 / 40 mΩ | In use |
| B3-04 | LiHV | 3S | 580 mAh | 2026-11 | 0 | 25 / 29 / 37 mΩ | In use |

Intake checks: [B3-01 – B3-04](../test-data/2026-11-19-cinewhoop-battery-intake/NOTES.md).

Internal resistance is measured with the charger when the pack is new and then about every
ten cycles. The charger shows it only during a balance charge. Readings vary by up to about
10 mΩ between attempts, so two readings are taken and averaged. A clear rise, or one cell that differs from the others, is a sign of wear.

## Receiving new batteries

1. Check the pack visually: no swelling, dents, torn wrap or damaged leads.
2. Measure each cell on the balance lead with a multimeter. New packs are shipped at storage
   voltage, about 3.7–3.9 V per cell, with less than 0.05 V between cells.
3. A cell below 3.5 V, or a large difference between cells, is reported to the seller before use.
4. Label the pack and add it to the log.
5. Store it at storage voltage until it is used.

Measurements go in `test-data/YYYY-MM-DD-battery-intake/`.

## Charging

- **Always balance charge.** Both the discharge lead and the balance lead are connected.
- **Check chemistry and cell count** on the charger before starting: LiPo or LiHV, and the
  number of cells, must match the pack.
- **Charge current 1C** as the default, meaning the capacity in Ah as amps (a 1.38 Ah pack is
  charged at 1.4 A). Higher only if the manufacturer allows it.
- **Never unattended.** Someone stays in the room while a pack is charging.
- **Fireproof surface.** Charge on a non-flammable surface (stone, tile, metal) or in a LiPo bag,
  away from curtains, paper and other flammable material.
- **Room temperature.** A pack that is hot after a flight, or cold from outside, is left to reach
  room temperature before charging.
- **Charge shortly before flying.** Full packs are not left lying around. A pack charged but not
  flown is returned to storage voltage within a day or two.
- **Adapters.** Only adapters with the correct polarity are used. A new or home-made adapter is
  checked with a multimeter before the first charge.

## Flying

- The flight controller shows battery voltage in the OSD. The flight is ended at about
  3.5 V per cell under light load.
- After landing, disconnect the battery before handling the drone.
- Check the pack after a crash. A pack that is dented, punctured or swollen is retired, see
  below.

## Storage

- **Storage voltage** (3.80–3.85 V per cell for LiPo and LiHV) whenever the pack will not be
  flown within a day or two. Use the charger's storage mode.
- **Fire-resistant container.** Packs are stored in a LiPo bag or a metal box with a lid that
  is not airtight, so that gas can escape.
- **Cool and dry, room temperature.** Not in a car, a cold garage or direct sunlight.
- **Connectors protected** so that they cannot short-circuit against each other or metal.
- A smoke alarm in the room where batteries are stored and charged.
- **Long storage.** Check the voltage about once a month and top up to storage voltage if needed.

## Transport

- At storage voltage, in a LiPo bag, with connectors covered.
- In a car: not in direct sun and not left in a parked car.
- Flying commercially: lithium batteries go in hand luggage only, never in checked baggage, and
  the airline's limits apply (usually up to 100 Wh per pack without approval).

## Damaged or worn-out batteries

A pack is retired if it is swollen, punctured, has damaged wrap or leads, cannot hold a balanced
charge, or has been discharged below the absolute minimum.

1. Move it to a non-flammable place outdoors or into a metal container, away from other packs.
2. Do not charge it.
3. Tape over the connectors.
4. Hand it in for recycling as a battery (the battery container at a recycling centre or in a
   shop that sells batteries).

A pack that becomes hot, smokes or starts to swell during charging or storage: disconnect the
charger if it can be done safely, move away and keep the room ventilated. Never carry a burning
battery through the house.

## In case of fire

1. Get people out and call 112.
2. Lithium battery fires cannot be smothered effectively and can re-ignite. Water cools the
   surroundings and the pack. Sand or a fire blanket limits the spread.
3. Ventilate afterwards. The smoke is toxic.

## Related

- [01 – Regulations](01-regulations.md)
- [test-data](../test-data/README.md) for battery measurements
