---
layout: default
title: Firmware
permalink: /firmware/
nav_order: 9
# has_children: true
---

# Firmware

This will be my attempt to cover most of the basics for writing QMK firmware for custom keyboards, addressing most common misconceptions.

WIP: split into sections
 1. Intro, common misconceptions, figuring out what you need
 2. Setting up QMK environment
 3. Modifying various QMK settings, creating required QMK files
 4. Compiling and flashing
 5. Extra, usage and other tips

---

## Common questions/misconceptions

---

### Firstly, should I use kbfirmware.com/builder.mrkeebs.com?

Short answer: **No.**

They're based on older versions of QMK. You also wont get any support for them since all they give you is the finished firmware file. That makes troubleshooting difficult.

---

### What is firmware? QMK?

Firmware refers to __what is actually running on the keyboard__. 

For custom keyboards, the most common firmware to run is **QMK firmware**.

As for what QMK is (in general), as per the [official site](https://docs.qmk.fm/#/?id=what-is-qmk-firmware):

QMK (Quantum Mechanical Keyboard) is an open source community centered around developing computer input devices. The community encompasses all sorts of input devices, such as keyboards, mice, and MIDI devices. A core group of collaborators maintains QMK Firmware, QMK Configurator, QMK Toolbox, qmk.fm...
{: .code-example }

**Links to:** QMK official [website](https://qmk.fm/), [documentation](https://docs.qmk.fm/#/), [github repository](https://github.com/qmk/qmk_firmware), and [discord server](https://discord.com/invite/Uq7gcHh).

---

### What does QMK Configurator do?

[QMK Configurator](https://config.qmk.fm/#/) is used to compile firmware of existing keyboards with your own keymap. It will spit out compiled firmware that you just need to flash. This is fine to use if you just want to set the keymap of your keyboard once.

However, if you want to __dynamically remap__ your keyboard, you can make use of VIA or VIAL. See below.

---

### So what is VIA?

VIA is a piece of **software**. In essence, it's a program that runs on your computer. All it does is __communicate__ to the firmware (QMK) on your keyboard to tell it to do things, i.e. remap keys, change lighting, etc. This means the __changes you make are stored on the keyboard itself__.

VIA was popularised a few years back. It was made separate from QMK, but QMK eventually added official support for the VIA protocol. This also means that the VIA and QMK development teams are separate.

VIA has recently gone through many changes, transitioning from [V2 to V3](https://www.caniusevia.com/docs/v3_changes). In the past, VIA has commonly been used as a desktop application. Nowadays, you can either use the [website](https://usevia.app/), or alternatively the [NEW desktop application](https://github.com/the-via/releases/releases).

**Links to:** VIA official [website](https://www.caniusevia.com/), [documentation](https://www.caniusevia.com/docs/specification), [list of precompiled firmware](https://www.caniusevia.com/docs/download_firmware), and [app source code](https://github.com/the-via/app) (app downloads linked above). For VIA support, head to the [QMK discord server](https://discord.com/invite/Uq7gcHh).

<div class="code-example" markdown="1">
<a id="via_detection"></a>

### A note on VIA support - Why doesn't VIA detect my keyboard?

VIA will only *automatically* detect keyboards that are part of their [official VIA list](https://github.com/the-via/keyboards). This means popular keyboards are more likely to be detected automatically.

This detection works by checking the USB VID (Vendor ID) and PID (Product ID) programmed onto the firmware, and seeing if it matches the VID/PID of any of the __keyboard definitons (i.e. via jsons)__ in the [official VIA list](https://github.com/the-via/keyboards).

So, if you have a less popular keyboard that's meant to have VIA support, you may have to find the via json to manually load [wip, link to the guide for loading via jsons manually]. You can usually find this on the vendor's discord server or possibly linked on the page/website where you bought the keyboard from.

If you cannot find the via json for your keyboard, you may have to create one yourself. [WIP: link to guide to creating VIA json]

If your keyboard does not get detected in VIA even after manually loading the via json, it's possible you have the wrong json, or your keyboard is not running a VIA-enabled version of QMK firmware. [WIP: link to guide for enabling VIA on existing keyboards]
</div>

---

### What's the difference between VIA and VIAL?

VIAL is __separate__ from VIA and QMK. It's also a program which serves a similar purpose, but has extra features. 

<div class="code-example" markdown="1">
Notably:
- Keyboard definitions (i.e. `vial.json`) are stored on the keyboard itself, so they get detected automatically, without requiring any online repositories, [unlike with VIA](#via_detection).
- Stronger Macro configuation. https://get.vial.today/manual/macros.html
- Tap Dance configuration from within the UI (key double tap, hold). https://get.vial.today/manual/tap-dance.html
- Combos configuration from within the UI https://get.vial.today/manual/combos.html
- Key Override configuration from within the UI. https://get.vial.today/changelog/release-0.5.html#dynamic-key-overrides
</div>

(Tap dance, combos and key overrides are offered in vanilla QMK, but require custom code, and are not dynamically reconfigurable in any UI)

__To utilise the extra features that VIAL offers, you need to flash a modified version (i.e. a fork) of QMK onto your keyboard.__

NOTE: This fork of QMK is **unofficial**, meaning the QMK developers have nothing to do with it. Please don't go to the QMK server asking for VIAL help. There is a dedicated VIAL server.
{: .code-example }

**Links to:** VIAL official [website](https://get.vial.today/), [app download](https://get.vial.today/download/), [github repository](https://github.com/vial-kb/vial-qmk), [documentation](https://get.vial.today/docs/), and [discord server](https://discord.gg/zNKEUXTKwF). There is also an [unofficial site with pre-compiled VIAL firmware](https://keyboard.gay/).

---

# So how do I get firmware onto my keyboard?

This will come down to what you're starting with.

<div class="code-example" markdown="1">
Here are the common scenarios:
- I want to [compile & flash QMK firmware for an existing keyboard](#compiling-and-flashing-qmk-firmware).
- I want to [enable 1000Hz polling rate](#the-1000hz-myth) on my custom keyboard which runs QMK already.
- I want to write basic [QMK firmware from scratch](#qmk-firmware-from-scratch) (for a PCB that I designed myself/I bought).
- I want to [add VIA support](#adding-via-support) for a keyboard that only runs vanilla QMK firmware.
- I have a keyboard with VIA support, but I want to [port it to VIAL](#porting-to-vial).
- I have an [OEM (e.g. chinese prebuilt or gaming) keyboard](#oem-keyboards-and-qmk) that doesn't have QMK by default, but I want to use QMK and VIA/VIAL.
</div>

In almost all scenarios, you will first want to learn how to [set up an environment](#setting-up-your-environment) for modifiying and compiling QMK firmware. **[WIP: link to that guide]**

**wip...**

---

## Setting up your environment

If you're going to be doing any modification, compiling or flashing of firmware, you need to set up your QMK environment.

This will involve a bit of Git. Git is generally better to use than just downloading zip files and extracting, as Git will version control and allow you to pull changes from the internet quickly. You can [learn more about git here](https://www.atlassian.com/git/tutorials/what-is-git).

QMK have an [official guide for setting up an environment](https://docs.qmk.fm/#/newbs_getting_started), but it can be a little confusing.

**WIP... clearer setup guide for vanilla qmk/via, and vial; and explanation of how qmk environment works**

---

### Compiling and flashing QMK Firmware

To compile firmware, you need to first [set up your environment](#setting-up-your-environment).

Official [QMK documention](https://docs.qmk.fm/#/newbs_building_firmware?id=build-your-firmware).

To flash QMK firmware, you can generally use [QMK Toolbox](https://github.com/qmk/qmk_toolbox). However, some keyboards may require other methods of flashing. Keyboards need to be in `bootloader` mode to flash them. There are various ways of entering the bootloader, depending on the design of the PCB.

**WIP... will be a separate page with more explanation on compiling and flashing, for vanilla qmk, via, and vial**

---

### The 1000Hz myth

Short answer: the latest version of QMK will have 1000Hz polling rate enabled **by default**. This means you do NOT have to add any lines in the firmware to enable it.

---

### QMK Firmware from scratch

Official [QMK documention](https://docs.qmk.fm/#/newbs).

<div class="code-example" markdown="1">
To write firmware from scratch, you need information about the following:
 - The keyboard's MCU
 - The layout of the keyboard
 - The pinout of rows/columns
</div>

If you designed the PCB/it's open sourced, this information should be readily available. Otherwise you may have to reverse engineer the PCB.

**WIP... Link to separate page for writing QMK firmware**

---

### Adding VIA support

VIA have documentation on how to add support for keyboards [here](https://www.caniusevia.com/docs/specification). However, their documentation isn't always the best/clearest.

You need to find the your keyboard's base firmware to work off. If your board is more popular, it will usually be located in the official [QMK repository](https://github.com/qmk/qmk_firmware/tree/master/keyboards), so you can just work off the official QMK repository as it is. 

<div class="code-example" markdown="1">
In essence, to add VIA support to a keyboard already in the official QMK repository, you need to add the following:
- A new `via` folder inside the `keymaps` folder
- A `rules.mk` file with `VIA_ENABLE = yes` inside
- A via json file that you can use to get VIA to recognise your keyboard
</div>

**wip... Link to separate page for adding VIA support**

---

### Porting to VIAL

'Porting' assumes that the keyboard you want to add VIAL support for already has VIA support. Generally, you can find that out by downloading the **VIAL** app, pressing `File > Download VIA Definitions` in the top left, and then seeing if your keyboard has the `[VIA]` tag next to its name (if it loads at all). If your keyboard does not show up, it means your keyboard either does not have VIA-enabled QMK firmware flashed, OR it's not part of VIA's official list of keyboards (see section on `Why doesn't VIA detect my keyboard?`).

If your keyboard does have VIA support, you'll need to find the source code for that firmware. If your board is more popular, you can usually find it in the official [QMK repository](https://github.com/qmk/qmk_firmware/tree/master/keyboards). There should be a `via` folder within your keyboard's `keymaps` folder.

Since VIAL requires a fork of QMK, when [setting up your environment](), you will have to actually use the `vial-qmk` [repository](https://github.com/vial-kb/vial-qmk) instead of the normal `qmk_firmware` repository. The `vial-qmk` repository is generally kept up-to-date with `qmk_firmware`, meaning you should also be able to find your keyboard in `vial-qmk`, along with it's `via` keymap folder. 

If there is also a `vial` folder in the `keymaps` folder, that means your keyboard has already been ported to VIAL, and you can simply skip this section and compile and flash the vial firmware **[WIP: link to guide for compiling and flashing]** to use VIAL.

**wip... Link to separate page for porting to VIAL**

---

### OEM Keyboards and QMK

Unfortunately, QMK does not officially support a lot of the MCUs that cheaper OEM keyboards (e.g. Redragon, Keychron K/S-series, Ajazz, Womier) typically use.

However, you can look into [SonixQMK](https://github.com/SonixQMK).

---

## Extra Tools and Firmware scripts

I have a [site](https://zykrah.me/) for making the generation of QMK and VIAL firmware files easier/faster (e.g. `config.h`, `info.json`, `vial.json`, `keymap.c`). It converts a single KLE into all those files. It requires a bit of firmware-writing knowledge to use. Make sure you read the [documentation](https://github.com/zykrah/firmware-scripts).

Xelus also has some [tools for firmware](https://xelus.netlify.app/guides) (`KLE -> RGB`, `KLE -> VIA`, `Layout Macro generator`).

Jels also has a similar [firmware generator](https://jels02.github.io/kicad2qmk/) in the works that converts a KiCAD project into QMK firmware. This hasn't been tested for more complex layouts so be weary.

---

## Lastly, side note: What's after VIA and VIAL?

Ultimately, VIA and VIAL are both technically unofficial programs that may not always folllow the visions of the official QMK developers. For instance, VIA developers may add some features that they want, and then it's left up to the QMK developers to adapt the firmware to allow keyboards to support those features.

Hence, QMK XAP is in the works. It's a new protocol that seeks to replace VIA while still maintaining VIA support. Ideally, QMK will have it's own version of VIA in the form of a new QMK configurator.

You can find more information about QMK XAP and the new QMK configurator on the QMK discord server. It's still in the works though.