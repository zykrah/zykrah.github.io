---
layout: default
title: "Extra Resources"
nav_order: 4
permalink: /extra-resources/
---

**Note**: Regarding the resources I linked/mentioned below, most of the information available in those guides will likely all be repeated in this guide. I’m making this guide in an attempt to combine the information available in those guides, as well as build upon them. However, that doesn’t make them useless. I would still recommend going over them to corroborate and build your knowledge further.
{: .code-example }

Now, expanding on the whole concept of using this guide in combination with other resources, I can highly recommend the following resources (for now):
## [**Hadi’s YouTube channel**](https://www.youtube.com/channel/UCpWGAJr2AU7LPUwVYbBQZRg)
  - Hadi’s series (parts 1-3) on keyboard PCB design is a great place to start with learning how to design keyboards in general. 
  - In his [first video](https://www.youtube.com/watch?v=BhFqkVggv8Q), he goes over designing a keyboard **layout** in Keyboard Layout Editor (or **KLE** for short) and adding **multi-layout** stuff to it to create a plate. Don’t worry about the section where he generates a plate file towards the end of the video though. That’s not relevant to this guide (though note if you’re designing an entire keyboard including case, generating a plate file is more relevant to the case design).
  - In his [second video](https://www.youtube.com/watch?v=cqayXajcmpU), hadi goes over some more stuff that **isn’t relevant** to this tutorial. He does mention some minor things that might come into consideration later such as spacebar stab holes being too close to the bottom edge of the pcb. 
  - His [third video](https://www.youtube.com/watch?v=vLGklanzQIc) is very technical but is the **most informative of the three** and the most relevant to actual PCB design in my opinion. In it, he describes the **pinout of the ATmega32u4** and **how a basic keyboard matrix works**. He also goes in depth on how you apply a switch matrix to a chosen layout, including how to account for **multi-layout** (e.g. split backspace). However, his justification for why keyboard matrices are the way they are is slightly pedantic in my opinion.

    Note, as far as I’m aware, hadi’s keyboard design tutorial stops at part 3. Comments have suggested that parts 4+ have existed but have since been deleted for some undeclared reason.
    {: .code-example }

## [**Ai03’s keyboard PCB guide**](https://wiki.ai03.com/books/pcb-design/chapter/pcb-designer-guide)
  - Ai03’s guide is short and detailed, however, **slightly outdated** (it recommends using an older version of KiCAD). In my opinion, it does a good job of showing how to set up a development environment and electronically design a PCB using an ATmega32u4 controller.
  - However, it falls short in the fact that it shows this **only for a 2x2 macropad**, with a **usb micro** connector (at least in the main tutorial parts). Realistically, most people seeking to make a keyboard are going to be looking to integrate an MCU into a more standard keyboard size where you don’t have a lot of room to fit components. Also, sometimes things aren’t explained in a way clear to those unfamiliar with EE.

## [**Masterzen’s PCB guide**](https://www.masterzen.fr/2020/05/03/designing-a-keyboard-part-1/) (parts 1-4)
  - Masterzen’s guide, as opposed to Ai03’s, shows how to make a keyboard PCB for a **65% Alps switch keyboard**. Masterzen’s is more in depth than Ai03, including a lot of information including explanations of certain components and what they do, plus what you should be looking for in certain parts. The guide also covers things such as how to export files from KiCAD for manufacturing with JLCPCB and their assembly service (which is realistically what you’re going to be using if you’re on a budget), as well as how to physcially hand solder the board and even write QMK firmware for it.
  - However, the images of the guide aren’t always consistent (fwiw certain steps get skipped from image to image) or sometimes things aren’t explained in a way clear to those unfamiliar with EE. That can definitely confuse beginners. Also, the guide is also on the **older KiCAD 5**, and is a little outdated in terms of the whole part/component choice scheme.
  - I definitely like his tutorial though, so I’ll be taking a lot of inspiration from it while filling in some of the gaps (things that personally confused me) in this guide.

## **Further**
  - The [**Atelier discord server**](https://discord.gg/b7vwhHS) is a great place for all keyboard creators (including PCB designers, case designers, etc) to ask questions and get help. It serves as a great tool for when (not if) you encounter errors not covered in this guide. There are many helpers there, and you may even catch me there.
  - [**Datasheets and Pinouts**](/basic-knowledge/mcus/#mcu-pinouts-and-datasheets) are also a great source of information, however they can be daunting to beginners who may not understand them. [Watch this video](https://www.youtube.com/watch?v=9r8JMbHc-xQ) if you want to learn more about how to read datasheets.
  - [**Sleepdealr's PCB Design Guidelines/Best practices**](https://gist.github.com/Sleepdealr/ab05f5edb82eae9e0393f4d63da55adf#schematics) gist also has some great, concise information.
  - **Documentation** 
    - [QMK Documentation](https://docs.qmk.fm/#/)
    - [VIA Documentation](https://www.caniusevia.com/docs/specification)
    - [VIAL Porting Guide](https://get.vial.today/docs/)

## Summary (My recommendation)
**I would recommend going through at least hadi's first and third video before continuing**. 

I will be mostly repeating most of the content in the Ai03 and Masterzen tutorials, so they are technically optional. I highly recommend opening up a datasheet (e.g. for an ATmega32u4) while creating your schematic + pcb (and actually reading the content inside) as they have useful information. 

Lastly, if you have any further questions that you cannot answer by going over above resources/googling, feel free to ask a question in the [Atelier discord server](https://discord.gg/b7vwhHS).

---

Now that you've got some more understanding, you can start actually creating your PCB: <br>
[Project Setup](/setup/){: .btn .btn-purple }
