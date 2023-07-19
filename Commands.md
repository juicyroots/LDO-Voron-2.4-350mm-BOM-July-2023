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
