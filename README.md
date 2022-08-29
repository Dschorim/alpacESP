# alpacESP

Disclaimer: This is a WIP-repository and is not considered stable, but feel free to comment your ideas/concerns/whatever in the issues tab.

## What is this and why is it here?
The idea behind this project is to create a fully functional 3d printer driver board based on the ESP32-S3.
There are other similar projects like PandaZHU (https://github.com/markniu/PandaZHU), but that uses an additional GPIO expander with closed-source firmware.
Since the relatively new ESP32-S3 comes with more GPIO pins (34 if you use the ESP32-S3, ESP32-S3FN8 or ESP32-S3R2, so models without octal-SPI PSRAM),
which is enough for a full driver board without making too many sacrifices.

## Features
 - 8 drivers in SPI mode
 - 3 temperature probes
 - 3 endstops
 - 1 LCD via EXP1 and EXP2 with beeper
 - 1 BLTouch sensor connector
 - 1 runout sensor
 - 3 heater/hotend outputs
 - 3 PWM fans
 - 3 always-on fans

 - 2 separate power inputs (with either 12V, 24V or 48V; controlled with jumpers)
 - Input can either be up to 12V@20A, 24V@10A or 48V@5A (bare in mind that not all connected devices (drivers, fans, hotend, heatbed) can support all voltage levels, so be careful not to fry any components. But all soldered components can deal with all voltage levels)

See [Electrical](https://github.com/Dschorim/alpacESP/blob/main/Electrical.md) for more details

## Jumpers
 - set fan voltage to 5V (internal buck converter), 12V, 24V or 48V (cross-shaped jumper to make sure only one voltage is connected)

## Design Decisions
Using the drivers in SPI mode reduces the number of required pins from 17 in UART mode (8 drivers with 2 signal wires each + 1 common enable signal)
down to 12 (3 pins for MISO, MOSI, SCK, 1 pins for a common enable and 8 pins for individual CS pins).

I decided to sacrifice the onboard SD card, since the ESP32-S3 natively supports WiFi and the display can also support a SD card.
Support for external UART connections (for other displays for example) and support for the temperature/humidity sensors like the DTH11 was dropped as well
since those are rarely used and there were no pins left.


## Credits
Thanks to [markniu](https://github.com/markniu) for creating the PandaZHU project, which gives me inspiration and ideas for this project