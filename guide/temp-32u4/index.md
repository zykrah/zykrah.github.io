---
layout: default
title: "[TEMPORARY] Tracing guidelines for 32u4"
permalink: /temp-32u4/
nav_order: 10
---

# [TEMPORARY] Tracing guidelines for 32u4

This page stands a temporary guide/cheat-sheet for how to wire up an ATMega32u4.

<div class="code-example" markdown="1">
**[WIP Notes for me]** Three main parts:
* USB/JST area
  * Option 1: USB C?
  * Option 2: JST?
  * Option 3: Both USB and JST?
  * ESD
  * Fuse
  * Data traces
  * Voltage regulator (STM, RP2040)
* MCU area (and other main components)
  * MCU
  * Decoupling capacitors
  * Terminating Resistors
  * Crystal
  * Debugging header
  * External Flash (RP2040)
* Switch matrix
  * Connecting Columns
  * Connecting Rows (don't cross over important traces just yet)
  * Bring all rows and columns near the MCU
* (Extra)
  * Other peripherals (e.g. OLED, etc)
  * LEDs (ARGB/WS2812, ISSI)
</div>

# Tracing/Routing Guideline 'Diagram'
A diagram I drew up, labelling components for a 32u4-based 2 layer Keyboard PCB. Based on a board I made a while ago. Please read all the notes.

![image](https://user-images.githubusercontent.com/23428162/170997119-b34ff4a4-c72c-4894-a658-aedada4f77db.png)

## Notes
- Rule of thumb, one 100nF decoupling cap per 5V pin.
- This is just a guideline showing how to place and wire up the main components for a 32u4 board. How you connect things to your GPIO pins (ie column/row pins) will depend on you. You can connect any row/column pin to any of the marked GPIO pins. See the 32u4 Pinout [here](https://github.com/zykrah/pcb-guide/wiki/2.-Basic-Knowledge#mcu-pinouts-and-datasheets-wip) for more information. See other sections of this guide for more information about switch matrices.
- Avoid crossing under your crystal area/traces with the 5V upstream trace. That's why it is a C/U shape.
- Probably add more ground vias around everywhere and you should be good in terms of grounding.
- The separated ground fill for the crystal isn't necessary.
- I did not include the ESD chip/terminating resistors in the above diagram.
- The USB pins are just a representation, they aren't accurate.

## Disclaimer
- This is just how I learnt to trace my 32u4 boards. I'm not entirely sure if this is the 100% best/correct way to do it for a 32u4.
- While I have not had a board manufactured this way, I am pretty sure others can vouch for this sort of layout/wiring.

# Extra

## 5V highlighted alone
(Ignore 10uF bulk cap placement in this photo, see diagram above)

![image](https://user-images.githubusercontent.com/23428162/170997855-6b8a857f-3534-403d-94ee-d5bba7564bba.png)


## GND highlighted alone
Keep in mind there is a ground fill on both sides (ignore 10uF bulk cap placement in this photo, see diagram above)

![image](https://user-images.githubusercontent.com/23428162/170997882-73194207-984d-4ce6-bcb4-cefdc38e33d0.png)


## XTAL (both) highlighted alone
Keep XTAL traces short by:
- Rotating the crystal and load caps appropriately
- Routing the XTAL traces BEFORE ground

![image](https://user-images.githubusercontent.com/23428162/170997895-905d59ea-8164-4f9a-972c-e044fabecf3d.png)
