---
layout: default
title: Capacitors
nav_order: 3
permalink: /basic-knowledge/capacitors/
parent: Basic EE Knowledge
---

# Capacitors

Capacitors (or ‘caps’ for short) are mainly used to **reduce noise** (unwanted change of a signal/current due to electromagnetic interference, or "EMI") and **prevent voltage drop** in a circuit. This will be explained more further in this section ([decoupling capacitors](/basic-knowledge/mcus/#decoupling-capacitors)).

To further explain capacitors, it is necessary to explore some of the mathematical models that represent their function.

1. i = C \frac{dV}{dt}
In other words, the current through a capacitor is equal to the change in voltage over time (multiplied by a constant, C, representing the capacitance [e.g. 100nF, .1uF]). This means that a change in voltage will change how much current flows through a capacitor. If the voltage increases, the capacitor "opens" and allows more current to flow through it (effectively reducing its impedance, AKA resistance, and lowering the voltage across it). If the voltage decreases, the opposite happens--the impedance of the capacitor increases and less current is allowed through it. 

2. Z = \frac{1}{j \omega C}
Here, Z is the impedance (analagous to resistance) of a capacitor. \omega represents the frequency across the capacitor (e.g. 60 Hz, 120 radians per second, 12 MHz). As the frequency increases, the impedance of the capacitor decreases. This low impedance "sinks" higher frequencies to ground, eliminating them from the input voltage of your microcontroller. 

<div class="code-example" markdown="1">
See the below video for more information ([mirror](https://www.youtube.com/watch?v=X4EUwTwZ110)):

<iframe width="100%" height="400" src="https://www.youtube.com/embed/X4EUwTwZ110" title="Capacitors Explained - The basics how capacitors work working principle" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

What capacitors look like

![image](https://www.theengineeringknowledge.com/wp-content/uploads/2020/12/Different-Types-of-Capacitors-and-Uses.jpg)
</div>

---

Continue: <br>
[Ground](/basic-knowledge/ground/){: .btn .btn-purple }
