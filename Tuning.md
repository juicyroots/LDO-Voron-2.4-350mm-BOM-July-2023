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

## Input Shaping - All Axis Tune
Test the accelerometer
```gcode
ACCELEROMETER_QUERY
```
Run Calibration
```gcode
SHAPER_CALIBRATE
```

## Input Shaping - X/Y Axis Tune

```gcode
TEST_RESONANCES AXIS=X
```
```gcode
TEST_RESONANCES AXIS=Y
```
After completing these scripts, Klipper will store the results in two CSV files: “/tmp/resonances_x_*.csv” and “/tmp/resonances_y_*.csv”.

## Input Shaping - Data Analysis
```
~/klipper/scripts/calibrate_shaper.py /tmp/resonances_x_*.csv -o /tmp/shaper_calibrate_x.png
~/klipper/scripts/calibrate_shaper.py /tmp/resonances_y_*.csv -o /tmp/shaper_calibrate_y.png
```
