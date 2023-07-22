List serial devices on Pi, such as the Octopus and Input Shaper
```
ls /dev/serial/by-id/*
```

Set variables in Cura for print_start macro.
In Cura go to "Settings" -> "Printer" -> "Manage printers" -> "Machine settings" -> "Start G-code" and update it to
```
print_start EXTRUDER={material_print_temperature_layer_0} BED={material_bed_temperature_layer_0} CHAMBER={build_volume_temperature}
```

Raspberry Pi Webcam

```
v4l2-ctl --list-devices
```
```
ls /dev/video*
```
```
lsusb
```