# 04 – Simulator training

Flight training in a simulator before the first real flights, and a log of the progress.
A crash in the simulator costs nothing; the goal is to have stick control as muscle memory
before flying the cinewhoop indoors and the 5" quad at an A3 site.

## Setup

| Part | Choice |
| --- | --- |
| Simulator | Liftoff (Steam) |
| Add-ons | Liftoff: Micro Drones, DLC Night Fever, DLC Slipstream |
| Controller | Spare ELRS radio connected over USB-C as a joystick. The main radio is used once it has been configured. |
| Mode | Mode 2 (throttle and yaw on the left stick) |

Liftoff is used for 5"-class racing and freestyle, Liftoff: Micro Drones for small whoops
flown indoors, which is closer to how the cinewhoop will be flown at first.

## Settings

| Setting | Value | Comment |
| --- | --- | --- |
| Center sensitivity | 120 °/s | Same for roll, pitch and yaw |
| Max rate | 500 °/s | Same for all axes. Calm beginner rates. |
| Expo | 0.40 | Same for all axes |
| Camera angle | 10° | Low, suited to slow flying and to the cinewhoop |

Liftoff's rate model corresponds to Betaflight's *Actual* rates type: center sensitivity,
max rate and expo map directly. The same values are to be set in the flight controller
configuration (`config/`) so that the real aircraft respond like the simulator.

### Planned progression

- Raise max rate in steps of about 50 °/s when turns start to feel slow. Typical rates for
  experienced pilots are 650–850 °/s.
- Raise the camera angle towards 20–30° for faster flying on the 5" quad. Keep 10–15° for the
  cinewhoop.
- Each change is noted in the log below, so that lap times before and after can be compared.

## Track notes

| Track | Why |
| --- | --- |
| Short Circuit – 01 – Pole Position | Large gates and plenty of room. Best track for learning to race. |

## Training log

Total time is accumulated play time in Liftoff (from Steam). Race times are as shown by Liftoff
(minutes:seconds.milliseconds). A race is two laps of the track.

| Date | Total time | Track | Settings | Result | Notes |
| --- | --- | --- | --- | --- | --- |
| 2026-11-24 | 9.8 h | Short Circuit – 01 – Pole Position | 120 / 500 / 0.40, camera 10° | 6:34.504 (race, 2 laps) | Completed with a few crashes |

## Next steps

1. Complete Pole Position without crashes, then lower the time.
2. Slow freestyle around obstacles in Liftoff: Micro Drones, as preparation for indoor flights
   with the cinewhoop.
3. Transfer the rates to Betaflight on both aircraft.
4. Simulator flights with the main radio once it has been configured, with the same rates and
   switch layout as for the real aircraft (arm, flight mode, the A1 speed-limit profile).
