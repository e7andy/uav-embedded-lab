# Logic analyser

A home-built logic analyser on a Raspberry Pi Pico, used for bench measurements on the flight
controllers, receivers, GPS and ESCs, and for the toy drone teardown. Building it is part of the
lab: it is a small embedded project in itself and a tool for everything that follows.

## Why build one

| | Pico-based analyser | Typical 24 MHz USB analyser |
| --- | --- | --- |
| Sample rate | up to 100 MS/s | 24 MS/s |
| Channels | up to 24 | 8 |
| Input level | 3.3 V only | 3.3 V / 5 V |
| Enough for gyro SPI (10–24 MHz) | yes | no |

UART (CRSF, GPS, MSP), I²C (compass), DShot and SPI (gyro, blackbox flash) are all 3.3 V on
the flight controllers in this lab.

## Parts

- Raspberry Pi Pico H (RP2040, headers fitted). Not Pico 2: without the level-shifter board
  the RP2350 GPIO errata can affect captures.
- Breadboard, 400 points
- Jumper wires, male/female, 15 cm, 10 pcs
- Micro test clips with male dupont pin, 10 pcs
- Resistors 330 Ω, 0.25 W, 10 pcs
- JST-SH 1.0 mm cable with open end, 6-pin (check the pin count against the flight controller)
- Pin header, 2.54 mm, breakable
- Heat-shrink tube Ø3 mm
- USB A to micro-B data cable

## Firmware and software

Two options, both free:

- [gusmanb/logicanalyzer](https://github.com/gusmanb/logicanalyzer): own capture program,
  24 channels, 100 MS/s, edge and pattern triggers. On a bare Pico the two trigger pins must be
  bridged (see the [hardware page](https://github.com/gusmanb/logicanalyzer/wiki/02---LogicAnalyzer-Hardware)).
- μLA: SUMP/OLS-compatible firmware, 16 channels, used with PulseView/sigrok. Same software as
  most commercial low-cost analysers, and `.sr` files as described in [test-data](../test-data/README.md).

Flashing: hold BOOTSEL, connect USB, release. The Pico mounts as a drive; copy the `.uf2` file to it.

## Build

### 1. Probe leads with series resistors

Each signal lead has a 330 Ω resistor built into the cable, so the protection follows the lead
and the breadboard layout stays simple.

1. Cut a male/female jumper wire in the middle.
2. Strip and tin both ends.
3. Slide on heat-shrink tube.
4. Solder one resistor leg to each half (inline splice).
5. Shrink the tube over the whole resistor.
6. Mark the lead (tape or colour) as a resistor lead.

Make 8 resistor leads. Keep 2 plain leads for ground and the trigger bridge.

Why 330 Ω: with the input capacitance of about 5 pF the cut-off is far above 24 MHz, so fast SPI
is not affected. A 5 V signal by mistake gives about 4 mA into the clamp diode, which the Pico
survives. The resistors do not protect against battery voltage.

### 2. Breadboard

- Pico H straddling the centre channel, USB connector towards the edge of the board.
- Pico GND to one of the rails. The ground lead to the device under test goes from that rail.
- Trigger bridge with a plain lead, if using the gusmanb firmware.
- Resistor leads plug directly into the free holes (columns a–b or i–j) of the GPIO rows used.
- Label the channels with tape along the edge.

### 3. JST-SH adapter

For UART, GPS and receiver ports on the flight controller:

1. Solder the open wires of the JST-SH cable to a short piece of pin header, one wire per pin.
2. Heat-shrink each joint.
3. Isolate the supply wire (5 V or 4.5 V) and leave it unconnected. Only signals and GND go to
   the breadboard.
4. Check the pinout against the flight controller manual before soldering.

Plugging the adapter into a port replaces the device that normally sits there. To capture
traffic between the flight controller and a device, measure on the pads with test clips, or
build a Y-cable later.

## Power and safety

- The Pico is powered from the computer's USB port. The 5 V from USB only feeds the Pico's
  regulator; the GPIO inputs are 3.3 V.
- Connect only GND and signals between the Pico and the device under test. Never VBUS, VSYS,
  3V3, 5 V or VBAT.
- Never connect a channel to battery voltage (up to 25 V on 6S), the main power pads or the
  VBAT pin of the ESC connector.
- Power the device under test via USB or through the smoke stopper during bench tests.

## Channel plan

| Test | Signals | Channels |
| --- | --- | --- |
| Receiver ↔ flight controller (CRSF) | TX, RX | 2 |
| GPS ↔ flight controller (UART) | TX, RX | 2 |
| Compass (I²C) | SDA, SCL | 2 |
| DShot to ESC | 4 motor signals | 4 |
| DShot with ESC telemetry | 4 motors + telemetry | 5 |
| Gyro (SPI) | SCK, MOSI, MISO, CS (+ INT) | 4–5 |
| Blackbox flash (SPI) | SCK, MOSI, MISO, CS | 4 |

Every capture also needs a ground connection. Ten test clips cover every capture in the table
with ground, with spares.

## First test: UART from a micro:bit

Before measuring on the drones, the analyser is verified on a known signal. A BBC micro:bit is
used as the source: it runs at 3.3 V like the Pico, so no level shifting is needed, and the
transmitted data is fully under control.

### Program (MakeCode)

In [MakeCode](https://makecode.microbit.org):

1. **on start:** `serial redirect to TX P0 RX P1 at baud rate 115200`
   (Advanced → Serial).
2. **forever:** `serial write line "Hello"`, then `pause (ms) 1000`.
3. Optional: **on button A pressed** → `serial write line "A"`, and the same for B, so that
   button presses show up in the capture.

Flash by copying the `.hex` file to the MICROBIT drive.

### Wiring

| micro:bit | Logic analyser |
| --- | --- |
| GND | GND rail |
| P0 (TX) | Channel 1, through a resistor lead |

The large edge rings P0 and GND take crocodile clips or the micro test clips.

### Capture and decode

1. Sample rate at least 1 MHz (8–10 samples per bit at 115200 baud is plenty).
2. Trigger on the falling edge of channel 1 (the UART start bit).
3. Add a UART decoder: 115200 baud, 8 data bits, no parity, 1 stop bit (8N1), idle high.
4. Expected result: `Hello` followed by CR LF once a second.

### Further exercises

- **Baud rate:** repeat at 9600 baud and compare the bit time (about 104 µs at 9600, 8.7 µs at
  115200).
- **Sensor data:** send accelerometer values with `serial write value`. This mirrors what the
  flight controller does with gyro data, at a much lower rate.
- **Wrong settings on purpose:** decode at the wrong baud rate or with inverted polarity and
  note what the result looks like. Useful when debugging CRSF and other inverted or unusual
  serial links later.

Save the capture and a `NOTES.md` in `test-data/YYYY-MM-DD-logic-analyser-first-test/` as the
first entry.

### Alternatives

- **Raspberry Pi:** enable the serial console (`raspi-config` → Interface Options → Serial
  Port) and capture the boot messages on GPIO14 (pin 8) at 115200 baud. 3.3 V, no code needed.
- **Arduino (5 V):** use a voltage divider before the Pico input, for example 330 Ω in series
  and two 330 Ω to ground, giving about 3.3 V.

## Later: level-shifter board

The project's V6 board adds level shifters (1.6–5 V inputs) and protection, and supports the
Pico 2 at higher sample rates. A possible later soldering project. Schematics and design files
are in the [repository](https://github.com/gusmanb/logicanalyzer).
