---
layout: default
title: "Extra Resources"
nav_order: 4
permalink: /extra-resources/
---

**Note**: Regarding the resources I linked/mentioned below, most of the information available in those guides will likely all be repeated in this guide. I’m making this guide in an attempt to combine the information available in those guides, as well as build upon them. However, that doesn’t make them useless. I would still recommend going over them to corroborate and build your knowledge further.
{: .code-example }
z
Now, expanding on the whole concept of using this guide in combination with other resources, I can highly recommend the following resources (for now):
## [**Ai03’s keyboard PCB guide**](https://wiki.ai03.com/books/pcb-design/chapter/pcb-designer-guide)
  - Ai03’s guide is short and detailed, however, **slightly outdated** (it recommends using an older version of KiCAD). In my opinion, it does a good job of showing how to set up a development environment and electronically design a PCB using an ATmega32u4 controller.
  - However, it falls short in the fact that it shows this **only for a 2x2 macropad**, with a **usb micro** connector (at least in the main tutorial parts). Realistically, most people seeking to make a keyboard are going to be looking to integrate an MCU into a more standard keyboard size where you don’t have a lot of room to fit components. Also, sometimes things aren’t explained in a way clear to those unfamiliar with EE.

## [**Masterzen’s PCB guide**](https://www.masterzen.fr/2020/05/03/designing-a-keyboard-part-1/) (parts 1-4)
  - Masterzen’s guide, as opposed to Ai03’s, shows how to make a keyboard PCB for a **65% Alps switch keyboard**. Masterzen’s is more in depth than Ai03, including a lot of information including explanations of certain components and what they do, plus what you should be looking for in certain parts. The guide also covers things such as how to export files from KiCAD for manufacturing with JLCPCB and their assembly service (which is realistically what you’re going to be using if you’re on a budget), as well as how to physcially hand solder the board and even write QMK firmware for it.
  - However, the images of the guide aren’t always consistent (fwiw certain steps get skipped from image to image) or sometimes things aren’t explained in a way clear to those unfamiliar with EE. That can definitely confuse beginners. Also, the guide is also on the **older KiCAD 5**, and is a little outdated in terms of the whole part/component choice scheme.
  - I definitely like his tutorial though, so I’ll be taking a lot of inspiration from it while filling in some of the gaps (things that personally confused me) in this guide.

## [**NoahK's YouTube channel**](https://www.youtube.com/channel/UC45VUrCGJStbkWobT0FMTVA)
  - Noah Kiser (NoahK) has a few videos on PCB related thing. He has a series that goes over the making of a TKL RP2040-powered PCB. [Part 1](https://www.youtube.com/watch?v=6Z49bynRqj8) includes setup and schematic work, as well as placing switch/diode footprints using my kle placer plugin. [Part 2](https://www.youtube.com/watch?v=YsHCpA9_U6s) goes over routing most of the MCU and USB.
  - He also has a video on making a pro-micro powered PCB. Good if you want to learn how the basic switch matrix and routing would look like without the pain of MCU routing.
  - Overall great watches, but I would try to pay attention to/learn the PCB **design concepts** rather than just copying exactly what he does, or you won't be able to apply the same concepts to other layouts. Some things with PCB design are pretty copy paste, e.g. most of an MCU schematic, but the routing on all PCBs will always be different.

## **Further**
  - The [**Atelier discord server**](https://discord.gg/b7vwhHS) is a great place for all keyboard creators (including PCB designers, case designers, etc) to ask questions and get help. It serves as a great tool for when (not if) you encounter errors not covered in this guide. There are many helpers there, and you may even catch me there.
  - [**Datasheets and Pinouts**](/basic-knowledge/mcus/#mcu-pinouts-and-datasheets) are also a great source of information, however they can be daunting to beginners who may not understand them. [Watch this video](https://www.youtube.com/watch?v=9r8JMbHc-xQ) if you want to learn more about how to read datasheets.
  - [**Sleepdealr's PCB Design Guidelines/Best practices**](https://gist.github.com/Sleepdealr/ab05f5edb82eae9e0393f4d63da55adf#schematics) gist also has some great, concise information.
  - **Documentation** 
    - [QMK Documentation](https://docs.qmk.fm/#/)
    - [VIA Documentation](https://www.caniusevia.com/docs/specification)
    - [VIAL Porting Guide](https://get.vial.today/docs/)
    - [In-depth Firmware/VIA/QMK Guide by bakingpy](https://docs.keeb.io/via-technical)

---

I will be mostly repeating most of the content in the Ai03 and Masterzen tutorials, so they are technically optional. I highly recommend opening up a datasheet (e.g. for an ATmega32u4) while creating your schematic + pcb (and actually reading the content inside) as they have useful information. 

Lastly, if you have any further questions that you cannot answer by going over above resources/googling, feel free to ask a question in the [Atelier discord server](https://discord.gg/b7vwhHS).

---

Now that you've got some more understanding, you can start actually creating your PCB: <br>
[Project Setup](/setup/){: .btn .btn-purple }
