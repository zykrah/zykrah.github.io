---
layout: default
title: Firmware
permalink: /firmware/
nav_order: 9
# has_children: true
---

# Firmware

This will be my attempt to cover most of the basics for writing QMK firmware for custom keyboards, addressing most common misconceptions.

---

## But what is firmware?

Firmware refers to what is actually running on the keyboard. For custom keyboards, the most common firmware to run is QMK.

## So what about VIA?

VIA is a piece of software. In essence, it's a program that runs on your computer. All it does is talk to the firmware (QMK) on your keyboard to tell it to do things, i.e. remap keys, change lighting, etc.

This means the changes you make are stored on the keyboard itself.

VIA was popularised a few years back. It was made separate from QMK, but QMK eventually added official support for the VIA protocol.

## What's the difference between VIA and VIAL?

VIAL is separate from VIA and QMK. It's also a program which serves a similar purpose, but has [extra features](https://get.vial.today/manual/). 

**To utilise the extra features that VIAL offers, you need to flash a modified version (i.e. a fork) of QMK onto your keyboard.**

This fork of QMK is unofficial, meaning the QMK developers have nothing to do with it. Please don't go to the QMK server asking for VIAL help. There is a dedicated VIAL server.

## Should I use kbfirmware.com/builder.mrkeebs.com?

**Short answer: No.**

They're based on older versions of QMK. You also wont get any support for them since all they give you is the finished firmware file. That makes troubleshooting difficult.

## A note on VIA support - Why doesn't VIA detect my keyboard?

VIA will only *automatically* detect keyboards that are part of their [official list](https://github.com/the-via/keyboards). This means popular keyboards are more likely to be detected automatically.

This detection works by checking the USB VID (Vendor ID) and PID (Product ID) programmed onto the firmware, seeing if it matches the VID/PID of any of the keyboard definitons (basically, via jsons) in the [official list](https://github.com/the-via/keyboards).

So, if you have a less popular keyboard that's meant to have VIA support, you may have to find the via json to manually load [wip, link to the guide for loading via jsons manually]. You can usually find this on the vendor's discord server or possibly linked on the page/website where you bought the keyboard from.

If you cannot find the via json for your keyboard, you may have to create one yourself. [WIP: link to guide to creating VIA json]

If your keyboard does not get detected in VIA even after manually loading the via json, it's possible your keyboard is not running a VIA-enabled version of QMK firmware. [WIP: link to guide for enabling VIA on existing keyboards]

---

## So how do I write firmware? How do I add VIA or VIAL support?

This will come down to what you're starting with.

In almost all scenarios, you will first want to learn how to set up an environment for modifiying and compiling QMK firmware. [WIP: link to that guide]

Here are the common scenarios:
- I want to compile firmware for an existing custom keyboard.
- I want to enable 1000Hz polling rate on my custom keyboard which runs QMK already.
- I want to add VIA support for a keyboard that only runs vanilla QMK firmware.
- I have a keyboard with VIA support, but I want to port it to VIAL.
- I want to write firmware from scratch for a PCB that I designed myself.
- I have an OEM (e.g. chinese prebuilt or gaming) keyboard that doesn't have QMK by default, but I want to use QMK and VIA/VIAL.

## The 1000Hz myth

Short answer: the latest version of QMK will have 1000Hz polling rate enabled **by default**. This means you do NOT have to add any lines in the firmware to enable it.

## Adding VIA support

VIA have documentation on how to add support for keyboards [here](https://www.caniusevia.com/docs/specification). However, their documentation isn't always the best/clearest.

You also need to find the base firmware to work off. If your board is more popular, it will usually be located in the official [QMK repository](https://github.com/qmk/qmk_firmware/tree/master/keyboards), so you can just work off the official QMK repository as it is. 

In essence, to add VIA support to a keyboard already in the official QMK repository, you need to add the following:
- A new `via` folder inside the keymaps folder
- A `rules.mk` file with `VIA_ENABLE = yes` written inside
- A via json file that you can use to get VIA to recognise your keyboard

wip...

## Porting to VIAL

'Porting' assumes that the keyboard you want to add VIAL support for already has VIA support. Generally, you can find that out by downloading the **VIAL** app, pressing `File > Download VIA Definitions` in the top left, and then seeing if your keyboard has the `[VIA]` tag next to its name (if it loads at all). If your keyboard does not show up, it means your keyboard either does not have VIA-enabled QMK firmware flashed, OR it's not part of VIA's official list of keyboards (see section on `Why doesn't VIA detect my keyboard?`).

If your keyboard does have VIA support, you'll need to find the source code for that firmware. If your board is more popular, you can usually find it in the official [QMK repository](https://github.com/qmk/qmk_firmware/tree/master/keyboards). There should be a `via` folder within your keyboard's `keymaps` folder.

Since VIAL requires a fork of QMK, you will have to actually use the [vial-qmk repository](https://github.com/vial-kb/vial-qmk) instead of the normal `qmk_firmware` repository. The `vial-qmk` repository is generally kept up-to-date with `qmk_firmware`, meaning you should also be able to find your keyboard in `vial-qmk`, along with it's `via` keymap folder. If there is also a `vial` folder in the `keymaps` folder, that means your keyboard has already been ported to VIAL, and you can simply skip this section and compile and flash the vial firmware [WIP: link to guide for compiling and flashing] to use VIAL.

wip...


## Lastly, side note: What's after VIA and VIAL?

Ultimately, VIA and VIAL are both technically unofficial programs that may not always folllow the visions of the official QMK developers. For instance, VIA developers may add some features that they want, and then it's left up to the QMK developers to adapt the firmware to allow keyboards to support those features.

Hence, QMK XAP is in the works. It's a new protocol that seeks to replace VIA while still maintaining VIA support. Ideally, QMK will have it's own version of VIA in the form of a new QMK configurator.

You can find more information about QMK XAP and the new QMK configurator on the QMK discord server. It's still in the works though.