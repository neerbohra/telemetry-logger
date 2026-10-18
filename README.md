# CubeSat-style telemetry logger

A battery-powered Arduino data logger in a 3D-printed frame. It records motion (MPU-6050), pressure and altitude (BMP280) to a microSD card, and the data is analysed in Python.

**Status:** in progress (Oct - Nov 2026)
**Skills:** Fusion (CAD + engineering drawing), Arduino (I2C, SPI, SD logging), 3D printing, soldering, Python (pandas, matplotlib)

---

## Goal

Build a small, self-contained logger that runs untethered, survives being moved and dropped, and produces clean data I can check against a real measurement (stair height).

## Hardware

| Part | Job |
|---|---|
| Arduino Nano | Microcontroller |
| MPU-6050 (GY-521) | Acceleration + rotation (I2C) |
| BMP280 | Pressure -> altitude (I2C, 3.3 V) |
| MicroSD module | Logging to CSV (SPI) |
| Slide switch + LED | Start/stop + status |
| 9 V battery | Untethered power (VIN) |
| Printed frame + lid | Holds everything, M3 screws |

## Folder layout

Add files as you go. Drag a whole folder onto GitHub's **Add file > Upload files** page to keep the structure.

```
cad/        STEP exports, STL files, drawing PDFs (GitHub shows .stl files in 3D)
code/       Arduino sketch (.ino)
data/       Raw CSV logs from tests
analysis/   Python / Jupyter notebook for the plots
images/     Renders, exploded view, wiring diagram, build photos
docs/       One-page write-up (PDF)
```

## Results

Fill these in after testing (Nov 24-25).

| Measurement | Value |
|---|---|
| Channels logged | |
| Logging rate | |
| Untethered run time tested | |
| Barometric altitude gain vs true stair height | |
| Error | |
| Tilt angle vs protractor | |

Plots: altitude over time, total acceleration, free-fall detection (add images to `images/` and link them here).

## Build log

One line per session: what worked, what broke, next step.

| Date | What happened |
|---|---|
| | |

## Milestones

- [ ] Blink, button, potentiometer, Serial Monitor
- [ ] MPU-6050 over I2C, CSV output (z-axis reads ~1 g flat)
- [ ] Barometer + SD logging (2 min at 20+ Hz opens in pandas)
- [ ] Switch, status LED, flush(), battery power (10 min untethered)
- [ ] Frame v1 printed and test-fitted
- [ ] Frame v2 + lid + engineering drawing (PDF)
- [ ] Soldered perfboard
- [ ] IMU calibration + complementary filter (within ~3 deg)
- [ ] Tests: stairs, drop, spin
- [ ] Analysis + error %
- [ ] Write-up + demo video

## How to run it

1. Open `code/` in Arduino IDE 2 and install the Adafruit MPU6050 and BMP280 libraries.
2. Wire it as in `images/wiring.png` and upload to the Nano.
3. Flip the switch to log; data goes to `LOG.CSV` on the card.
4. Run the notebook in `analysis/` on the CSV.
