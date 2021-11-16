# *UNDER DEVELOPMENT !!!*

# AM8 plus "Switchwire"
This is a Core XZ upgrade for the popular AM8 frame inspired by the Voron Switchwire.

![Rendering of AM8 plus](https://github.com/maximilian-foerg/AM8-plus-Switchwire/blob/7e2688451dff600d9a9c57fc6b51b4a1cb78b321/Renderings/AM8_plus_Switchwire_2021-Sep-05_03-54-34PM-000_CustomizedView7736393708.png)

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

## FAQ
### Could you provide a ready-to-go Marlin or Klipper config for this printer?
Sadly not. This is because I do not have the original Anet A8 board anymore. On my prototype, I'm using Klipper together with an MKS Gen L V1.0 Board, TMC 2208 stepper drivers, and a custom print head with a LJ18A3-8-Z/AX bed leveling probe, E3D V6 hotend and a BMG extruder set up as Bowden extrusion system. If you think my config can still be helpful to you, I'll be happy to send it to you. In the future I'd like to provide ready to use configurations for Marlin and Klipper, but I can't promise that.
### Why are there three versions of the XZ Joint Rod Clamp (40, 45 and 46mm)?
There are two versions of the Anet A8, one with 45mm spacing between the linear rods of the X-axis, and one with 46mm spacing. This also means that the ball bearings on the print head are either 45mm or 46mm apart. You need to find out which version of the Anet A8 you have, and print the appropriate version of the rod clamp. The 40mm rod clamps are needed for the VORON Afterburner printhead.
### Why is this still under development? Can I already transform my printer?
* The Core XZ mechanics are mature and thoroughly tested by me and will probably not undergo any more changes. I'm using my AM8 plus on a daily basis without any issues.
* The main reason why it still is under development, is the printhead. The original Anet A8 printhead just isn't great. It's too heavy. Still, the Core XZ mechanics will work fine. The only problem is, unlike threaded spindles, a Core XZ mechanism does not lock itself when the printer is turned off. This means that the print head falls onto the print bed. Well, "falling" is perhaps an exaggeration; with properly tensioned belts, it's sliding down slowly. No speeds are reached that would damage the nozzle or the print bed. Nevertheless, it's not pretty. That's why I'm designing a lighter printhead and want to release it with the mod. But for that you will have to buy more parts, because I want to use a BMG extruder and an E3D v6 hotend. I'm currently using my printer with a prototype of this printhead, and it allows for higher print speeds and better print quality, despite being a bowden setup. It's also more silent.

## BOM
The following lists specify which additional parts you'll need to upgrade your existing printer to an AM8 plus. Note that there are alternative standards for each DIN standard (for example, the corresponding ISO standard). These are just the standards I used to design the parts. If you decide to use other nuts and bolts, check the dimensions beforehand. This is especially important for nuts and countersunk screws, less so for button head screws and cylindrical head screws.

### If you already have an AM8...
... and want to keep your Y axis:
* 1 more GT2 16T timing pulley (2 are already included with Anet A8)
* ~5 meters of GT2 timing belt with 6mm width (glassfiber belt recommended, and it's highly recommended to replace the Y axis belt too)
* 4 DIN 934 M2 nuts (only 2 if you're not using the Z endstop)
* 2 DIN 912 M2x10 screws
* 2 DIN 912 M2x12 screws (only if you ARE using the Z endstop)
* 2 DIN 934 M3 nuts
* 4 DIN 7991/ISO 10642 M3x25 screws
* 18 DIN 7991/ISO 10642 M3x30 screws
* 21 ISO 7380 M5x10 screws (only 20 if you're not using the Z endstop) and the same number of M5 slot nuts for your type of aluminium extrusions (you may already have some of these from your disassembled AM8 Z axis!)
* 16 DIN 988 6x3x0.5 precision shim rings (YES, measurements are important, and NO, you can't just use cheap M3 washers)
* 16 F623 ball bearings
* 12 Threaded Heat Inserts M3x5x4 (the ones VORON printers use)

For the original Anet A8 printhead:
* 2 more DIN 934 M3 nuts
* 2 DIN 912 M3x12 screws

## More renderings!
![Rendering of AM8 plus](https://github.com/maximilian-foerg/AM8-plus-Switchwire/blob/7e2688451dff600d9a9c57fc6b51b4a1cb78b321/Renderings/AM8_plus_Switchwire_2021-Sep-05_03-56-04PM-000_CustomizedView29330691624.png)
![Rendering of AM8 plus](https://github.com/maximilian-foerg/AM8-plus-Switchwire/blob/7e2688451dff600d9a9c57fc6b51b4a1cb78b321/Renderings/AM8_plus_Switchwire_2021-Sep-05_03-57-19PM-000_CustomizedView22261559062.png)
![Rendering of AM8 plus](https://github.com/maximilian-foerg/AM8-plus-Switchwire/blob/7e2688451dff600d9a9c57fc6b51b4a1cb78b321/Renderings/AM8_plus_Switchwire_2021-Sep-05_03-58-23PM-000_CustomizedView30775230664.png)
