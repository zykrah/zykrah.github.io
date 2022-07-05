---
layout: default
title: Setup
permalink: /setup/
nav_order: 4
---

# Setup

## Step 1: Downloading Required Software
This section will mostly be a repeat of the first few sections of Ai03’s/Masterzen's guides, just with updated KiCad and different libraries.

Download [KiCad 6.0.6](https://www.kicad.org/download/) (the latest stable version as of writing). The installer file is about 1 GB (make sure you aren’t installing a lite version), and KiCad itself takes about 6 GB of storage.

Also download [GitHub Desktop](https://desktop.github.com/). We’ll be using it to set up a git repository which is useful for tracking version history.

**Git is a powerful tool** for software related projects, so learning to use it correctly is definitely something I would advise if you tackle these sorts of projects often.

<div class="code-example" markdown="1">
**Note**: If you want to learn more about Git/GitHub, I recommend the the written guide [by w3schools](https://www.w3schools.com/git/default.asp?remote=github).

The following video is also useful:

<iframe width="100%" height="400" src="https://www.youtube.com/embed/DVRQoVRzMIY" title="Git Tutorial for Beginners - Git & GitHub Fundamentals In Depth" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

---

## Step 2: Setting up a Git repo with GitHub Desktop
If you’re familiar with Git/GitHub, feel free to set up a repo however you’d like.
{: .code-example }

Create an account on GitHub if you haven't already.

Now run the installer for GitHub Desktop.

Once GitHub Desktop opens, log in and create a new repository (`File > New repository…`):

![image](https://user-images.githubusercontent.com/23428162/151100217-d1e8e0ce-a621-4540-985e-f5364e92e2f7.png)


Give your repository a name and description (I recommend a name in lowercase separated by dashes). 
For the path, you can choose whatever you like. 
It will create a folder in the path that you choose with your repository name (in this case `C:/Users/.../Keyboards/pcb-guide`).

![image](https://user-images.githubusercontent.com/23428162/151098341-e947e954-9765-445b-81b9-949d6988dc0d.png)


Once it is set up, publish the repository as below:

![image](https://user-images.githubusercontent.com/23428162/151098364-c009f2fa-b549-41c5-98f5-4c534bb22bc7.png)


If you want, you can untick `Keep this code private`:

![image](https://user-images.githubusercontent.com/23428162/151098373-18e15f2d-26b2-4565-91b6-2cc1e631df67.png)


If you go to where you created your git repo, you should see the following files:

![image](https://user-images.githubusercontent.com/23428162/151098389-391f1d07-3e92-42f3-82e2-f70dfc9840e9.png)


<div class="code-example" markdown="1">
Note: if you can’t see the `.git` folder or the extension names (e.g. `.md`), you should check the following boxes in File Explorer:

![image](https://user-images.githubusercontent.com/23428162/151098410-f128d708-ff7c-44e0-b139-5990641a5e5a.png)
</div>


If you go to your repo on the GitHub website, it should look something like this:

![image](https://user-images.githubusercontent.com/23428162/151098419-4bdfcc49-d167-4338-b20e-f7b056e356f6.png)


---

Feel free to adjust it how you would like, by modifying the `README.md` or otherwise. For the purposes of this guide, I won’t be bothering.

---

## Step 3: Setting up KiCad
Run the installer for KiCad and go through the install process.

Make sure these options are enabled when installing:

![image](https://user-images.githubusercontent.com/23428162/151098265-421e1b77-7c49-43e6-9063-ec033a1e1ddb.png)


Now open KiCad. It should look like this:

![image](https://user-images.githubusercontent.com/23428162/151098659-a7f20028-81ca-45cd-a6b0-5bcac1e64450.png)


Create a new project (File > New Project...):

![image](https://user-images.githubusercontent.com/23428162/151098467-94830dff-6e14-4c62-a1e2-b450335b8bef.png)


Save the project file in the repository folder created earlier. Make sure to uncheck `Create a new folder for the project`. Name the project whatever you want, but generally it’s easiest to just name it the same thing as the repository:

![image](https://user-images.githubusercontent.com/23428162/151098548-f895c37a-ed24-4632-988f-e7a182007862.png)


Just press `Yes` if you see this pop-up:

![image](https://user-images.githubusercontent.com/23428162/151098490-3b197670-2f50-49ea-b59c-bf1f6f8deea8.png)


Now, you should commit to the git repository. Here's how you commit in GitHub Desktop:

![image](https://user-images.githubusercontent.com/23428162/151106575-53af2f75-060b-4732-bdea-6520220aa2cc.png)

Note how it shows the changes made on the left.
{: .code-example }

**You should commit after every important change, in case you ever need to revert.**
{: .code-example }

---

## Step 4: Installing KiCad libraries
A KiCad library generally contains symbols, footprints and/or 3d models for use in KiCad. KiCad comes with many common symbols and footprints in the libraries installed by default (which I recommend using wherever possible), however footprints/symbols for things such as MX switches require a third-party library.

<div class="code-example" markdown="1">
### Library options

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
### Installing Marbastlib
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
    branch = untested
```
Then run `git submodule update --init --remote`.

This will add the marbastlib submodule with the included untested footprints (in case you need them) to your git repo.

<div class="code-example" markdown="1">
### Adding Footprint libs to the KiCad PCB Editor

Now open your pcb editor in your KiCad project:

![image](https://user-images.githubusercontent.com/23428162/177284226-dbad8654-cca7-4081-be4d-a44e862e561f.png)

Go to `Preferences > Manage Footprint Libraries...` and add the footprint libaries as follows:

![image](https://user-images.githubusercontent.com/23428162/177283938-aa05d15e-1345-4488-a767-585fc15bfa0f.png)

![image](https://user-images.githubusercontent.com/23428162/177283849-4fe0032c-9c1c-4243-8418-8400a5227a46.png)

![image](https://user-images.githubusercontent.com/23428162/177284157-c42ac5a1-1e25-4060-ac65-55f614646f2e.png)

The libraries should be added. Click `Ok`.
</div>

<div class="code-example" markdown="1">
### Adding Symbol libs to the KiCad Schematic Editor

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

### Installing other libaries

To install, git bash into your project folder and just run `git submodule add <url>`.

Then follow the same instructions in KiCad as was done for marbastlib above.

---

### Tips Regarding submodules/kicad libaries

If you need to update your submodules, run `git submodule update --remote`.
{: .code-example }

If you need to remove a submodule, see [this link](https://stackoverflow.com/questions/1260748/how-do-i-remove-a-submodule/1260982#1260982).
{: .code-example }

---

### Gitignore
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

## Step 4.5: Syncing changes

Once you are done installing submodules, I recommend once again committing, then pushing to origin.

`Pushing to origin` will **sync your changes with the remote github repository**.
{: .code-example }

See:

![image](https://user-images.githubusercontent.com/23428162/177290902-a2be19e0-e66f-40ef-bb5a-da538a327f3e.png)

**Note**: You may have varying changes than in the screenshot above.
{: .code-example }

---

![image](https://user-images.githubusercontent.com/23428162/151123430-c43cd289-543c-45ee-801e-ca7f93fbdc38.png)

---

At this stage, your project folder should look something like this:

![image](https://user-images.githubusercontent.com/23428162/177289616-35c53caf-9ff9-4243-a425-0c9275b65c30.png)

**Note**: You may have varying folders depending on what libraries you chose.
{: .code-example }
