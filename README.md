# *UNDER DEVELOPMENT*

# AM8 plus "Switchwire"
This is a Core XZ upgrade for the popular AM8 frame inspired by the Voron Switchwire.

![Rendering of AM8 plus](https://github.com/maximilian-foerg/AM8-plus-Switchwire/blob/e5b23ad9de3f0b2a86c8a19ee00f621ad309499c/Renderings/AM8_plus_Switchwire_2021-Jun-19_02-42-49PM-000_CustomizedView16176384139.png)

In case you don't know about the Voron Project, check it out at https://www.vorondesign.com/. They design outstanding open-source 3D printers, and if you're looking for a *real* upgrade, I'd suggest you build a Voron instead. It probably won't get any better.

But if you enjoy tinkering on your cheap 3D printer just like me, this mod could be something for you. It doesn't matter if you're still using an original Anet A8 or already upgraded to an AM8. For each case, you will find the necessary parts in the provided BOM. 

__DISCLAIMER__
I would like to emphasize that this is purely a hobby project, and I cannot guarantee that this rebuild will improve print quality at all!

## Some Facts
* Build volume is 220x220x220mm.
* The dimensions of the aluminum extrusions are the same as for the AM8.
* This upgrade uses as many of the original Anet A8 and AM8 parts a possible. Still, you will have to buy some stuff. Have a look at the [BOM](#bom).
* Although I redesigned every part, the Y axis did not change compared to the AM8. So if you already have an AM8, you can continue to use your Y axis.
* You can use the original Anet A8 board for this build, but you will have to flash another firmware. One possibility is to use [Marlin](https://marlinfw.org/), which can be configured for Core XZ motion systems. My recommendation is [Klipper](https://www.klipper3d.org/) together with a Raspberry Pi running [OctoPrint](https://octoprint.org/) or [Mainsail](https://docs.mainsail.xyz/). Klipper runs all calculations on the much more computationally powerful Raspberry Pi, so you can use it to compensate for the weak hardware of the original Anet A8 or other cheap 3D printer motherboards.
* I didn't give much love to the Z axis endstop mount, because I think one really should use an inductive probe for bed leveling. They are very cheap, and there are several mounts for different kinds of probes available on thingiverse.

## Why Core XZ?
3D printers make fast movements, so it is a great advantage if moving parts have the lowest possible mass. This is why the Core XY architecture was developed, where two stepper motors can move the print head in two directions through a sophisticated belt drive without having to move themselves. Well-known DIY Core XY printers are, for example, the [Voron 0](https://www.vorondesign.com/voron0.1), [Voron 1](https://www.vorondesign.com/voron1.8) and [Voron 2](https://www.vorondesign.com/voron2.4), or the very popular [Hypercube](https://www.thingiverse.com/thing:1752766) and [Hypercube Evolution](https://www.thingiverse.com/thing:2254103).
However, a Core XY motion system requires a cube-shaped frame, which we do not have with the AM8. Converting the frame would contradict the sense of an "upgrade" and would rather be a completely new printer. Therefore, the [Voron Switchwire](https://www.vorondesign.com/voron_switchwire) gave me the idea to implement the Core XY architecture rotated by 90 degrees as Core XZ architecture on the AM8. This has the following advantages:
* The weight of the X axis is now balanced, because there is no longer a motor hanging on one side.
* The Z axis becomes lighter since all stepper motors are fixed to the frame.
* You get rid of the threaded spindles.
* You can make movements in the Z direction just as fast as in the X and Y directions.
* You need one less stepper motor.

## Printing Tips
* The number at the end of the file name of each STL indicates how often the part must be printed.
* The parts HAVE to be printed in ABS, PETG, ASA or any other material that can withstand mechanical stress. PLA is NOT an option. Avoid PETG if you have an enclosure for your printer or want to build one, because it bends at high ambient temperatures.
* I recommend printing the parts with a 0.4mm nozzle and the following settings:
  * 0.2mm layer height
  * 4 walls, 5 bottom layers, 5 top layers
  * 40% grid or gyroid infill
* Before printing, calibrate your extruder steps and the tenperature and flow rate for your specific filament. Get rid of any strining, warping and elephant food on your prints. There are tons of tutorials on the web on how to do each of that.

## BOM
The following lists specify which additional parts you'll need to upgrade your existing printer to an AM8 plus.

### If you already have an AM8...
... and want to keep your Y axis:
* 1 more GT2 16T timing pulley (2 are already included with Anet A8)
* ~5 meters of GT2 timing belt with 6mm width (glassfiber belt recommended, and it's highly recommended to replace the Y axis belt too)
* 4 DIN 934 M2 nuts (only 2 if you're not using the Z endstop)
* 4 DIN 912 M2x12 screws (only 2 if you're not using the Z endstop)
* 28 DIN 934 M3 nuts
* 6 DIN 912 M3x12 screws
* 4 DIN 912 M3x14 screws
* 4 DIN 7991 M3x18 screws
* 22 DIN 7991 M3x30 screws
* 12 ISO 7380 M5x10 screws
* 16 DIN 988 6x3x0.5 precision shim rings (YES, measurements are important, and NO, you can't just use cheap M3 washers)
* 16 F623 ball bearings
