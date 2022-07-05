---
layout: default
title: Light Emitting Diodes (LEDs)
nav_order: 5
permalink: /basic-knowledge/leds/
parent: Basic EE Knowledge
---

# Light Emitting Diodes (LEDs)

If you’re living in the 21st century, you probably know what Light Emitting Diodes (LEDs) are. They take a voltage, and emit light. They can be pretty bright for how small they are, but can also be power hungry at full brightness if used in large quantities/arrays.

<div class="code-example" markdown="1">
ARGB (adressable red, green, blue) LEDs, e.g. `WS2812(B)` LEDs, will consume more power because they actually consist of three LEDs, one for red, green and blue. They also contain a controller on-board to interpret a data signal that requires further power.

WS2812 LEDs up close:

![image](https://hackaday.com/wp-content/uploads/2017/01/sidebysidenotext_featured.png)
</div>

**I won’t be covering how to add a per-key RGB** LED switch matrix as it is out of the scope of this guide, but I may make a follow up tutorial in the future. Other resources exist online already if you want to learn how (or you can just ask people), but I **wouldn’t recommend attempting it for a first PCB.**

**Note**: Dumb/common anode LEDs require a matrix and dedicated RGB controller chip, whereas ARGB LEDs such as WS2812s have onboard controllers.
{: .code-example }

---

Continue: <br>
[PCBs](/basic-knowledge/pcbs/){: .btn .btn-purple }
