---
layout: default
title: "Design Considerations"
nav_order: 3
permalink: /considerations/
---

# Design Considerations

**THIS PAGE IS WIP**
{: .fs-5 .ls-10 .code-example .text-center }

## What keyboard do I want?
One of the first major decisions you'll have to make is **"What kind of keyboard do I want to make?"**.

It may sound obvious but the truth is, **the answer to that question will influence your design decisions the most**. 

---

## Integrated MCU boards
If you're looking for a larger keyboard with lots of keys, like a 60% or larger, you'd definitely be looking towards **integrating the MCU onto the PCB**.

This guide is mainly meant for this kind of keyboard.

<div class="code-example" markdown="1">
See the below PCB. It's using an integrated MCU (STM32F103) ([source](https://www.reddit.com/r/MechanicalKeyboards/comments/975qxn/stm60_60_mechanical_keyboard_pcb/)):

![image](https://user-images.githubusercontent.com/23428162/170258935-ac86e019-36b9-4e62-8b58-6eeee6d1760a.png)

![image](https://user-images.githubusercontent.com/23428162/170259033-d37998cf-4bd2-4b6f-bfef-22d802e1c8de.png)
</div>

---

## Side mention: Pro Micro-based/handwired keyboards
On the other hand, if you're more interested in making a **small keypad** or something one-off, consider using a pro micro (or [alternatives](https://makezine.com/2021/10/27/a-chip-is-born-rp2040-based-boards/) <- see RP2040-based ones). This will allow you to design a PCB without needing PCB assembly, and then you can hand solder on THT (through hole) components. Alternatively you can also try [handwiring](https://www.crackedthecode.co/a-complete-guide-to-building-a-hand-wired-keyboard/).

<div class="code-example" markdown="1">
See the below image of a macropad using an Arduino Pro Micro ([source](https://www.reddit.com/r/arduino/comments/oe689y/pro_micro_powered_4x4_macro_keyboard_with_an_oled/)):

![image](https://user-images.githubusercontent.com/23428162/170257560-598e9690-93f4-499d-a4d3-b27c925c348d.png)
</div>

You only need to buy one controller board, which is what makes up the majority of the cost, leading to an overall cheaper product given you're only producing a really **low quanitity of boards** (1-2). They do also have their **downsides**. For example, they usually do not have as many GPIO pins available (for small keyboards this is a non-issue), and take up more room. 

**I won't cater this guide to this kind of board**, but that's not to say that the information in this guide is entirely irrelevant to it. Certain sections like the ones about MCU choice and layout choice still apply. (I will likely write a separate guide/section on how to design a board like this later. They are a lot simpler than integrated MCU boards.)

Essentially: You need to learn is how a switch matrix works, then connect your columns and rows to GPIO pins on the controller, and write your firmware.

For now, I'll continue the guide with integrated MCU in mind..

---

## Layout and KLE
Especially for a beginner, try and make your life easier from the start. **Layouts with more empty space will obviously be easier to route**.

With that in mind, I recommend something like a TKL to start off. You could also make a small macropad with empty space reserved just for the MCU and whatnot, however, its my belief that learning and experimenting to put a MCU on an proper keyboard layout will give you much more useful experience in terms of learning to route things efficiently and cleanly. I'll give some of my pointers for routing on realistic keyboard layouts later on (in the meat of the guide).

It's a good idea to make a [KLE](http://www.keyboard-layout-editor.com/) to draft your layout. Be sure to **save this** somewhere, whether by logging into github and saving to your account or simply saving it as a gist. The KLE is useful in planning the switch matrix, and is very very important to **firmware** creation later on (assuming you're using QMK/VIA/VIAL).

While you can rotate keys in KLE for special layouts like alices and whatnot, I won't cover how to design boards around layouts with rotated keys. But if you're interested, you can ask in on Atelier (though I might make another section for this at a later date).
{: .code-example }

<div class="code-example" markdown="1">
Simple example of a KLE, a F13 TKL:

![image](https://user-images.githubusercontent.com/23428162/170257748-03028946-da25-4fd1-a71e-9933711900af.png)
</div>

---

## PCB Manufacturer + budget
If you intend on ever getting your PCB physically manufactured, the first thing that you should consider is **how you intend on getting them manufactured**. Knowing what manufacturer you're working with will lay some more specific guidelines that you'll need to follow, and it will heavily influence some of the choices you'll make during the entire design process. Every PCB manufacturer has specific **'capabilities'** (tolerances that you'll need to follow such that a working product is ensured). 

For example, **JLCPCB**, a PCB manufacturer popular for it's affordable low quantity PCB manufacturing service, has its capabilities documented [here](https://jlcpcb.com/capabilities/Capabilities). If you're new to PCBs, a lot of the stuff on this page will seem quite daunting initially. Don't worry. Some are obvious, but with time you'll slowly learn the meanings of the rest.

NOTE: PCB manufacturer capabilities constantly change/update (JLC in particular). So anything about capabilities, prices, and recomendations I mention in this guide may change (I'll try to keep it as up to date as I can).
{: .code-example }

As I mentioned, I highly **recommend JLCPCB, for prototyping** at the very least. They are affordable even at low qualities of boards (minimum order 5), and also offer an affordable PCB assembly service (though as you'll see, it has a few limitations). Therefore, the rest of the decisions I'll be making from now on will be influenced with JLC's PCB manufacturing and assembly capabilities in mind. 

In terms of actual **costs**, I mentioned this towards the very beginning of the guide but, getting PCBs mannufactured won't be free. Expect to pay upwards of 100 USD (5 PCBs assembled and shipped, from JLCPCB) for the example PCB I'll be designing in this guide. If you cannot cop that cost, consider reading the section above about pro micro based pcbs. Don't worry though, as I'll be going over what influences price throughout this section. At the end, I will pick what I deem to be the best value at the time of writing (while still balancing design simplicity for the sake of the guide).

I will elaborate on how to order your PCB from JLC later in the guide.

For now, I'll continue...

---

## MCU Choice
`WIP: mention MU vs AU (QFN vs QFP)`

  * **AVR** (ATMEGA/ATMEL..)
    * **PROS**: Simple to work with for a beginner (only have to deal with 5V), simple routing, can technically hand solder the AU, has established QMK support (unlike the RP2040)
    * **CONS**: expensive for what you get (8-25 USD), outdated, low/patchy availability in general, small flash (this is more of a pain than you might think)
  * **STM32**
    * **PROS**: relatively cheap for what you get (6-12 USD), ARM, lots of (internal) flash usually, has established QMK support (unlike the RP2040), comes in a different range of sizes and packages (both QFN and QFP), decent availability on JLC
    * **CONS**: Can be highly confusing to choose a chip ([see here for more info](http://acheronproject.com/joker_mcus/joker/)), availablity is patchy, more complex than a 32u4 (you have to deal with a voltage regulator/stepdown, as the chip runs on 3v3 and 1v1), more complex routing
  * **RP2040**
    * **PROS**: really cheap (1-2 USD), ARM, new, lots of flash storage, easy to flash, readily available on JLC
    * **CONS**: official QMK support only exists in [develop branch](https://github.com/qmk/qmk_firmware/tree/develop) (support in `master` will be merged Q3 2022), only QFN (cant hand solder), requires external flash (though you have up to 16MB), more complex than a 32u4 (you have to deal with a voltage regulator/stepdown, as the chip runs on 3v3 and 1v1), more complex routing

NOTE: 'Pro micro'-like controllers have varying chips too (the real pro-micro has a 32u4).
{: .code-example }

### Combo footprints
You can combine two footprints of similar PCBs to support more than one type of MCU without much effort.

**Note**: There are some implications behind this. You may need to modify the solder paste layer on your PCB depending on the manufacturer that you pick.
{: .code-example }

  * 32u4: MU + AU <br>
![image](https://user-images.githubusercontent.com/23428162/170264531-b4f11e1c-19c6-413a-9de0-df96c0ed1f5c.png)
  * STM32: Joker MCU
    * http://acheronproject.com/joker_mcus/joker/

---

## Switch matrix
* [Hadi video part 3](https://www.youtube.com/watch?v=vLGklanzQIc)
* Diodes
* Size
  * One pin per column/row
* Duplex matrices
  * Reduce pin usage by making matrix more square
* Direct pin?

## Multilayout?
* How it works
* See [hadi's video (timestamped)](https://youtu.be/vLGklanzQIc?t=963) about special cases like split BS

## SMD vs THT
* Cost vs complexity
* Designing complexity
* Cost + availability of components
* Hot-swap vs Solder + other switch footprints considerations
* Multi-layout compatibility

---

## More on PCB Assembly
* Limitations (JLCPCBA)
  * Only assemble one side
  * Certain colours only
  * No ENIG (for non-green boards)
  * Size minimum & max
  * THT?
* LCSC/JLC Parts
  * [JLC part library](https://jlcpcb.com/parts)
  * Extended vs Basic parts
  * Minimum order quantities
  * Ordering parts to inventory
* NEW: Ordering parts from other vendors for assembly (e.g. Mouser)

---

## What's a Daughterboard?
* Daughterboard vs Integrated USB port
  * [Unified DB](https://github.com/ai03-2725/Unified-Daughterboard)
* Can I have both?
  * Yes.

---

## RGB...
* RGB
  * Adds a lot of complexity, unecessary for beginner
  * Common anode vs ARGB

---

## What I’ll be going with for this guide example [WIP]

**WIP**: Need to outline my decicisons for other things mentioned in this page
{: .code-example }

**Note to begin**: As much as I love the RP2040, I would recommend **FIRST** designing a board with the **32u4**. The experience you will gain (by the time you have a design that should be manufacturable) is **invaluable**. 

If you're short on money and don't want to manufacture two boards, get your final product confirmed by someone who knows more than you. This will at least make sure you're not doing anything wrong/missing knowledge, should you decide to move on to using different MCUs (like the RP2040).

* I'll be using the ATMega32u4 for this guide.
* HOWEVER, consider RP2040. See pros and cons above.

---

The next part of the guide outlines some more useful resources you can use: <br>
[Extra Resources](/extra-resources/){: .btn .btn-purple }

