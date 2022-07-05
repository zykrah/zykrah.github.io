---
layout: default
title: Introduction
permalink: /intro/
nav_order: 2
---

# Introduction

## Disclaimer
First, **I am by no means an electrical engineer**. This guide should serve as just another resource, used in combination with other online guides and your own research. Asking questions, trying things out for yourself and taking advantage of all the resources you can find are, without a doubt, important if you want to pick up any sort of skill. Don’t worry though, I’ll be linking some places/resources you can use/go over.

**Note**: this guide will include a lot of text. I **highly recommend reading all the text** properly and **not to skim read**. Missing one or two important steps can be costly, and it saves me from answering questions that could be answered by reading the guide properly.
{: .code-example }

I will also be working on some video(s) to hopefully portray all this information in a much more digestible format. This written guide will allow me to make edits and take in feedback before that happens though.

## Intro
This guide is aimed at keyboard enthusiasts who want to start making their own PCBs. Whether you just want a personalized macropad or perhaps want to design an entire keyboard, this guide should cover most of the things I’ve personally learnt in my (admittedly short) time in the custom mechanical keyboard hobby designing keyboard PCBs. 

Hopefully, this can act as a simple guide for creating your first basic PCB, without too many bells and whistles. The keyboard PCB iceberg can get pretty deep, and this guide will likely only scratch about the top 30-50% of it. 

I will try my best to release future guides that include some **more interesting things**, e.g. per-key RGB, split keyboards, a keyboard with an ARM microcontroller, etc.
{: .code-example }

## Prerequisite - Keyboard knowledge
Ignoring EE (electrical engineering) knowledge first, I personally believe that something you should be asking yourself before considering moving forward is whether or not you know much about the keyboard hobby in general. While the knowledge as a whole is not imperative to creating a keyboard PCB, it certainly helps to at least have a **basic-novice level knowledge of custom keyboards**, as many design considerations all throughout the process of designing a keyboard PCB can fall on that kind of knowledge. Though, if you’re reading this tutorial, you hopefully at least have built/own one custom mechanical keyboard. If not, I would probably stop here and maybe invest some more time (and money) into the hobby before considering designing your own keyboard PCB…

## Time and Cost
Next, I’d like to briefly discuss one thing that many usually don’t discuss at the beginning: time and cost. I will be going further in-depth over cost-considerations throughout the guide, but I think it is important to first make clear that designing a keyboard PCB (especially your first few) is **time consuming**, and getting them manufactured **isn’t free** (despite what some manufacturer’s sites/people may say).

If you want a loose answer on how much time and money it will take to get 5 (MOQ) decent, fully functioning 60% keyboard PCBs (with integrated controllers) running QMK/VIA in your lap, I would bet at least ~12 hours of actual work, a few weeks of actual time and at least ~150 USD in costs (assembled by one of the cheaper manufacterers like JLCPCB). A small macropad without assembly will only set you back 2-10 USD/board before shipping (however that doesn't take into account the costs of components you'll need). Costs and time will greatly vary though, depending on different considerations throughout the entire process. Like I mentioned however, I’ll make sure to go over these sorts of considerations throughout the entire guide.
{: .code-example }

## Software required
Furthermore, this guide is specifically catered towards the majority (in which I stand). I’ll be using **64-bit Windows 10**, but if you're competent enough to use **Linux**, you should be able to follow along with no issues. 

<div class="code-example" markdown="1">
I'll be using various free programs, commonly used for designing keyboard PCBs:
- For its open source nature and the fact that there are many online resources for it, I’m opting for **KiCAD** for designing the PCB. 
- I’ll also be introducing **Git/GitHub**, an extremely powerful tool/platform (e.g. can be used for version control). 
- Additionally, I’m also going to be using **Visual Studio Code** (later) in the guide because it’s free and what I’m comfortable with. Feel free to follow along or just use whatever other IDE/text editors you may be already used to.
</div>

Start the guide by learning some EE basics: <br>
[Basic EE Knowledge](/basic-knowledge/){: .btn .btn-purple }