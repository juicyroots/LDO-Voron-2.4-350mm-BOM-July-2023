## KIAUH

Step 1:
To download this script, it is necessary to have git installed. If you don't have git already installed, or if you are unsure, run the following command:
```
sudo apt-get update && sudo apt-get install git -y
```
Step 2:
Once git is installed, use the following command to download KIAUH into your home-directory:
```
cd ~ && git clone https://github.com/th33xitus/kiauh.git
```
Step 3:
Finally, start KIAUH by running the next command:
```
./kiauh/kiauh.sh
```

## Secondary MCU Software Install

```
sudo apt update
sudo apt install python3-numpy python3-matplotlib libatlas-base-dev
```

```
~/klippy-env/bin/pip install -v numpy
```

```
cd ~/klipper/
sudo cp ./scripts/klipper-mcu.service /etc/systemd/system/
sudo systemctl enable klipper-mcu.service
```

```
cd ~/klipper/
make menuconfig
```

```
sudo service klipper stop
make flash
sudo service klipper start
```

Make sure the Linux SPI driver is enabled by running sudo raspi-config and enabling SPI under the "Interfacing options" menu.

## List GPIO Info

To install the Linux GPIO character device - binary on a debian based distro like octopi run:
```
sudo apt-get install gpiod
```

To check available gpiochip run:
```
gpiodetect
```

To check the pin number and the pin availability tun:
```
gpioinfo
```

## List Serial Devices

List serial devices on Pi, such as the Octopus and Input Shaper
```
ls /dev/serial/by-id/*
```

## Cura Setup

### Set Variables

In Cura go to "Settings" -> "Printer" -> "Manage printers" -> "Machine settings" -> "Start G-code" and update it to
```
print_start EXTRUDER={material_print_temperature_layer_0} BED={material_bed_temperature_layer_0} CHAMBER={build_volume_temperature}
```

### Set Timelapse

Click on Extensions -> Post Processing -> Modify G-Code.
Navigate to Add a script -> Insert at layer change -> G-code to insert
```
TIMELAPSE_TAKE_FRAME
```

## Raspberry Pi Webcam

```
v4l2-ctl --list-devices
```
```
ls /dev/video*
```
```
lsusb
```


## Misc
```
/home/pi/crowsnest/tools/dev-helper.sh -c
```

##Logitech C920
```
                     brightness (int)  : min=0 max=255 step=1 default=-8193 value=128
                       contrast (int)  : min=0 max=255 step=1 default=57343 value=128
                     saturation (int)  : min=0 max=255 step=1 default=57343 value=128
 white_balance_temperature_auto (bool) : default=1 value=1
                           gain (int)  : min=0 max=255 step=1 default=57343 value=0
           power_line_frequency (menu) : min=0 max=2 default=2 value=2
      white_balance_temperature (int)  : min=2000 max=6500 step=1 default=57343 value=4000 flags=inactive
                      sharpness (int)  : min=0 max=255 step=1 default=57343 value=128
         backlight_compensation (int)  : min=0 max=1 step=1 default=57343 value=0
                  exposure_auto (menu) : min=0 max=3 default=0 value=3
              exposure_absolute (int)  : min=3 max=2047 step=1 default=250 value=250 flags=inactive
         exposure_auto_priority (bool) : default=0 value=1
                   pan_absolute (int)  : min=-36000 max=36000 step=3600 default=0 value=0
                  tilt_absolute (int)  : min=-36000 max=36000 step=3600 default=0 value=0
                 focus_absolute (int)  : min=0 max=250 step=5 default=8189 value=0 flags=inactive
                     focus_auto (bool) : default=1 value=1
                  zoom_absolute (int)  : min=100 max=500 step=1 default=57343 value=100
```
