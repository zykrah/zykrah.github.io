---
layout: default
title: QMK Environment Setup
nav_order: 2
permalink: /firmware/environment/
parent: Firmware
---

# Setting up a QMK Environment

## Contents

 - [Choose a QMK terminal](#choose-a-qmk-terminal)
 - [Install Git](#install-git)
 - [Learn basic Git terminology and basic CLI commands](#learn-basic-git-terminology-and-basic-cli-commands)
    - [CLI concept checklist](#cli-concept-checklist)
    - [Git concept checklist](#git-concept-checklist)
 - [Windows Terminal and Powershell 7 (Optional)](#windows-terminal-and-powershell-7-optional)
 - [Choose a QMK terminal](#choose-a-qmk-terminal)
    - [QMK MSYS](#qmk-msys) 
    - [QMK WSL](#qmk-wsl)
 - [Using Visual Studio Code](#using-visual-studio-code)
    

# Choose a text editor/IDE

I personally use [Visual Studio Code](https://code.visualstudio.com/) (VSC). It's free, works well for qmk-related purposes and has good community support. You can find out more about [using VSC with qmk_firmware down the page](#using-visual-studio-code).


# Install Git

If you haven't already installed Git (not to be mistaken with GitHub Desktop), you can find [the page for installing Git here](https://git-scm.com/download/win) (Windows).

## Learn basic Git terminology and basic CLI commands

I can't stress enough the importance of learning some basic Git commands/terminology. I've added a checklist below for most of the concepts you should understand before you continue. Otherwise, you'll probably learn about them on the way.

[This is a great rundown on git/github by freecodecamp](https://www.freecodecamp.org/news/learn-the-basics-of-git-in-under-10-minutes-da548267cc91/).


<div class="code-example" markdown="1">

### CLI concept checklist

 - The concept of a directory
 - How to change the current directory (`cd` command)

### Git concept checklist

> This is ranked in order of importance/how you should learn them. 

 - The difference between GitHub and Git
 - What a git **repository** is
 - The difference between a **local** and **remote** repository
 - What **cloning** a remote repository means, and how to do it
 - What **commits** are/do, and how to make and manage them
 - What **pulling** and **pushing** commits is/does
 - What **branches** are/do, and how manage them locally
 - What a **fork** of a repository is, and why people use them

> **Note**: There are ways of managing git repositories both graphically (e.g. utilising [VSC's source control tools](https://code.visualstudio.com/docs/sourcecontrol/overview)) and through commands (i.e. `git commit`, `git checkout`, etc). It'll come down to preference, however I generally use a **mix of both CLI and VSC** when I am working on firmware. [More info on VSC below](#using-visual-studio-code).
</div>


# Windows Terminal and Powershell 7 (Optional)

I would recommend using Windows' new Terminal if you're on Windows 10 and don't already use it (should be installed by default on W11). Find more about the [new Windows Terminal here](https://learn.microsoft.com/en-us/windows/terminal/). 

Also, If you're still using the old Powershell that comes default with W10, I would also recommend [installing Powershell 7](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows), which should work nicely with the new Windows Terminal.

> **Note**: Feel free to [customise your Terminal](https://learn.microsoft.com/en-us/windows/terminal/tutorials/custom-prompt-setup) to make it look fancy. You can also find more information on Google/YouTube if you so wish.


# Choose a QMK terminal

Assuming you're on Windows, there are two main options for setting up a QMK environment:
 1. [QMK MSYS](#qmk-msys) (simpler to use)
 2. [QMK WSL](#qmk-wsl) (faster, recommended)

> **Note**: I personally use QMK WSL, as it compiles things way faster. However, it is more tedious to set up.

## QMK MSYS

> **Note**: QMK MSYS takes incredibly long to compile firmware. I would reccomend QMK WSL if you plan on compiling and modifying firmware a lot. It will save you a lot of time.

To set up a QMK Environment with QMK MSYS, follow the steps laid out [in this guide by QMK themselves](https://msys.qmk.fm/guide.html#next-steps).

After running `qmk setup`, QMK MSYS will clone the offical `qmk/qmk_firmware` repository to `C:\Users\<user>`, setting it as the default remote (`origin`). It should also download/sync submodules/dependencies. Extra: If you wish to publicate your firmware and/or keep track of it online, [follow this section on how to set up a fork **WIP**]().

Otherwise, your QMK environment is now set up and you can run qmk commands.

To test, make sure you are in the qmk_firware directory (if not, use `cd qmk_firmware` to enter it) and then you can try a simple firmware compilation e.g. `qmk compile -kb hineybush/h88 -km via`. It should compile and output the firmware to the qmk_firmware folder.

> **Note**: If you can't find the directory in your file explorer, it's `C:\Users\<user>\qmk_firmware` (by default).

You can access QMK MSYS from anytime through the start menu (search up QMK MSYS). Note that it starts in the `C:\Users\<user>` by default, so make sure to `cd qmk_firwmare` each time to access the repo and compile firmware/run git commands.
{: .code-example }

## QMK WSL

Setting up QMK WSL can be a little tedious, but it is still relatively simple if you follow the appropriate processes.

First, to use QMK WSL, you'll have to enable virtualisation on Windows. You can find a [guide on enabling virtualisation here](https://support.microsoft.com/en-us/windows/enable-virtualization-on-windows-11-pcs-c5578302-6e43-4b4b-a449-8ced115f58e1).

You'll then have to actually install WSL. You can follow [Microsoft's instructions for installing WSL here](https://learn.microsoft.com/en-us/windows/wsl/install), but essentially you just run `wsl --install` in powershell. You might have to restart once or twice.

> **Note**: You can use either WSL 1 or WSL 2. See the [differences between WSL 1 and WSL 2 here](https://learn.microsoft.com/en-us/windows/wsl/compare-versions). There may also be some nuances when it comes to WSL and USB device access which may affect the ability to use `qmk flash` or qmk debugging. WSL 2 is generally recommended afaik.

Following that, you can now [install QMK WSL](https://qmk.github.io/qmk_distro_wsl/guide.html#next-steps). 

On the `qmk-admin` step, when it asks you to "Use your fork?", if you wish to publicate your firmware and/or keep track of it online, [follow this section on how to set up a fork **WIP**](), otherwise, leave it as the default `qmk/qmk_firmware`. This will clone the official qmk repo to your WSL directory and set it as the default remote (`origin`).
{: .code-example }

> **Note**: When using QMK WSL with WSL 2, make sure you only access files that are placed within the QMK WSL file directory (by default `\\wsl$\QMK\`). Attempting to access the normal OS filesystem will be very very slow. I would recommend sticking to this even if you are using WSL 1 though.

Open QMK WSL (you can access it by searching it in start menu) and run `qmk setup`. It should download/sync submodules/dependencies.

Otherwise, your QMK environment is now set up and you can run qmk commands.

To test, make sure you are in the qmk_firware directory (if not, use `cd qmk_firmware` to enter it) and then you can try a simple firmware compilation e.g. `qmk compile -kb hineybush/h88 -km via`. It should compile and output the firmware to the qmk_firmware folder.

> **Note**: If you can't find the directory in your file explorer, it's `\\wsl$\QMK\home\qmk\qmk_firmware` (by default).

You can access QMK WSL from anytime through the start menu (search up QMK WSL). Note that whenever it starts, it opens in the `home/qmk` directory by default, so make sure to `cd qmk_firwmare` each time to access the appropriate repo to compile firmware/run git commands.
{: .code-example }


# Using Visual Studio Code

I recommend [Visual Studio Code](https://code.visualstudio.com/) (VSC).

You can open the `qmk_firmware` directory as a folder in VSC to utilise its powerful IDE/text editor and source control features. It should automatically be recognised as a git repository if everything is setup correctly.

This also works for WSL directories, VSC should automatically detect it as a WSL instance and setup everything appropriately.

You can learn more about [VSC's source control tools here](https://code.visualstudio.com/docs/sourcecontrol/overview), or find [some neat VSC extensions here](https://marketplace.visualstudio.com/vscode).

> **Tip**: You can search/run commands through the **command palette** with `Control + Shift + P` if you can't find the button for a specific action in the GUI.

You should now be able to use VSC to modify qmk firmware as you wish. I have a list of the [main VSC features I use for qmk firmware here **WIP**]().
