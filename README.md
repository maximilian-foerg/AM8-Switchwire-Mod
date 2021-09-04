# *UNDER DEVELOPMENT*

# AM8 plus "Switchwire"
This is a Core XZ upgrade for the popular AM8 frame inspired by the Voron Switchwire.

![Rendering of AM8 plus](https://github.com/maximilian-foerg/AM8-plus-Switchwire/blob/ff0caa099e454a39bc08930d6c69bd091ac44261/Renderings/AM8_plus_Switchwire_2021-Sep-04_07-04-03PM-000_CustomizedView15834890300.png)

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
3D printers make fast movements, so it is a great advantage if moving parts have the lowest possible mass. This is why the Core XY architecture was developed, where two stepper motors can move the print head in two directions through a sophisticated belt drive without having to move themselves. Well-known DIY Core XY printers are, for example, the [Voron 0](https://www.vorondesign.com/voron0.1), [Voron Trident](https://www.vorondesign.com/voron_trident) and [Voron 2](https://www.vorondesign.com/voron2.4), or the very popular [Hypercube](https://www.thingiverse.com/thing:1752766) and [Hypercube Evolution](https://www.thingiverse.com/thing:2254103).
However, a Core XY motion system requires a cube-shaped frame, which we do not have with the AM8. Converting the frame would contradict the sense of an "upgrade" and would rather be a completely new printer. Therefore, the [Voron Switchwire](https://www.vorondesign.com/voron_switchwire) gave me the idea to implement the Core XY architecture rotated by 90 degrees as Core XZ architecture on the AM8. This has the following advantages:
* The weight of the X axis is now balanced, because there is no longer a motor hanging on one side.
* The Z axis becomes lighter since all stepper motors are fixed to the frame.
* You get rid of the threaded spindles.
* You can make movements in the Z direction just as fast as in the X and Y directions.
* You need one less stepper motor.

## Printing Tips
* The number at the end of each file name indicates how often the part must be printed.
* All parts are already oriented for the best printing position. Do not change the orientation.
* The parts HAVE to be printed in ABS, PETG or another material that can withstand mechanical stress. PLA is NOT an option. Avoid PETG if you have an enclosure for your printer or want to build one, because it bends at high ambient temperatures. ABS is the best way to go here.
* I recommend printing the parts with a 0.4mm nozzle and the following settings:
  * 0.2mm layer height
  * 4 walls, 5 bottom layers, 5 top layers
  * 40% cubic or gyroid infill
* Before printing, calibrate your extruder steps and the temperature and flow rate for your specific filament. Get rid of any strining, warping and elephant food on your prints. There are tons of tutorials on the web on how to do each of that.

## About XZ belts & belt tensioning
There's no belt tensioning system. But for printers with a core architecture it's significantly important that the belts have equal tension, otherwise the printhead won't be able to move in a straight line. This is how I did it:
* I attached the upper pulley mounts each about 3mm to 4mm below the top edge of the aluminum frame.
* Then I attached one end of the uncut belt to the print head on one side of the belt clamp (it doesn't matter which side).
* I routed the belt as it will be mounted later until the other end arrived on the other side of the print head.
* There, without applying any tension to the belt, I estimated what length would be suitable so that I could secure the other end of the belt in the belt clamp as well. At this point I cut off the belt. It doesn't hurt to make the belt a few inches longer than necessary. In the middle of the belt clamp you can let excess belt protrude.
* Now I took the cut piece of belt out of the printer again and cut a second belt with exactly the same length from the remaining belt. The fact that the two belts have the same length helps a lot to achieve equal belt tension.
* I then installed both belts in the printer. To do this, I first attached both belts with the exact same number of teeth to one side of the print head and then routed them through the motion system. Then I attached both belts to the other side of the printhead. Again, I applied only a little tension to the belts. This is important! It is also crucial to make sure that the belts have the same number of teeth protruding after they have been fastened with the clamp.
* To tighten the belts, I finished by loosening the screws on the upper pulley mounts until they could be moved a little. While pushing them up with one hand, I reattached them to the frame with the other. In the end, my straps were evenly tensioned.

## FAQ
### Could you provide a ready-to-go Marlin or Klipper config for this printer?
Sadly not. This is because I do not have the original Anet A8 board anymore. On my prototype, I'm using Klipper together with an MKS Gen L V1.0 Board, TMC 2208 stepper drivers, and a custom print head with a LJ18A3-8-Z/AX bed leveling probe, E3D V6 hotend and a BMG extruder set up as Bowden extrusion system. If you think my config can still be helpful to you, I'll be happy to send it to you. In the future I'd like to provide ready to use configurations for Marlin and Klipper, but I can't promise that.
### Why are there two versions of the XZ Joint Rod Clamp (45mm and 46mm)?
There are two versions of the Anet A8, one with 45mm spacing between the linear rods of the X-axis, and one with 46mm spacing. This also means that the ball bearings on the print head are either 45mm or 46mm apart. You need to find out which version of the Anet A8 you have, and print the appropriate version of the rod clamp.

## BOM
The following lists specify which additional parts you'll need to upgrade your existing printer to an AM8 plus. Note that there are alternative standards for each DIN standard (for example, the corresponding ISO standard). These are just the standards I used to design the parts. If you decide to use other nuts and bolts, check the dimensions beforehand. This is especially important for nuts and countersunk screws, less so for button head screws and cylindrical head screws.

### If you already have an AM8...
... and want to keep your Y axis:
* 1 more GT2 16T timing pulley (2 are already included with Anet A8)
* ~5 meters of GT2 timing belt with 6mm width (glassfiber belt recommended, and it's highly recommended to replace the Y axis belt too)
* 4 DIN 934 M2 nuts (only 2 if you're not using the Z endstop)
* 4 DIN 912 M2x12 screws (only 2 if you're not using the Z endstop)
* 20 DIN 934 M3 nuts
* 6 DIN 912 M3x12 screws
* 16 DIN 7991/ISO 10642 M3x30 screws
* 8 DIN 7991/ISO 10642 M3x35 screws
* 13 ISO 7380 M5x10 screws (only 12 if you're not using the Z endstop)
* 16 DIN 988 6x3x0.5 precision shim rings (YES, measurements are important, and NO, you can't just use cheap M3 washers)
* 16 F623 ball bearings
