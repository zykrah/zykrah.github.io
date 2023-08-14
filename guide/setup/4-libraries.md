---
layout: default
title: "Step 4: Installing KiCad libraries"
nav_order: 4
permalink: /setup/installing-libraries/
parent: Setup
---

# Step 4: Installing KiCad libraries

A KiCad library generally contains symbols, footprints and/or 3d models for use in KiCad. KiCad comes with many common symbols and footprints in the libraries installed by default (which I recommend using wherever possible), however footprints/symbols for things such as MX switches require a third-party library.

<div class="code-example" markdown="1">
## Library options

There are a few popular options for third-party keyboard libaries:
- [Ai03's MX/Alps lib](https://github.com/ai03-2725/MX_Alps_Hybrid) (recommended)
  - Contains footprints for MX, MX basic hotswap (+ anti-shear hotswap), Alps, Kailh choc, and MX/Alps combo.
  - Has dedicated MX-NoLED and MX-LED symbols
- [Ebastler's marbastlib](https://github.com/ebastler/marbastlib) (recommended)
  - Contains footprints for MX, MX hotswap (plated holes), choc, LEDs (e.g. WS2812B)
  - Unlike the Ai03 lib, stabs are separate footprints, meaning to add a stabilized key, you combine a 1u footprint and stab footprint of apprpriate size, then align the two in the pcb editor (I'll be showing how in this guide). 
  - Has symbol for stabililzers
  - Has many 3D models
- [Perigoso's keyswitch lib](https://github.com/perigoso/keyswitch-kicad-library)
  - Contains MX, basic MX hotswap, Alps, choc and MX/Alps switches (footprints only), however stabs are separate.
  - Has some 3D models
- Keebio's libs ([footprints](https://github.com/keebio/Keebio-Parts.pretty)/[symbols](https://github.com/keebio/keebio-components))
</div>

<div class="code-example" markdown="1">
## Installing Marbastlib
I recommend [marbastlib](https://github.com/ebastler/marbastlib). It has a large range of footprints for all types of keyboards, however, note that **some of the footprints are untested** (they haven’t been put on a production board for physical testing, but should theoretically be correct). We’ll only be using confirmed working footprints in this guide, but if you're concerned just read over the git repo. 

As of recently, marbastlib has also added symbols for switches, so mostly everything (footprints, symbols, etc) needed for keyboards can be found in this library alone.

Now let’s install the marbastlib library as a **git submodule**. Open the git bash as shown: 

![image](https://user-images.githubusercontent.com/23428162/151098886-13ecbfbf-15e2-4277-b8ae-c99e8f9a3301.png)


You can also just open Git Bash from your windows menu (or otherwise) and run the command `cd <filepath>`. E.g. `cd /c/Users/.../Documents/Keyboards/pcb-guide`.
{: .code-example }

This should open a bash terminal:

![image](https://user-images.githubusercontent.com/23428162/151098902-ef15afd9-9b79-466b-902c-e5de947587af.png)


**Note**: The shortcut to paste in Git Bash is `Shift+Insert`, if you don't have insert binded, just right-click and press paste.
{: .code-example }

From here, just type `git submodule add https://github.com/ebastler/marbastlib`. 

Then open the `.gitmodules` file and edit it as following:
```
[submodule "marbastlib"]
    path = marbastlib
    url = https://github.com/ebastler/marbastlib
    branch = v6-untested
```
Then run `git submodule update --init --remote`.

This will add the marbastlib submodule with the included untested footprints (in case you need them) to your git repo.

<div class="code-example" markdown="1">
## Adding Footprint libs to the KiCad PCB Editor

Now open your pcb editor in your KiCad project:

![image](https://user-images.githubusercontent.com/23428162/177284226-dbad8654-cca7-4081-be4d-a44e862e561f.png)

Go to `Preferences > Manage Footprint Libraries...` and add the footprint libaries as follows:

![image](https://user-images.githubusercontent.com/23428162/177283938-aa05d15e-1345-4488-a767-585fc15bfa0f.png)

![image](https://user-images.githubusercontent.com/23428162/177283849-4fe0032c-9c1c-4243-8418-8400a5227a46.png)

![image](https://user-images.githubusercontent.com/23428162/177284157-c42ac5a1-1e25-4060-ac65-55f614646f2e.png)

The libraries should be added. Click `Ok`.
</div>

<div class="code-example" markdown="1">
## Adding Symbol libs to the KiCad Schematic Editor

Now open your schematic editor:

![image](https://user-images.githubusercontent.com/23428162/177284286-59c77740-cd48-4f36-aad6-b74fb06f0a7b.png)

Go to `Preferences > Manage Symbol Libraries...` and add the symbol libaries as follows:

![image](https://user-images.githubusercontent.com/23428162/177285714-477757eb-44e0-4b4b-8a44-e88d2bebf961.png)
![image](https://user-images.githubusercontent.com/23428162/177285393-b8ad7568-219e-4e66-85da-b499dfc0b2ed.png)
![image](https://user-images.githubusercontent.com/23428162/177285995-d46e8a3b-2095-47cc-af26-54e7be55957b.png)

The libraries should be added. Click `Ok`.

</div>

That should succesfully install the `marbastlib` librar(ies) into your KiCad project.

</div>

## Installing other libaries

To install, git bash into your project folder and just run `git submodule add <url>`.

Then follow the same instructions in KiCad as was done for marbastlib above.

---

## Tips Regarding submodules/kicad libaries

If you need to update your submodules, run `git submodule update --remote`.
{: .code-example }

If you need to remove a submodule, see [this link](https://stackoverflow.com/questions/1260748/how-do-i-remove-a-submodule/1260982#1260982).
{: .code-example }

---

## Gitignore
You can also add a `.gitignore` file. Read about what a gitignore file does [here](https://www.w3schools.com/git/git_ignore.asp?remote=github). Kicad generates certain folders/files that you don't really want in your public remote git repository. 

<div class="code-example" markdown="1">
Example of a `.gitignore` I usually use:

```
*-backups/
_autosave-*
*.kicad_sch-bak
*.kicad_pcb-bak
#auto_saved_files#
\#auto_saved_files\#
```
</div>

---

Continue to Step 4.5: <br>
[Syncing Changes](/setup/syncing-changes/){: .btn .btn-purple }
