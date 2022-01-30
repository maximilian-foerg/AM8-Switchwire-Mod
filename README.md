# AM8 Switchwire Mod

## Table of Contents
1. [Introduction](#introduction)
2. [Renders](#renders)
3. [Some Facts](#some-facts)
4. [Why Core XZ?](#why-core-xz)
5. [Printing Tips](#printing-tips)
6. [Firmware Tips](#firmware-tips)
7. [FAQ](#faq)
8. [BOM (Bill of Materials)](#bom)

## Introduction
This is a Core XZ upgrade for the popular [AM8 frame](https://www.thingiverse.com/thing:2263216) inspired by the Voron Switchwire, which also makes the AM8 compatible with VORON Afterburner.

![Render 01](Images/Render%2001.png)
![Render 02](Images/Render%2002.png)

In case you don't know about the Voron Project, check it out at https://www.vorondesign.com/. They design outstanding open-source 3D printers, and if you're looking for a *real* upgrade, I'd suggest you build a Voron instead. It probably won't get any better.
But if you enjoy tinkering on your cheap 3D printer just like me, this mod could be something for you.

## Renders
![Render 03](Images/Render%2003.png)
![Render 04](Images/Render%2004.png)
![Render 05](Images/Render%2005.png)
![Render 06](Images/Render%2006.png)
![Render 07](Images/Render%2007.png)
![Render 08](Images/Render%2008.png)

## Some Facts
* Build volume is 220x220x220mm with Anet A8 print head and up to 220x220x270mm with VORON Afterburner.
* The dimensions of the aluminum extrusions are the same as for the AM8.
* This upgrade uses as many of the original Anet A8 and AM8 parts as possible. Still, you will have to buy some stuff. Have a look at the [BOM](#bom).
* Although I redesigned every part, the Y axis did not change compared to the AM8. So if you already have an AM8, you can continue to use your Y axis.

**_CAUTION!_**
* Altough it would work, **you better not use the original Anet A8 board for this mod**. The Anet A8 board is designed to have two motors connected to the stepper motor driver for the Z axis. Many older versions of the board do not allow you to regulate the voltage for these motors. Since this mod only requires one stepper motor for the Z axis, it would get twice as much current as it should. This could destroy the motor. But it is a good idea to change to a more modern board anyway - especially TMC stepper motor drivers will raise the printer to a new level. My recommendation is the Bigtreetech SKR mini E3 V2. At first glance it may seem expensive, but it has TMC 2209 drivers integrated and is therefore relatively cheap. The TMC drivers allow the voltage for each stepper motor to be controlled individually by software.
* You will have to flash a new firmware (and for the time being, configure it yourself). One possibility is to use [Marlin](https://marlinfw.org/), which can be configured for Core XZ motion systems. My recommendation is [Klipper](https://www.klipper3d.org/) together with a Raspberry Pi running [Mainsail](https://docs.mainsail.xyz/). Klipper runs all calculations on the much more computationally powerful Raspberry Pi, so you can use it to compensate for the weak hardware of the original Anet A8 or other 3D printer controller boards.

## Why Core XZ?
3D printers make fast movements, so it is a great advantage if moving parts have the lowest possible mass. This is why the Core XY architecture was developed, where two stepper motors can move the print head in two directions through a sophisticated belt drive without having to move themselves. Well-known DIY Core XY printers are, for example, the [Voron 0](https://www.vorondesign.com/voron0.1), [Voron Trident](https://www.vorondesign.com/voron_trident) and [Voron 2](https://www.vorondesign.com/voron2.4), or the very popular [Hypercube](https://www.thingiverse.com/thing:1752766) and [Hypercube Evolution](https://www.thingiverse.com/thing:2254103).
However, a Core XY motion system requires a cube-shaped frame, which we do not have with the AM8. Converting the frame would contradict the sense of an "upgrade" and would rather be a completely new printer. Therefore, the [Voron Switchwire](https://www.vorondesign.com/voron_switchwire) gave me the idea to implement the Core XY architecture rotated by 90 degrees as Core XZ architecture on the AM8. This has the following advantages:
* The weight of the X axis is now balanced, because there is no longer a motor on one side.
* The X axis becomes lighter since all stepper motors are fixed to the frame.
* You get rid of the threaded spindles.
* You can make movements in the Z direction just as fast as in the X and Y directions.
* You need one less stepper motor.

## To check before modding your printer
### Extrusions
This mod is using the same aluminium extrusions as the AM8 mod. Extrusions used for designing the parts are Misumi HFSB5-2040, but any 2020 B-type nut 6 extrusions will work.
Make sure your extrusions have these lenghts:
* 3 * 310mm
* 2 * 340mm
* 2 * 440mm
A few mm more or less will work too, as long as the deviations are consistent (f.e. 3 * 313mm is fine, but 2 * 310mm and 1 * 313mm is not).

### Linear Rods
This mod assumes that the original linear rods of the Anet A8 are used. Their lengths are:
* 2 * 436mm
* 4 * 380mm
The required length of the X axis rods is the length of your shortest extrusion + 115mm. So for the spec 310mm extrusions, rods of 425mm in length are required. Longer rods will stick out on the sides, but that's ok.

## Printing Tips
* A number at the end of each file name indicates how often the part must be printed (no number = print it once).
* The `[A]` tag at the beginning of a file name means that this is an accent part. You can print it in an accent color if you like.
* All parts are already oriented for the best printing position. Do not change the orientation. They are specially designed and oriented to be printed without any supports.
* The parts HAVE to be printed in ABS, PETG or another material that can withstand mechanical stress. PLA is NOT an option. Avoid PETG if you have an enclosure for your printer or want to build one, because it bends at high ambient temperatures ("heat creep"). ABS is the best way to go here.
* The parts are designed to be printed with a 0.4mm nozzle at 0.2mm layer height. I recommend the following slicer settings:
  * 4 walls, 5 bottom layers, 5 top layers
  * 40% cubic or gyroid infill
  * No supports
  * No raft
  * Brim or skirt as needed
* Before printing, calibrate your extruder steps and the temperature and flow rate for your specific filament. Get rid of any strining, warping and elephant food on your prints. There are tons of tutorials on the web on how to do each of that.

## Firmware Tips
This sections contains some tips for firmware configuration. Note that the firmware directory contains some configurations.

### General
* Min. Y position: 0
* Max. Y position: 220
* Min. Z position: 0
* Z hop before homing: 5
* DO NOT disable stepper motors (g-code command `M84`) after prints. Print head would fall down on print or bed.
### Anet A8 print head
* Min. X position: -24
* Max. X position: 225
* Max. Z position: 220
* Choose a z hop > 30 if using a level probe instead of the Z endstop switch. This is necessary because if the printhead falls next to the bed after power off, the nozzle protrudes about 30mm below the bed.
### VORON Afterburner print head
* Min. X position: -13
* Max. X position: 240
* Max. Z position: 250

## FAQ
### Why are there three versions of the XZ Axis X Rod Mount (40, 45 and 46mm)?
There are two versions of the Anet A8, one with 45mm spacing between the linear rods of the X-axis, and one with 46mm spacing. This also means that the ball bearings on the print head are either 45mm or 46mm apart. You need to find out which version of the Anet A8 you have, and print the appropriate version of the rod mounts. The 40mm rod mounts are needed for the VORON Afterburner.

## BOM
The following lists specify which additional parts you'll need to upgrade your existing printer to this mod. Note that there are alternative standards for each DIN standard (for example, the corresponding ISO standard). These are just the standards I used to design the parts. If you decide to use other nuts and bolts, check the dimensions beforehand. This is especially important for nuts and countersunk screws, less so for button head screws and cylindrical head screws.

### If you want to keep your Y axis:
| Item | Amount | Comment |
| ---- | :----: | ------- |
| DIN 934 M2 nut | 4 | Only 2 if you're not using the Z endstop |
| DIN 912 M2x10 screw | 4 | Only 2 if you're not using the Z endstop |
| ISO 7380 M3x25 screw | 4 |
| ISO 7380 M3x30 screw | 20 |
| DIN 912 M3x30 screw or any other M3 screw with 30-40mm in length | 1 | Only if you ARE using the Z endstop |
| ISO 7380 M5x10 screw | 21 | Only 20 if you're not using the Z endstop |
| M5 slot nut for your type of aluminium extrusions | 21 | Only 20 if you're not using the Z endstop |
| DIN 988 6x3x0.5 precision shim ring | 16 | YES, measurements are important, and NO, you can't just use cheap M3 washers |
| GT2 16T timing pulley | 1 | 3 needed in total, but 2 are already included with Anet A8 |
| GT2 timing belt with 6mm width | ~5m | Glassfiber belt recommended, and it's highly recommended to replace the Y axis belt too |
| F623 ball bearing | 16 |
| Threaded heat insert M3x5x4 | 17 | The ones VORON printers use; Only 16 if you're not using the Z endstop |

### If you want to upgrade your Y axis, you'll ALSO need:
| Item | Amount | Comment |
| ---- | :----: | ------- |
| DIN 912 M2x14 screw | 2 |
| DIN 934 M2 nut | 2 |
| DIN 934 M3 nut | 1 |
| ISO 7380 M3x16 screw | 1 | DIN 912 or other button head would work too, length should be 16-18mm |
| ISO 7380 M3x30 screw | 4 |
| ISO 7380 M5x10 screw | 12 | You may already have these from your AM8 |
| M5 slot nut for your type of aluminium extrusions | 12 | You may already have these from your AM8 |
| DIN 988 6x3x0.5 precision shim ring | 2 | Again, measurements are important |
| F623 ball bearing | 2 | Came with A8 |

### Print Heads
#### Original Anet A8
| Item | Amount |
| ---- | :----: |
| DIN 934 M3 nut | 2 |
| DIN 912 M3x12 screw | 2 |

#### VORON Afterburner
For the adapter and belt clamp, you need (some may also be listed in the official sourcing guide):
| Item | Amount | Comment |
| ---- | :----: | ------- |
| DIN 934 M3 nut | 2 |
| DIN 912 M3x12 screw | 4 |
| DIN 912 M3x20 screw | 2 | Only if you are using the PL-08N probe |
| DIN 912 M3x30 screw | 2 |
| DIN 912 M3x40 screw | 3 |
| Threaded heat insert M3x5x4 | 9 | Only 7 if you're NOT using the PL-08N probe |
| LM8LUU linear bearing | 2 | Misumi recommended. Short LM8UU bearings of Anet A8 print head NOT compatible. |

For the rest of the items, please refer to the official VORON sourcing guide: https://www.vorondesign.com/sourcing_guide (select 'VORON Afterburner' at the bottom).

For the printed parts, you can download Switchwire's repository: https://github.com/VoronDesign/Voron-Switchwire (click on _Code_ -> _Download ZIP_). You will find the STLs under `STL/Gantry/XZ_Axis/X_Carriage`.
Print the following:
* `[a]_blower_housing_front.stl`
* `blower_housing_rear.stl`
* `hotend_fan_mount.stl`
* `Direct_Feed/[a]_connector_cover.stl` (If you like, but it isn't really compatible)
* `Direct_Feed/[a]_guidler.stl`
* `Direct_Feed/[a]_latch.stl`
* `Direct_Feed/[a]_latch_shuttle.stl`
* `Direct Feed/extruder_body.stl`
* `Direct_Feed/extruder_motor_plate.stl`
* And every part under `Printheads/X` for print head X of your choice

### Accessories
Required parts for optional accessories.

#### Print Head Cable Duct
| Item | Amount |
| ---- | :----: |
| ISO 7380 M5x10 screw | 1 |
| M5 slot nut for your type of aluminium extrusions | 1 |
| Zip tie | 3 |

#### Feet
| Item | Amount |
| ---- | :----: |
| ISO 7380 M5x10 screw | 4 |
| M5 slot nut for your type of aluminium extrusions | 4 |

#### LCD Controller Mount
| Item | Amount |
| ---- | :----: |
| ISO 7380 M3x10 screw | 2 |
| ISO 7380 or DIN 912 M3x12 screw | 4 |
| ISO 7380 M5x10 screw | 1 |
| M5 slot nut for your type of aluminium extrusions | 1 |
| Threaded heat insert M3x5x4 | 2 |

From the VORON Switchwire repository (link above), print everything...
* ... from directory `STL/Electronics/LCD/2004 (Prusa)` for LCD 2004 controller
* ... or from directory `STL/Electronics/LCD/Mini12864` for Mini 12864 LCD controller

#### Lightweight LM8UU Bearing Blocks
| Item | Amount | Comment |
| ---- | :----: | ------- |
| DIN 934 M4 nut | 4 | Per block |
| ISO 7380 M4x8 screw | 4 | Per block; Different screw heads are fine too (no countersunk) |

#### Other
* Print some **2020 Cable Clips** for cable management with zip ties.
* From the Switchwire repository ypu can print:
  * `STL/Electronics/skr_mini_e3_mount.stl` to mount the recommended SKR Mini E3 board
  * `STL/Electronics/raspberry_pi_mount.stl` to mount a Raspberry Pi
  * or `STL/Electronics/raspberry_pi_zero_shelf` to mount a Raspberry Pi Zero on the SKR Mini E3, which results in a cheap and compact control unit. There's a great [video](https://www.youtube.com/watch?v=AtW3GqkKUz8) about how to connect them.
