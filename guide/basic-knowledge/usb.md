---
layout: default
title: USB
nav_order: 7
permalink: /basic-knowledge/usb/
parent: Basic EE Knowledge
---

# Universal Serial Bus (USB)
There are many varying standards for USB.

## USB2.0
Modern keyboards generally operate at USB 2.0 speeds. 

USB (2.0) connections consist of the following four lines: 
- one for **power** (+/5V/VCC)
- one for **ground** (-/GND)
- a **pair** of [**data lines**](/basic-knowledge/mcus/#data-traces)

<div class="code-example" markdown="1">
Below is the pinout of a USB-A connector:

![image](https://user-images.githubusercontent.com/23428162/151112391-13952470-97d8-4f20-a0cd-39e8c9e773cd.png)
</div>

## Micro-USB
Smaller USB connectors are preffered for devices such as keyboards or phones. Micro-USB is an example of one that used to be very popular (there is also mini-usb/usb-b).

<div class="code-example" markdown="1">
Below is the pinout of a Micro USB connector:

![image](https://user-images.githubusercontent.com/23428162/151113767-311c6d62-28b2-471e-a05c-976d84a35cf0.png)
</div>

## Type-C
Many keyboards nowadays opt to use a USB Type-C connector. Type-C connectors have a few extra pins required for hitting USB 3+ speeds that aren’t important for USB 2.0 operation.

<div class="code-example" markdown="1">
These are the pins on a standard Type-C connector required for a USB 2.0 keyboard: 

![image](https://user-images.githubusercontent.com/23428162/151113065-41c143ab-f90a-4ed8-953f-b7c95f8369ce.png)

**Type-C connections running on USB 2.0 devices also require 5.1k pullup resistors between the CC pins and ground.** You'll see this in the schematic for the keyboard later in the guide.
</div>

Note: There are different types of Type-C connectors (e.g. top mount, mid mount).

## Extra

<div class="code-example" markdown="1">
This is an optional (but interesting and informative) video on USB and how it applies to keyboards.

<iframe width="100%" height="400" src="https://www.youtube.com/embed/wdgULBpRoXk" title="How does a USB keyboard work?" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>