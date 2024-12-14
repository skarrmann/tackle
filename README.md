# Tackle Keyboard

Tackle is a wearable 48 key ortholinear keyboard, powered by a bluetooth-enabled Pro Micro compatible dev board.

It uses Choc v1 keyswitches with 18mm x 17mm spacing.

Tackle is strapped to your torso so you can type anywhere your hands are free.

## Project structure

* [`gerbers`](gerbers): Gerber files for PCB manufacturing
* [`graphics`](graphics): Source assets for PCB silkscreen
* [`kicad`](kicad): KiCad project files (schematics and PCB designs)
* [`kicad-libraries`](kicad-libraries): KiCad components and footprints
* [`images`](images): Images for project documentation

## PCBs

**Each build uses five copies of the PCB.**

One PCB is used as the logical PCB. Three PCBs are used as cutouts for the microcontroller dev board and battery. A final PCB is used as the bottom plate. All the PCBs are screwed directly together.

## Keyboard firmware

* ZMK
    * Tackle shield definition is in [skarrmann's zmk-config](https://github.com/skarrmann/zmk-config)

## Bill of materials

Part | Purpose | Quantity | Notes
---- | ------- | -------- | ---------
Main PCB  | logical PCB, case plates | 5 | Send Gerber zip files to [JLCPCB](https://jlcpcb.com/)
Bluetooth Pro Micro | Microcontroller board | 1 | nice!nano or SuperMini nRF52840
303450 LiPo Battery | Powers the wireless keyboard | 1 | JST PH 2.0 connector, ~5cm wire length
S2B-PH-K-S connector | JST PH 2.0 battery connector | 1 |
SS12D00 | On/Off switch | 1 |
6mm x 6mm push button | Reset button | 1 |
1N4148 SOD-123 | Diodes for keyboard row-column matrix | 34 |
Choc v1 Keyswitches |  | 48 |
Choc v1 Keycaps |  | 48 | Use keycaps which fit 18mm x 17mm spacing
M2 10mm screws | Screws PCBs together | 10 |
M2 nuts | Holds the top screws between the PCBs | 5 |
[Peel-a-way Sockets and Pins](https://ringerkeys.com/collections/modders-tools/products/peel-a-way-sockets) | socket dev board to PCB | 2 strips of 12 pins/sockets | May use other low profile sockets which give less than ~4.8 mm total height.

## PCB manufacturing settings

These are the manufacturing settings I used when ordering from JLCPCB:

* **Base Material**: FR4
* **Layers**: 2
* **Dimensions**: (whatever the gerber file specifies)
* **PCB Qty**: 5
* **Different Design**: 1
* **Delivery Format**: Single PCB
* **PCB Thickness**: 1.6
* **PCB Color**: Black
* **Silkscreen**: White
* **Surface Finish**: LeadFree HASL-RoHS
* **Outer Copper Weight**: 1 oz
* **Gold Fingers**: No
* **Confirm Production File**: No
* **Flying Probe Test**: Fully Test
* **Castellated Holes**: No
* **Mark on PCB**: Remove Mark

## Build tips

* Before starting, check if the PCBs are warped, and bend them to be perfectly flat before soldering.
* Make sure the diodes are oriented correctly, cathode on the side with the line! Once the keyswitches are soldered in, you won't be able to get to them anymore.
* Make sure the dev board is placed **components side up**. The pinout labels printed on the PCB should align with those printed on the dev board.
    * ![Tackle keyboard build, dev board components side up](images/tackle-dev-board-install.jpg)
* While soldering the the battery connector, reset button, and power switch, use tape to temporarily hold them in place. Solder just one leg of each of these components, make sure they are aligned correctly, and then solder the other legs. Clip the legs of the power switch since they are longer than the bottom plate.
    * ![Tackle keyboard build, battery connector, reset button, power switch](images/tackle-reset-button-power-switch-install.jpg)
* Don't plug in the battery until you're done soldering everything! **MAKE SURE THE BLACK WIRE (-) IS ON TOP AND THE RED WIRE (+) IS ON BOTTOM, OR YOU'LL FRY YOUR DEV BOARD!** Use tape to secure the battery and its wires.
    * ![Tackle keyboard build, battery taped in place](images/tackle-battery-install.jpg)

## Revision history

* Tackle 1.1 (2024-12-13)
    * Widen cutout for dev board and battery, to make sawing PCBs easier
* Tackle 1.0 (2024-11-28)
    * Initial Choc switch PCB design