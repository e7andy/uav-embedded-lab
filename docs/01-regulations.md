# 01 – Regulations and certification

Flying in Sweden under the EU drone regulation (EU 2019/947 and 2019/945), administered by
Transportstyrelsen (the Swedish Transport Agency). All flying is planned in the **open category**.

## Status

| Step | Status | Date | Notes |
| --- | --- | --- | --- |
| UAS operator registration | Done | 2026-10-27 | Registered as a private operator via Transportstyrelsen's e-service (Drönarsidan). Renewed yearly. |
| Operator ID on Visuo XS809HW | Done | 2026-10-27 | Public part of the ID only, see below. |
| Operator ID on 5" quad | To do | | When built. |
| Operator ID on cinewhoop | To do | | When delivered. |
| Remote pilot certificate A1/A3 | To do | | Online training and theory test. Required for the 5" quad (> 250 g). |
| Remote pilot certificate A2 | To do | | Not required for these aircraft, taken for the competence. |
| Liability insurance | To do | | Check coverage for drones > 250 g, or via a model flying club. |

## Aircraft and subcategories

Both drones are **privately built**, which means they carry no class label (C0–C4).
That decides which open subcategory they can fly in.

| Aircraft | Take-off mass (est.) | Subcategory | Conditions |
| --- | --- | --- | --- |
| 5" freestyle quad | ~630 g | **A3** | Far from uninvolved people, at least 150 m from residential, commercial, industrial and recreational areas. |
| 2.2" cinewhoop | ~135 g | **A1** or **A3** | A1 only with max speed below 19 m/s. A3 otherwise. |
| Visuo XS809HW (toy) | 158 g | A1 | Camera drone, operator ID required. |

Common to all outdoor flights: max 120 m above ground, visual line of sight
(via an observer when flying with goggles), and checking geographical zones on
Transportstyrelsen's drone map before flying at a new site.

Indoor flights are outside the scope of the aviation rules.

### A2 does not apply

Subcategory A2 is limited to C2-labelled drones. A privately built drone can never fly in A2,
whatever certificate the pilot holds.

### Speed limit for A1 on the cinewhoop

The estimated top speed of the cinewhoop is 60–90 km/h, above the 19 m/s (~68 km/h) limit for
privately built drones in A1. This is handled in the flight controller configuration:

- **Profile 1 (A1):** throttle limit set so that top speed stays below 19 m/s.
- **Profile 2 (A3):** no limit.
- Profile selection on a switch on the radio.

The chosen limit and the test that verifies it are documented in `config/cinewhoop/`.

## Operator ID marking

- The operator ID is shown **legibly and durably** on every drone with a camera.
- Only the **public part** is displayed. The three secret characters after the hyphen
  are never shown on the aircraft, in photos or in this repository.

## Remote ID

Direct Remote ID is required for drones with class labels C1–C3 in the open category and for
all drones in the specific category. Privately built drones without class labels flying in the
open category are not covered by that requirement, so neither custom build needs Remote ID
today. This changes if flying moves to the specific category or into airspace that requires it.

Remote ID (ASTM F3411 / EN 4709-002, OpenDroneID) is a possible later experiment with ArduPilot.

## References

- [Transportstyrelsen – Drönare](https://www.transportstyrelsen.se/dronare)
- [EASA – Open category](https://www.easa.europa.eu/en/node/119320)
