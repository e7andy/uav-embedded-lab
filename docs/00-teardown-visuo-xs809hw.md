# 00 – Teardown: Visuo XS809HW

A teardown of a toy-grade camera drone bought in 2018, as a baseline before the
custom builds. The goal is to see how a low-cost consumer drone is built inside and
compare it with a proper STM32-based flight controller running open firmware.

> **Status:** template, to be filled in during the teardown.

## The drone

| Property | Value |
| --- | --- |
| Model | Visuo XS809HW (foldable "selfie" drone) |
| Bought | 2018 |
| Weight | 158 g (spec) / ___ g (measured) |
| Size | 325 × 325 × 60 mm unfolded, 190 × 140 × 60 mm folded |
| Camera | 2 MP, 720p, 120° FOV, Wi-Fi live view to phone app |
| Control link | 2.4 GHz handheld transmitter |
| Battery | 1S 3.7 V 900 mAh LiPo |
| Features | Barometric altitude hold, auto take-off/landing, three speed modes, flips |

## Safety first

- [ ] Inspect the battery for swelling or damage. A swollen pack is **not** charged; it is
      discharged and recycled.
- [ ] Measure the resting cell voltage: ___ V. Below 3.0 V the pack is considered unsafe to charge.
- [ ] Remove the battery before opening the airframe.

## Teardown log

Photograph every step. Save photos as `images/00-teardown-<step>.jpg`.

1. **Opening the shell.** Screws, clips, glue: ___
2. **Main board.** Photo of both sides, board dimensions: ___
3. **Motors.** Brushed or brushless, size, connector type: ___
4. **Camera and Wi-Fi module.** Separate board or integrated: ___
5. **Antennas.** Type and placement for control link and Wi-Fi: ___

## Component identification

Read the markings on each chip (a magnifier or phone macro photo helps) and look up the datasheet.

| Function | Marking | Identified part | Datasheet |
| --- | --- | --- | --- |
| Microcontroller | | | |
| IMU (gyro/accelerometer) | | | |
| Barometer | | | |
| Radio receiver (2.4 GHz) | | | |
| Wi-Fi / camera SoC | | | |
| Motor drivers (MOSFETs) | | | |
| Voltage regulator | | | |

## Bench measurements

Instruments: UNI-T UT161D multimeter, SparkFun 8-channel logic analyser (PulseView/sigrok).
Raw captures go in `test-data/YYYY-MM-DD-visuo-xs809hw/`.

- [ ] Supply rails (battery, 3.3 V, others): ___
- [ ] Continuity and ground reference points for the logic analyser: ___
- [ ] Bus between MCU and IMU (I²C or SPI), clock speed and register reads: ___
- [ ] Bus between MCU and radio receiver: ___
- [ ] Motor drive signal: PWM frequency and duty cycle at hover and full throttle: ___
- [ ] Debug or programming pads (SWD, UART) present? ___

## Comparison with the custom builds

| Aspect | Visuo XS809HW | Custom builds (STM32 + Betaflight/INAV) |
| --- | --- | --- |
| Flight controller MCU | | STM32H743 / STM32F405 |
| IMU | | ICM-42688-P class |
| Motor control | | Brushless, ESC with DShot and RPM telemetry |
| Control loop rate | | 4–8 kHz |
| Firmware | Closed | Open source, buildable from source |
| Logging | None | Blackbox flash, 16 MB |
| Video | Wi-Fi to phone, high latency | DJI O4 digital link, ~20 ms |
| Configurability | Fixed | Fully configurable PID, filters, rates |

## Findings and conclusions

What does a toy drone get away with, and what does it lack? What would it take to make it
a real flight controller platform?

- ___
