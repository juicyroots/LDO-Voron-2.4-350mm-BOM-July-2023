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

## Set variables in Cura for print_start macro.

In Cura go to "Settings" -> "Printer" -> "Manage printers" -> "Machine settings" -> "Start G-code" and update it to
```
print_start EXTRUDER={material_print_temperature_layer_0} BED={material_bed_temperature_layer_0} CHAMBER={build_volume_temperature}
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
