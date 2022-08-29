# Electrical Specifications
 - Input voltage: DC12V-DC48V 5A-15A
 - Maximum total power is 180W@12V, 360W@24V or 720W@a48V

## Inputs:
 - FAN_IN for fans. This connection is optional.
 - HEAT_IN for heated bed. This connection mandatory if you use a heated bed.
 - HOT_IN for hotend. This connection is mandatory.
 - DRI_IN for the drivers. This connection is optional.
 - PWR_IN as a general power input. This connection is mandatory.

## Considerations
 - Standard 2.54mm Jumpers are rated for 5A or 250V max
 - When adding buck/boost converts from the main power supply to an input bare in mind that those are not working at 100% efficiency, so rather over- than underspec those
 - When using multiple power supplies (generally not recommended, only do this if you know exactly what you are doing), make sure to decouple the power supplies
 - If possible, use a power supply that matches the components with the highest combined power draw and use buck/boost converters from there

## Fan Power:
All 6 fans come with separate jumpers for FAN_IN or 5V (the board has an internal buck converter to 5V). This is needed in case the printer uses both 12V fans and 5V fans.

## Heatbed Power
Since the heatbed can exceed the 5A rating of the jumpers, there is a separate heatbed input, which has to be wired up manually in case a heated bed is used.

## Hotend Power
To my knowledge the highest power hotend is the SuperVolcano from E3D, which draws 80W@12V, resulting in a max current of almost 7A. Thus both additional heater inputs
come with a single separate power input.

## Driver Power
Each driver has a maximum rating of 3A due to its socket. Thus, each individual driver has a jumper to select between DRI_IN and PWR_IN.

## ESP32
The MCU can either be powered via USB or the internal buck converter, chosen by the corresponding jumper.