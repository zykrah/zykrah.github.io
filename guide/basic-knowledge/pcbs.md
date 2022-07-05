---
layout: default
title: Printed Circuit Boards (PCBs)
nav_order: 6
permalink: /basic-knowledge/pcbs/
parent: Basic EE Knowledge
---

# Printed Circuit Boards (PCBs)

PCBs are made of core fiberglass material (most commonly FR4) with various layers of copper in which **traces** connect various **components** together.

## Layers
Complex PCBs such as PC motherboards can have upwards of 14 layers, however PCBs can get as simple as just 1 layer. For keyboards, **2 layers is generally all you need**.

## Vias
[What are PCB vias?](https://www.pcbgogo.com/Blog/PCB_Vias__Something_You_Need_To_Know.html)
{: .code-example }

Vias act as pathways between layers, connecting traces and allowing signals to **hop from layer to layer**. They are important, but should only be used when necessary. I'll be going over via usage further in depth later.

<div class="code-example" markdown="1">
The below image shows a 6 layer pcb, and how vias connect traces between the layers:

![image](https://www.allaboutcircuits.com/uploads/articles/via_intro_1.png)
</div>

<div class="code-example" markdown="1">
Good videos about PCBs (second video is pretty informative)

<iframe width="100%" height="400" src="https://www.youtube.com/embed/H9pGbLJknDk" title="How Do PCBs Work?" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<iframe width="100%" height="400" src="https://www.youtube.com/embed/YJr-kHy6STg" title="What is a PCB?" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

---

## WIP
* SMT/D and THT
* Component “form factors” (packages)
* Symbols
* Footprints