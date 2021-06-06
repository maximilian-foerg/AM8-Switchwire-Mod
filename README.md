# *UNDER DEVELOPMENT*

# AM8 plus "Switchwire"
This is a Core XZ upgrade for the popular AM8 frame inspired by the Voron Switchwire.

![Rendering of AM8 plus](https://github.com/maximilian-foerg/AM8-plus-Switchwire/blob/de6ad050a957cc1e82d35bacd7145864ecaa8a1a/Renderings/AM8_plus_Switchwire_2021-Jun-06_10-02-51AM-000_CustomizedView17519671649.png)

In case you don't know about the Voron Project, check it out at https://www.vorondesign.com/. They design outstanding open-source 3D printers, and if you're looking for a *real* upgrade, I'd suggest you build a Voron instead. It probably won't get any better.

But if you enjoy tinkering on your cheap 3D printer just like me, this mod could be something for you. It doesn't matter if you're still using an original Anet A8, already upgraded to an AM8 or want to build this from scratch. For each case, you will find the necessary parts in the provided BOM. 

__DISCLAIMER__
I would like to emphasize that this is purely a hobby project, and I cannot guarantee that this rebuild will improve print quality at all!

## Some Facts
* Build volume is 220x220x220mm.
* The dimensions of the aluminum extrsusions are the same as for the AM8.
* This upgrade uses as many of the original Anet A8 and AM8 parts a possible. Still, you will have to buy some stuff, have a look at the BOM.
* Although I redesigned every part, the Y axis did not change compared to the AM8. So if you already have an AM8, you can continue to use your Y axis.
* You can use the original Anet A8 board for this build, but you will have to flash another firmware. One possibility is to use Marlin (https://marlinfw.org/), which can be configured for core xz motion systems. My recommendation is Klipper (https://www.klipper3d.org/) together with a Raspberry Pi running OctoPrint (https://octoprint.org/) or Mainsail (https://docs.mainsail.xyz/). Klipper runs all calculations on the much more computationally powerful Raspberry Pi, so you can use it to compensate for the weak hardware of the original Anet A8 motherboard.

## Why Core XZ?
3D printers make fast movements, so it is a great advantage if moving parts have the lowest possible mass. This is why the Core XY architecture was developed, where two stepper motors can move the print head in two directions through a sophisticated belt drive without having to move themselves. Well-known DIY Core XY printers are, for example, the Voron 0, Voron 1 and Voron 2, or the very popular printers Hypercube (https://www.thingiverse.com/thing:1752766) and Hypercube Evolution (https://www.thingiverse.com/thing:2254103).
However, a Core XY motion system requires a cube-shaped frame, which we do not have with the AM8. Converting the frame would contradict the sense of an "upgrade" and would rather be a completely new printer. Therefore, the Voron Switchwire gave me the idea to implement the Core XY architecture rotated by 90 degrees as Core XZ architecture on the AM8. This has the following advantages:
* The weight of the X axis is now balanced, because there is no longer a motor hanging on one side.
* The Z axis has become lighter since all stepper motors are fixed to the frame.
* You get rid of the threaded spindles! This is great because:
  * They are usually crooked, which is why cheap China printers usually leave them free play at the top, where they can wiggle merrily. It should be clear that this does not contribute to precision.
  * The cheap spindles are not very precisely manufactured, have play and are susceptible to backlash.
  * Even anti-backlash nuts do not necessarily help against this, because the threaded spindles are often connected to the stepper motor via flexible couplings. These spring back during movements, which makes precise movements in the Z-axis impossible.
  * You can now make movements in the Z direction just as fast as in the X and Y directions.
  * You need one less stepper motor.
