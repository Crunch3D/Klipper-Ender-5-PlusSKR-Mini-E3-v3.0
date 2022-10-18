# Klipper Config: Ender 5 Plus w/ SKR Mini E3 v3.0

Out of the box, my Klipper configuration supports the following setup. This includes pre-calulated stepper motor voltages, and other E5+ specific settings. Use this configuration as a baseline, and tweak to your heart's desire.

- Ender 5 Plus
- Mainboard: BTT SKR Mini E3 v3.0
- BLTouch probe
- Filament runoff sensor switch (removed)
- Stock rails
- Stock Creality stepper motors (X/Y/Z)
- Bondtech BMG Extruder (right variant, unmirrored)
- Phaetus Dragonfly BMS Hotend
- Touchscreen flashed with Desuuuu's DGUS firmware
- BantaMount in a bowden configuration
- Pressure Advance is ready to go, configure your own settings
- ADXL345 for input shaping calibration

## Printing Profiles

Provided for both PrusaSlicer and SuperSlicer, with sensible defaults. Note that these also include my extrusion multiplier values, so you may want to reset these to 1.0 and tune for your filaments.

## Start/End Gcode

If not using the included SuperSlicer profile, configure the following:-

### Start Gcode

#### SuperSlicer:
```
PRINT_START BED={first_layer_bed_temperature[initial_extruder]} EXTRUDER={first_layer_temperature[initial_extruder]+extruder_temperature_offset[initial_extruder]}
```

#### PrusaSlicer:
```
PRINT_START BED={first_layer_bed_temperature[0]} EXTRUDER={first_layer_temperature[0]}
```

### End Gcode

```
PRINT_END
```

## Supported Extruders
- Creality Stock (comes with the printer, all-metal extruder also supported)
- Bondtech BMG with NEMA17 "pancake" stepper motor

## Supported Part Cooling
- Creality Stock
- BantaMount w/ single 5015 fan (current config)

No changes should be required to move from Creality's stock part cooling to a BantaMount.

## Touchscreen Display

- Connects with the [Klipper firmware by Desuuuu](https://github.com/Desuuuu/klipper/tree/dgus-display). The `dgus-display` branch is known compatible.
- Wire as follows, using the [SKR Mini E3 v3.0 Pinout Diagram](https://github.com/bigtreetech/BIGTREETECH-SKR-mini-E3/blob/master/hardware/BTT%20SKR%20MINI%20E3%20V3.0/Hardware/BTT%20E3%20SKR%20MINI%20V3.0_PIN.pdf) as reference.

| SKR Mini E3 v3.0 Pins | Touchscreen Pins |
| ----------------------|------------------|
| TFT +5V               | +5V              |
| TFT GND               | GND              |
| TFT TX2               | RX2              |
| TFT RX2               | TX2              |

### Flashing the Touchscreen Firmware

1. Download the [known compatible screen firmware](https://github.com/Desuuuu/DGUSPrinterMenu/releases/tag/1.0.0)
2. Format an SD Card (preferably smaller than 16GB) with the FAT32 filesystem
3. Extract the contents of touchscreen firmware directly to the root of the SD card
4. Disconnect the Raspberry Pi from the printer before turning on
5. Insert the SD card into the rear of the touchscreen
6. Turn on the printer. After a few seconds, the screen should turn blue. Flashing has begun
7. Wait for the final message to read `END` before turning off the printer, and removing the SD card
8. Reconnect the Raspberry Pi, and turn on the printer

If all is well, you should now have a printer icon visible on the touchscreen. Continue by flashing Desuuuu's Klipper to the SKR Mini E3.

### Flashing Desuuuu's Klipper Branch

Assuming you already have Klipper built for the printer using the official repository, we can switch to Desuuuu's branch and build that.

```bash
sudo systemctl stop klipper
cd ~/klipper
git remote add desuuuu https://github.com/Desuuuu/klipper.git
git fetch desuuuu dgus-display
git checkout -b dgus-display desuuuu/dgus-display
make menuconfig # Configure as per BTT's instructions
make -j4
```

Copy the `klipper.bin` file to the SD card from the build directory, renaming it as `firmware.bin`. Insert into the SKR Mini, turn on the printer, wait 5 seconds, then turn off.
Validate that the firmware was flashed by re-inserting the SD card into your computer. The firmware.bin file should have been renamed. If so, the flash was successful.

Start Klipper again:-

```bash
sudo systemctl restart klipper
```

> **Be sure that the `[dgus_display]` section of printer.cfg is uncommented. When Klipper starts back up, the display should now be usable.**

## Compatibility Notes

### Bondtech BMG Extruder

Does not align with the filament sensor, so I removed the filament sensor. One day I'll get around to building a compatible mounting bracket..

### Bondtech NEMA17 25mm "pancake" stepper motors

Creality wire the middle two pins on the motor connectors backwards. You will need to switch these two pins around for these motors to function correctly. Otherwise, they will vibrate and heat up very quickly, possibly damaging them.

### Phaetus Dragonfly BMS Hotend

Clearance from the gantry is minimal with the stock part cooling setup, and may cause the silicone sock to be unremovable. You can add some washers as a spacer, but I chose to use the BantaMount which doesn't have this issue. For the BantaMount, extra clearance is needed at the rear of the hotend mount. If you need this file, please open a new issue and I will get right on it.

## Extra Notes

My original wiring follows the video tutorial by [Kersey Fabrications](https://www.youtube.com/watch?v=VAXY3GkgTyY). I do not use Kersey's firmware builds, instead I've opted to run Klipper firmware directly from a source compile.

If you would like help with debugging your own setup, don't hesitate to open an issue.

Happy printing!

# Further Reading

- [Extruder Calibration Guide (rotation_distance)](https://www.klipper3d.org/Rotation_Distance.html)
- [Stepper Motor Driver Currents (run_current)](https://docs.vorondesign.com/community/howto/120decibell/calculating_driver_current.html)
- [SKR Mini E3 v3.0 pinout diagram](https://github.com/bigtreetech/BIGTREETECH-SKR-mini-E3/blob/master/hardware/BTT%20SKR%20MINI%20E3%20V3.0/Hardware/BTT%20E3%20SKR%20MINI%20V3.0_PIN.pdf)
- [gh/KersyFabrications](https://github.com/KerseyFabrications)
- [AndrewEllis93's Print-Tuning-Guide](https://github.com/AndrewEllis93/Print-Tuning-Guide)
- [Vector3D's Califlower (for X/Y stepper calibration)](https://vector3d.co.uk/product/vector-3d-printer-calibration-and-test-suite/)

# Donations

Found this repo helpful? Buy me a [Ko-Fi](https://ko-fi.com/tinyfluffs_).

# License

MIT License
