
DrmDmp64_mass is a mass storage device firmware for the DreamDumper64 project.

This is a fork of the original project that's located here:
https://github.com/nopjne/drmdmp64_mass


This unofficial version produces:
- The rom that can be extracted in both .v64 (byteswapped) and .z64 (big endian) formats.
- .sra, .fla and .eep save files compatible with various pj64/mupen emulators.
- .ram, .flash and .eeprom save files compatible with ares.

The .ram, .flash and .eep save files can also be used with gopher64, but the .ram/.flash files must be renamed to .sra/.fla before use. DO NOT use the pj64/mupen .sra/.fla files with gopher64.

---

I've also made an eeprom save fix for the dumper that's sold on various websites that looks like this:
![alt text](https://github.com/mikehattsu/drmdmp64_mass/blob/master/dumper.jpg?raw=true)

You need to turn the cartridge reader upside down and have it so the cartridge port is on the top and the Pi Pico clone at the bottom. You then need to wire and connect the 5th pin counting from the bottom left of the cartridge port (aka pin 21 when seen from the right side up EEPROM_DAT) to the pin with the number 16 on the Pi Pico clone board, and the 7th pin counting from the bottom left (aka pin 19 when seen from the right side up CIC_11) to the pin with the number 17 on the Pi Pico clone board:
![alt text](https://github.com/mikehattsu/drmdmp64_mass/blob/master/dumperfix.jpg?raw=true)

Make sure you double check that the pins on whatever Pi Pico clone you have matches. The 2 pins that I connected on mine says 16 and 17 on the top of the board.


How to build (this project depends on tinyusb):
```
git submodule update --init
mkdir build
cd build
cmake ..
cmake --build .
```

How to update the firmware:
```
Hold the bootsel button down while connecting USB to PC.
Copy uoDrmDmp64_mass.uf2 to the RPI-RP2 drive that shows up.
Wait for the device to reboot.
```

How to use:
```
1. Insert cartridge into the cartridge slot.
2. Connect USB to PC.
3. Navigate to the drive, use normally.
```

NOTE: When swapping cartridges make sure you disconnect and eject the drive, otherwise the operating system may cache the files from the previous cartridge.
