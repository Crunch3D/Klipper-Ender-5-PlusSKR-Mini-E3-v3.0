<img src="https://raw.githubusercontent.com/tinyfluffs/klipper_ender_5_plus/main/printer.jpg" width="500" />

# Klipper Config: Ender 5 Plus w/ SKR Mini E3 v3.0

Out of the box, my Klipper configuration supports the following setup. As my printer receives upgrades, older components will get pushed out into separate config files. You may find these useful if your configuration differs from my own.

- Ender 5 Plus
- Mainboard: BTT SKR Mini E3 v3.0
- BLTouch probe
- Filament runoff sensor switch
- Stock rails
- Stock Creality stepper motors (X/Y/Z)
- Bondtech BMG Extruder (right variant, unmirrored)
- Phaetus Dragonfly BMS Hotend
- Touchscreen display **disabled** due to firmware limitations
- Hero Me Gen6 (dual with BLTouch) part cooling
- ADXL345 for input shaping calibration

## Supported Extruders
- Creality Stock (comes with the printer, all-metal extruder also supported)
- Bondtech BMG with NEMA17 "pancake" stepper motor

## Supported Part Cooling
- Creality Stock
- Hero Me Gen6 (dual 4020 radial fans)

## Printable upgrades

None required for stock. Check back later for other mods.

## Compatibility Notes

### Bondtech BMG Extruder

1. Does not align with the filament sensor. An adapter plate is required (coming soon).

2. A screw to the mounting plate interfers with the clearance on the top of the extruder housing. It's fine to remove it, but that's just a [bodge](https://www.youtube.com/watch?v=lIFE7h3m40U).

### Bondtech NEMA17 25mm "pancake" stepper motors

Creality wire the middle two pins on the motor connectors backwards. You will need to switch these two pins around for these motors to function correctly. Otherwise, they will vibrate and heat up very quickly, possibly damaging them.

### Phaetus Dragonfly BMS Hotend

Clearance from the gantry is minimal, and may cause the silicone sock to be unremovable. According to Andrew "[MediaMan3D](https://www.printables.com/social/56045-mediaman3d/about)", this could be fixed by reversing the hotend. I have yet to test this.

## Extra Notes

My original wiring follows the video tutorial by [Kersey Fabrications](https://www.youtube.com/watch?v=VAXY3GkgTyY). I do not use Kersey's firmware builds, instead I've opted to run Klipper firmware directly from a source compile.

If you would like help with debugging your own setup, don't hesitate to open an issue.

Happy printing!

# Further Reading

- [Extruder Calibration Guide (rotation_distance)](https://www.klipper3d.org/Rotation_Distance.html)
- [Stepper Motor Driver Currents (run_current)](https://docs.vorondesign.com/community/howto/120decibell/calculating_driver_current.html)
- [SKR Mini E3 v3.0 pinout diagram](https://github.com/bigtreetech/BIGTREETECH-SKR-mini-E3/blob/master/hardware/BTT%20SKR%20MINI%20E3%20V3.0/Hardware/BTT%20E3%20SKR%20MINI%20V3.0_PIN.pdf)
- [gh/KersyFabrications](https://github.com/KerseyFabrications)

# Donations

Found this repo helpful? Buy me a [Ko-Fi](https://ko-fi.com/tinyfluffs_).

# License

MIT License
