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
- Touchscreen display **removed** due to firmware limitations
- BantaMount in a bowden configuration
- Pressure Advance is ready to go, configure your own settings
- ADXL345 for input shaping calibration

## Printing Profiles

Provided for SuperSlicer with sensible defaults.

## Supported Extruders
- Creality Stock (comes with the printer, all-metal extruder also supported)
- Bondtech BMG with NEMA17 "pancake" stepper motor

## Supported Part Cooling
- Creality Stock
- BantaMount w/ single 5015 fan (current config)

No changes should be required to move from Creality's stock part cooling to a BantaMount.

## Compatibility Notes

### Bondtech BMG Extruder

1. Does not align with the filament sensor, so I removed the filament sensor. One day I'll get around to building a compatible mounting bracket..

### Bondtech NEMA17 25mm "pancake" stepper motors

Creality wire the middle two pins on the motor connectors backwards. You will need to switch these two pins around for these motors to function correctly. Otherwise, they will vibrate and heat up very quickly, possibly damaging them.

### Phaetus Dragonfly BMS Hotend

Clearance from the gantry is minimal with the stock part cooling setup, and may cause the silicone sock to be unremovable. You can add some washers as a spacer, but I chose to use the BantaMount which doesn't have this issue.

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
