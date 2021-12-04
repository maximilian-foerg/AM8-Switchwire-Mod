# *UNDER DEVELOPMENT !!!*

# AM8 plus "Switchwire"
This is a Core XZ upgrade for the popular AM8 frame inspired by the Voron Switchwire.

![Render 01](Images/Render%2001.png)

In case you don't know about the Voron Project, check it out at https://www.vorondesign.com/. They design outstanding open-source 3D printers, and if you're looking for a *real* upgrade, I'd suggest you build a Voron instead. It probably won't get any better.
But if you enjoy tinkering on your cheap 3D printer just like me, this mod could be something for you.

## Features
### Core XZ using Anet A8's stock linear rods!
![Render 02](Images/Render%2002.png)
### Easily and precisely adjustable Z endstop!
![Render 03](Images/Render%2003.png)
### Compatible with VORON Afterburner!
![Render 04](Images/Render%2004.png)

## Some Facts
* Build volume is 220x220x220mm.
* The dimensions of the aluminum extrusions are the same as for the AM8.
* This upgrade uses as many of the original Anet A8 and AM8 parts a possible. Still, you will have to buy some stuff. Have a look at the [BOM](#bom).
* Although I redesigned every part, the Y axis did not change compared to the AM8. So if you already have an AM8, you can continue to use your Y axis.
* You can use the original Anet A8 board for this build, but you will have to flash another firmware. One possibility is to use [Marlin](https://marlinfw.org/), which can be configured for Core XZ motion systems. My recommendation is [Klipper](https://www.klipper3d.org/) together with a Raspberry Pi running [OctoPrint](https://octoprint.org/) or [Mainsail](https://docs.mainsail.xyz/). Klipper runs all calculations on the much more computationally powerful Raspberry Pi, so you can use it to compensate for the weak hardware of the original Anet A8 or other cheap 3D printer motherboards.

## Why Core XZ?
3D printers make fast movements, so it is a great advantage if moving parts have the lowest possible mass. This is why the Core XY architecture was developed, where two stepper motors can move the print head in two directions through a sophisticated belt drive without having to move themselves. Well-known DIY Core XY printers are, for example, the [Voron 0](https://www.vorondesign.com/voron0.1), [Voron Trident](https://www.vorondesign.com/voron_trident) and [Voron 2](https://www.vorondesign.com/voron2.4), or the very popular [Hypercube](https://www.thingiverse.com/thing:1752766) and [Hypercube Evolution](https://www.thingiverse.com/thing:2254103).
However, a Core XY motion system requires a cube-shaped frame, which we do not have with the AM8. Converting the frame would contradict the sense of an "upgrade" and would rather be a completely new printer. Therefore, the [Voron Switchwire](https://www.vorondesign.com/voron_switchwire) gave me the idea to implement the Core XY architecture rotated by 90 degrees as Core XZ architecture on the AM8. This has the following advantages:
* The weight of the X axis is now balanced, because there is no longer a motor on one side.
* The Z axis becomes lighter since all stepper motors are fixed to the frame.
* You get rid of the threaded spindles.
* You can make movements in the Z direction just as fast as in the X and Y directions.
* You need one less stepper motor.

## Printing Tips
* A number at the end of each file name indicates how often the part must be printed.
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
This sections contains some tips for firmware configuration.
### General
* Min. Y position: 0
* Max. Y position: 220
* Min. Z position: 0
* Max. Z position: 220
* DO NOT disable stepper motors (g-code command `M84`) after prints. Print head would fall down on print or bed.
### Anet A8 print head
* Min. X position: -23
* Max. X position: 225
* Max. velocity (all directions): 100 mm/s
* Z hop before homing: 35 mm
### VORON Afterburner print head
* Min. X position: -18
* Max. X position: 240
* Max. velocity (XY): 120 mm/s
* Max. velocity (Z): 100 mm/s
* Max. acceleration (XY directions): 3000 mm/s^2
* Max. acceleration (Z direction): 1000 mm/s^2
* Z hop before homing: 5 mm

## FAQ
### Could you provide a ready-to-go Marlin or Klipper config for this printer?
Sadly not. This is because I do not have the original Anet A8 board anymore. On my prototype, I'm using Klipper together with an MKS Gen L V1.0 Board, TMC 2208 stepper drivers, and a LJ18A3-8-Z/AX bed leveling probe. If you think my config can still be helpful to you, I'll be happy to send it to you. In the future I'd like to provide ready to use configurations for Marlin and Klipper, but I can't promise that.
### Why are there three versions of the XZ Axis X Rod Mount (40, 45 and 46mm)?
There are two versions of the Anet A8, one with 45mm spacing between the linear rods of the X-axis, and one with 46mm spacing. This also means that the ball bearings on the print head are either 45mm or 46mm apart. You need to find out which version of the Anet A8 you have, and print the appropriate version of the rod mounts. The 40mm rod mounts are needed for the VORON Afterburner.

## BOM
The following lists specify which additional parts you'll need to upgrade your existing printer to an AM8 plus. Note that there are alternative standards for each DIN standard (for example, the corresponding ISO standard). These are just the standards I used to design the parts. If you decide to use other nuts and bolts, check the dimensions beforehand. This is especially important for nuts and countersunk screws, less so for button head screws and cylindrical head screws.

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
| DIN 912 M3x25 screw | 1 | Any other M3 screw with 25mm+ in length would work too |
| ISO 7380 M3x25 screw | 1 |
| ISO 7380 M3x30 screw | 4 |
| DIN 912 M4x10 screw | 1 | Shorter screw does work too, but head is important |
| ISO 7380 M5x10 screw | 12 | You may already have these from your AM8 |
| M5 slot nut for your type of aluminium extrusions | 12 | You may already have these from your AM8 |
| DIN 988 6x3x0.5 precision shim ring | 2 | Again, measurements are important |
| F623 ball bearing | 2 | Came with A8 |
| Threaded heat insert M3x5x4 | 2 |

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

For the printed parts, you can download Switchwire's release repository: https://github.com/VoronDesign/Voron-Switchwire/releases/tag/V1.0. You will find the STLs under `STL/Gantry/XZ_Axis/X_Carriage`.
Print the following:
* `[a]_blower_housing_front.stl`
* `blower_housing_rear.stl`
* `hotend_fan_mount.stl`
* `Direct_Feed/[a]_guidler.stl`
* `Direct_Feed/[a]_latch.stl`
* `Direct_Feed/[a]_latch_shuttle.stl`
* `Direct Feed/extruder_body.stl`
* `Direct_Feed/extruder_motor_plate.stl`
* And every part under `Printheads/X` for print head X of your choice
