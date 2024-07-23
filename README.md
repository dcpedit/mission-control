<p align="center">
  <img width="350" alt="Mod Mmm Logo" src="https://i.imgur.com/8TSD5ec.png"/>
</p>

# Mission Control PCB for the IBM Model M122

This project is designed to replace all internal compoents of an Model M122 keyboard, and is based off my previous [Mod Mmm Project](https://github.com/dcpedit/mod-mmm).  Only the curved steel backplate is needed for the PCB to be mounted on.

![m122 9009](https://i.imgur.com/1ZAMhn9.jpeg)
![m122 switches](https://i.imgur.com/W7ycrXl.jpeg)

Image gallery: https://imgur.com/a/wuXMWVg

## Features

* Hotswap sockets for MX switches
* Multiple layout support, including ISO, split spacebar, and 4x5 macropad for numpad. [KLE link](http://www.keyboard-layout-editor.com/#/gists/d71adbbb0de71b98bfe3e79a4a607b5c)
* PCB mount stabilizers
* Under-switch LED for caps lock and num lock
* Piezo buzzer
* Solenoid
* LCD display
* USB-C support
* Bluetooth support (via PillBug)
* QMK/VIA firmware
* ZMK firmware (for BT PillBug)

<img width="350" alt="Layout" src="https://i.imgur.com/4Qnehgr.png">

## The Build "Stack"

The following is a table of measurements of everything that's stacked on top of the steel backplate.  The key spacing was taken from hires scans I made of the Model M's wiring membrane.  I recalculated the spacing for each decrease in radius except for the foam where I reused the numbers from the switch plate.  I was lazy and figured foam can stretch anyways.

| Part            | Thickness (mm) | Radius (mm) | Radius Start | 1u vertical spacing (mm) |
|-----------------|----------------|-------------|--------------|--------------------------|
| Steel backplate | 1.0            | 276.635     | inner        | 20.617
| Hex Standoffs   | 4.0            | n/a         | n/a          | n/a
| PCB     | 1.0            | 272.135     | center       | 20.560
| Plate Foam      | 3.5            | n/a         | n/a          | n/a
| Switch Plate    | 1.5            | 267.385     | center       | 20.201

## Parts List

| Part                        | Count | Notes |
|-----------------------------|-------|-------|
| Mission Control PCB         | 1     | 1mm FR4 thickness
| Blackpill (STM32F411)       | 1     |
| M2.5x3mm Wafer Screw        | 138   | [Link](https://www.aliexpress.us/item/2255800885711092.html?spm=a2g0o.order_list.order_list_main.22.1875180223MOsy&gatewayAdapt=glo2usa&_randl_shipto=US)
| M2.5x4mm Hex Standoff       | 69    | [Link](https://www.aliexpress.us/item/2251832790997097.html?spm=a2g0o.order_list.order_list_main.23.1875180223MOsy&gatewayAdapt=glo2usa&_randl_shipto=US)
| BAV70 Diodoe                | 64    | [Link](https://www.mouser.com/ProductDetail/Nexperia/BAV70215?qs=me8TqzrmIYX%252B%2FJ6jIjzNeA%3D%3D&countrycode=US&currencycode=USD)
| Piezo Buzzer                | 1     | [Link](https://www.digikey.com/en/products/detail/tdk-corporation/PS1240P02BT/935924)
| 5v Solenoid                 | 1     | [Link](https://www.digikey.com/en/products/detail/sparkfun-electronics/ROB-11015/6163694)
| Hotswap Sockets       | 108 - 115 | Recommend Gateron v2
| 2mm LED                     | 2     | For switch status led. [Link](https://www.amazon.com/gp/product/B01C5HL0PO/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&th=1)
| 10kΩ Resistor               | 2     | For keycap LED. Smaller = brighter |
| 22kΩ Resistor               | 1     | Pullup for pin A10 |
| TIP120 Transistor           | 1     | For solenoid. [Link](https://www.amazon.com/gp/product/B08212F42Z/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1)
| 1N4001 Diode                | 1     | For solenoid. Comes with above kit |
| 2.2kΩ Resistor              | 1     | For solenoid. Comes with above kit |
| Mill-Max 315 sockets (1x20) | 2     |
| Mill-Max 315 sockets (1x4)  | 1     |
| Mill-Max round pin (¼in)    | 44    | [Link](https://www.mouser.com/ProductDetail/Mill-Max/3320-0-00-15-00-00-03-0?qs=s8Nb1z4Wn%2FQ16WBIwCPrTw%3D%3D&countryCode=US&currencyCode=USD)
| 2u plate mount stabilizer   | 7 - 10| Count varies based on layout
| 7u plate mount stabilizer   | 1     | For 7u spacebar
| Switch plate (5 piece set)  | 1     | Optional 1.5mm acrylic
| Case foam (under PCB)       | 1     | Optional 2mm EVA
| Plate Foam                  | 1     | Optional 3.5mm EVA foam (or 2mm + [1.5mm](https://www.aliexpress.us/item/3256804208838525.html?spm=a2g0o.order_list.order_list_main.5.21ef1802FA7EIC&gatewayAdapt=glo2usa&_randl_shipto=US))
| 2.2" ILI9341 display        | 1     | Optional display, [link](https://a.co/d/10fYStD)
| 8 pin headers (2.54mm pitch)| 2     | For optional display
| 8 pin ribbon cable          | 1     | For optional display
| USB-C panel mount           | 1     | [Link](https://a.aliexpress.com/_mLVMrx6)

For the Mill-Max 315 series sockets, I found it more cost efficient to just buy a really long socket and cut the sizes I need with flush cutters.  [Here's an example of a 1x64 socket.](https://www.mouser.com/ProductDetail/Mill-Max/315-93-164-41-003000?qs=WZRMhwwaLl%252BIMh92Iwf2Uw%3D%3D&countryCode=US&).  Make sure to file down the rough edge after cutting.

## PCB Build Guild

<img src="https://i.imgur.com/i8CSYAg.jpeg" width="350">

To complete this build, you will need to get the main PCB manufactured with an **FR4 thickness of 1mm**.  I personally like using [JLCPCB](https://jlcpcb.com/), and I've included the gerber zip in the `pcb/production` folder.  (Note: you will need to order a minimum of 5 boards).

### 1) Disassembly
The first step is to disassemble your Model M and clean it if neccessary.  There are lots of tutorials online on how to do this, and make sure you have a 7/32 inch (5.5mm) socket for the case screws.

Remove the plastic rivets on the back of the steel plate with a pair of flush cutters.  Once this is done, all the components can be removed leaving just the steel plate.

### 2) Shape PCB

Using the hex standoffs and a few screws, mount the PCB onto the steel backplate for 24hrs.  You only need enough screws & standoffs for the PCB to hold its shape.  After you remove the PCB, you want there to be a slight curve to the FR4 before soldering on the components.  This way, the componenets and solder joints experience less stress when the PCB is bent into its final shape.

### 3) BAV70 Diodes

Flip the PCB over to the backside and solder on the BAV70 diodes (D1 - D64). Place a dab of solder on the single bottom pad of the diode on the PCB. Then using tweesers, position the diode so that the legs line up with the pads. Then using the point of one tweeser leg, gently hold the top of the diode in place while melting the dab of solder that was placed on the bottom pad previously. With the diode now held in position, solder the top two legs to their respective pads.

### 4) Hotswap Sockets

Place some solder on one of the hot swap socket pads. There should be enough solder to make a small mound. Place the socket into position and melt the mound of solder that was previously added while pressing down on the center of the socket. Be sure to avoid touching any metalic parts to prevent burns. Keep the soldering iron on the pad long enough for the solder to flow around the socket connector (usually around 3 to 4 seconds). Now solder the other socket connector to the pad.

### 5) 22k Pullup Resistor

In order to use pin A10 on the Blackpill, a 22k pullup resistor is needed (according to the [QMK docs](https://docs.qmk.fm/#/platformdev_blackpill_f4x1)). Solder this into the R3 position.  Orientation does not matter.

### 6) Blackpill Development Board

It's probably best to flash the firmware onto the Blackpill first using the `bin` file in the `firmware` directory. Hook it up to [QMK Toolbox](https://github.com/qmk/qmk_toolbox/releases) and push the following buttons to place it in bootloader mode before flashing:
* Press and hold the BOOT0 button
* Press and release NRST (reset) button
* Release BOOT0 button

Solder the Mill-Max 315 sockets onto the daughterboard.  Then place a piece of masking tape over the pin holes, and insert each pin though the tape and into its hole with tweezers.  Then set the Blackpill into place with the components facing up and the USB port facing the top of the daughterboard.  Solder the pins into place, and then carefully and slowly remove the Blackpill.  If you pull too fast and hard, one edge will suddenly pop loose, bending the pins on the opposite side.  Remove the masking tape, and push the Blackpill back into place.

Lazy-man's short cut: skip the masking tape.  But note that using too much solder will cause it to flow down the pin and into the socket.  If this happens, the keyboard will still work, but you won't be able to remove the Blackpill without desoldering.

## Choose build option

At this point in the build, you will need to choose between ONE of the following 2 options.

### Option #1: Solenoid, buzzer, and status LEDs

<img src="https://i.imgur.com/jOQl0lg.jpeg" width="450"/>

#### a) Solenoid Components
Bend the narrow part of the pins on the TIP120 back towards the heatsink at a 90 degree angle.  Solder it into the TIP1 position.

The 2.2k resistor goes into the R4 spot (orientation does not matter).  The 1N4001 diode goes in to the 1N1 position where the line matches the printed line on the board.  The solenoid wires don't have an orientation, and you can solder them directly into the holes or use a header/connector.

#### b) Piezo Buzzer

Solder this into the BZ1 position.  Orientation does not matter.


#### c) Switch LEDs and resistors (optional)

These LEDs go under the caps lock and scroll lock switches.  Depending on your switch, you may have to solder these in AFTER placing the switch into the socket.  You can tell by looking under the switch to see if there's a hole big enough for the LED to fit through.  If there are only 2 small holes for the LED pins, then the switch needs to go in first.  The short pin of the LED goes in the square pad.  As for the accompanying 10kΩ resistors (R1 and R2), orientation does not matter.

I use a higher resistance here for the white LEDs because they tend to be too bright for me personally.  Feel free to lower the resistance if you want them brighter, or if you choose a different color.

### Option #2: LCD display

<img src="https://i.imgur.com/pWeyHcX.jpeg" width="350">

#### a) Display headers

Mount headers for on the PCB facing down (PCB position J1) and right angled headers on the display facing towards the right

#### b) Cut display window

Turn on your display, and measure the physical height and width of the display area.  This will be the size of your case "window".  Use masking tape to mark the edges of the window on the top of your case and cut the hole out.

I believe the best tool for this job is with a CNC router.  Since I didn't have access to one, I first used a dremel with a cutting disk to cut the hole out.  Then I smoothed the edges with a file, and then with fine grit sand sand paper wrapped around a flat piece of plastic.  I found that adding a chamfered edge makes it look more "finished".

#### c) Mounting display

I found that the easiest thing to do here is to first connect the display to the PCB with the ribbon cable and power it up.  Center the displayed image within the window, and while holding it firmly in place, place hot glue in each corner of the display's PCB, allowing some to flow through the mounting holes.

<img src="https://i.imgur.com/wHgdfui.jpeg" width="350">

## Continue with main build

### 7) Stabilizers

Install your stabilizers of choice onto the PCB.  For the vertical stabs, in order to counteract the curvature of the PCB, I used adhesive stabilizer pads and cut them in half lengthwise (band-aids would work as well).  I then placed them on the inside half of where the stabs would sit.  The idea here is to angle the stabs back outwards so that they remain parallel.

Note that I made all the stab holes a tad larger in the vertical direction to allow for some wiggle room.

<img src="https://user-images.githubusercontent.com/800930/232109738-f275d87e-9415-4e2d-bade-86b1453beb47.jpg" width="350" />

### 8) Install PCB standoffs

<img src="https://i.imgur.com/jx1PXzl.jpeg" width="350"/>

Starting with the steel backplate, insert a screw from the back and screw a standoff on from the other side.  Keep it loose enough so that the standoff can rattle around a bit.  Do this for all the mount holes on the steel plate, even if you end up not using them because they're still good for support.  Omit any standoff that interferes with your stabilizers.

Slip the steel backplate back into the bottom of the case.  You'll need to slide the bottom into the slots first, and then place the plastic case posts into the top-left and top-right corners of the steel backplate.

### 9) Case foam (optional)

If you opted for the 2mm EVA case foam, you'll need to place it over the steel plate before installing the PCB.  The holes in the foam should line up over the standoffs. (Filename: `case/case-foam.ai`)

### 10) Center and Install PCB

Line up the PCB over the holes and place 2 or 3 screws positioned horizontally from each other near the center of the PCB.  Push the center firmly down onto the standoffs to force the PCB to bend (this part is a bit nerve racking, especialy when you hear creaking noises), and secure it with the screws while holding it in place.

Shift the steel backplate all the way to the top until it can't move anymore.  This is the correct position of the plate, so I'd recommend wedging strips of 2mm foam between the case the bottom edge of the case.

<img src="https://i.imgur.com/6zq2th1.jpeg" width="350">

Now place a switch and keycap combo at the corner of every section of the keyboard.  Put the top of the case on, making sure it's aligned and fully seated with no gaps.  Carefully shift the PCB around slightly to get the keycaps to be in the correct position with equal amounts of spacing from the keycap to the case walls.  Basically you're trying to center the PCB by eye-balling the keycap gaps.

With the PCB now centered, remove the top of the case and begin screwing in all the mounting screws.  I'd suggest starting near the center and spiral outwards towards the edges.  This is where you'll probably need to shift the loose standoffs around to line the holes up.  Also, if you run into the problem where the top and bottom screws bump into each other inside the standoff, you'll need to add an insulated washer to the bottom screw.  Place the top case back on every once in a while to make sure the PCB didn't shift and is still centered.  After you're done, remove the steel backplate from the bottom of the case and tighten all the screws on the back.  If you feel that the standoffs are just spinning while you're turning the screw, just squeeze the PCB and backplate together so that it pinches the standoff and keeps it from spinning.

## Assembly photos

<img src="https://i.imgur.com/e6YCYtL.jpeg" width="350"/>
<img src="https://i.imgur.com/NsROSgC.jpeg" width="350"/>
<img src="https://i.imgur.com/vAM7rK7.jpeg" width="350"/>
<img src="https://i.imgur.com/Cfabkr7.jpeg" width="350"/>
<img src="https://i.imgur.com/XdZ64QQ.jpeg" width="350"/>

## Firmware

Binaries are located in the `firmware` directory.

Source code is located in the `missioncontrol` branch of my QMK fork:

https://github.com/dcpedit/qmk_firmware/tree/mission-control/keyboards/dcpedit/missioncontrol

The LCD build requires it's own separate firmware because it uses the solenoid/buzz/LED pins.

### Change graphic

Copy your 240x320 image (320x240 image rotated counter-clockwise 90 degrees) into the following QMK directory:

```
keyboards/dcpedit/missioncontrol/lcd/image/background.png
```

Then run the following command from that directory

```
qmk painter-convert-graphics -f rgb565 -i background.png -o ./
```

That will generate a new `*.c` and `*.h` file.  You can now compile the firmware:

```
make dcpedit/missioncontrol/lcd:via
```