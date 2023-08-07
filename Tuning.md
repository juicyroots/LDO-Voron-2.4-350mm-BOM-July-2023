## PID Tune Heated Bed
Move nozzle to the center of the bed and approximately 5-10mm above the bed surface, then run:
```gcode
PID_CALIBRATE HEATER=heater_bed TARGET=100
```

## PID Tune Hotend
Set the part cooling fans to 25% (M106 S64) and then run:
```gcode
PID_CALIBRATE HEATER=extruder TARGET=245
```

## Input Shaping
Test the accelerometer
```gcode
ACCELEROMETER_QUERY
```
Run Calibration
```gcode
SHAPER_CALIBRATE
```

### Input Shaping - X/Y Axis Tune

```gcode
TEST_RESONANCES AXIS=X
```
```gcode
TEST_RESONANCES AXIS=Y
```
After completing these scripts, Klipper will store the results in two CSV files: “/tmp/resonances_x_*.csv” and “/tmp/resonances_y_*.csv”.

### Input Shaping - Data Analysis
```
~/klipper/scripts/calibrate_shaper.py /tmp/calibration_data_x_*.csv -o /tmp/shaper_calibrate_x.png 
~/klipper/scripts/calibrate_shaper.py /tmp/calibration_data_y_*.csv -o /tmp/shaper_calibrate_y.png 
```

## Cable Orientation
![Input Shaper Cable Orientation](https://docs.ldomotors.com/input_shaper_kit/pi_zero_2w.jpg "Input Shaper Cable Orientation")

## Pressure Advance

Use a high speed (eg, 100mm/s), zero infill, and a coarse layer height (the layer height should be around 75% of the nozzle diameter). Make sure any "dynamic acceleration control" is disabled in the slicer

Model to Print: [Tuning Tower](https://www.klipper3d.org/prints/square_tower.stl)
```
SET_VELOCITY_LIMIT SQUARE_CORNER_VELOCITY=1 ACCEL=500
```
```
TUNING_TOWER COMMAND=SET_PRESSURE_ADVANCE PARAMETER=ADVANCE START=0 FACTOR=.005
```

```
pressure_advance = <start> + <measured_height> * <factor>. (For example, 0 + 12.90 * .020 would be .258.)
```


## Input Shaper Results

### X Axis

Fitted shaper 'zv' frequency = 58.6 Hz (vibrations = 4.3%, smoothing ~= 0.051)
To avoid too much smoothing with 'zv', suggested max_accel <= 13400 mm/sec^2
Fitted shaper 'mzv' frequency = 60.0 Hz (vibrations = 0.0%, smoothing ~= 0.057)
To avoid too much smoothing with 'mzv', suggested max_accel <= 10600 mm/sec^2
Fitted shaper 'ei' frequency = 72.0 Hz (vibrations = 0.0%, smoothing ~= 0.062)
To avoid too much smoothing with 'ei', suggested max_accel <= 9700 mm/sec^2
Fitted shaper '2hump_ei' frequency = 89.8 Hz (vibrations = 0.0%, smoothing ~= 0.067)
To avoid too much smoothing with '2hump_ei', suggested max_accel <= 9000 mm/sec^2
Fitted shaper '3hump_ei' frequency = 108.0 Hz (vibrations = 0.0%, smoothing ~= 0.070)
To avoid too much smoothing with '3hump_ei', suggested max_accel <= 8500 mm/sec^2
Recommended shaper is mzv @ 60.0 Hz

### Y Axis

Fitted shaper 'zv' frequency = 44.0 Hz (vibrations = 14.9%, smoothing ~= 0.085)
To avoid too much smoothing with 'zv', suggested max_accel <= 7500 mm/sec^2
Fitted shaper 'mzv' frequency = 42.6 Hz (vibrations = 1.6%, smoothing ~= 0.112)
To avoid too much smoothing with 'mzv', suggested max_accel <= 5300 mm/sec^2
Fitted shaper 'ei' frequency = 52.6 Hz (vibrations = 2.8%, smoothing ~= 0.116)
To avoid too much smoothing with 'ei', suggested max_accel <= 5200 mm/sec^2
Fitted shaper '2hump_ei' frequency = 63.6 Hz (vibrations = 0.0%, smoothing ~= 0.133)
To avoid too much smoothing with '2hump_ei', suggested max_accel <= 4500 mm/sec^2
Fitted shaper '3hump_ei' frequency = 76.4 Hz (vibrations = 0.0%, smoothing ~= 0.140)
To avoid too much smoothing with '3hump_ei', suggested max_accel <= 4300 mm/sec^2
Recommended shaper is 2hump_ei @ 63.6 Hz

# Tuning Notes - Sanity Check

- Solid Print Table/Surface
- Square and Measure Frame Corners
- Greased Rails
- Belt Tension
- Heat Soak Tightening
- Hotend PID Tuning
- Bed PID Tuning
- Quad Gantry Level
- Bed Mesh
- Extruder Calibration
- Wash Build Surface
- First Layer Z Height
- Pressure Advance Tuning
- Extrusion Multiplier Tuning
- PA / EM Oddities
- Cooling and Layer Times
- Retraction
- Infill/Perimeter Overlap
- Stepover
