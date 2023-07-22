In Cura go to "Settings" -> "Printer" -> "Manage printers" -> "Machine settings" -> "Start G-code" and update it to:
```print_start EXTRUDER={material_print_temperature_layer_0} BED={material_bed_temperature_layer_0} CHAMBER={build_volume_temperature}```

Raspberry Pi Webcam

v4l2-ctl --list-devices
ls /dev/video*
lsusb
