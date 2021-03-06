# QFSAE PCB Projects

This repository stores the various PCB designs made by the QFSAE team as well as useful reference designs.

## Cloning The Repository

- If you do not have git installed, please download it [here](https://git-scm.com/downloads).
- Clone the repository using the git command line interface (CLI) by typing the command `git clone https://github.com/qfsae/pcb.git`.
- Download the Altium Designer library modules using `git submodule update --init`.
- Alternatively to the CLI, you can install [GitHub Desktop](https://desktop.github.com/). Cloning the repository with GitHub Desktop will automatically download the sub modules.
- For a full picture of Git and its various functions, check out this Git and GitHub [handbook](https://www.notion.so/Git-GitHub-61bc81766b2e4c7d9a346db3078ce833).

# Altium Designer

The QFSAE team designs its boards using Altium Designer. If you do not have Altium Designer (hereby referred to as "Altium") installed, Please contact Logan or Brent to obtain the appropriate licensing information to get Altium up and running on your computer. In regards to manufacturing, the team most often makes use of [JLCPCB](https://jlcpcb.com/). Traditionally, PCBs made by QFSAE members have been populated by hand in house. However, due to the restrictions imposed on team operation by the ongoing COVID-19 pandemic, it has become of utmost importance to create an Altium workflow which allows us to outsource our board assembly in an efficient manner. JLCPCB offers an economical assembly service for surface mount components with the following caveats.

- All surface mount components must be on one side of the board
- Through hole parts will not be soldered
- Board must be at least 20 x 20 mm
- The components must be from the JLCPCB parts that they keep in stock at their manufacturing facility.
- The part being populated on the board must be within the size and clearance constraints given by JLC PCB.

In order to meet these manufacturing conditions, we must restrain the SMD parts we use to those offered by JLCPCB and use Altium design rules that reflect the manufacturing capabilities of JLCPCB when checking our PCB layouts. The parts library is quite vast with over 30,000 components. With that being said, there will still be cases where a custom footprint or one from another library must be used. In that case, check with another team member to verify that it can be hand soldered properly. The sections below provide instructions on importing the JLC parts libraries, which are included in this repository as well as design rules.

## Installation & Setup

Altium is licensed software. In order to get a license, contact the electrical lead (Logan - Q21) to get your email added to the organization. Once you've been added, you should receive an email with your login. It is recommended that you sign in to [altium.com](https://www.altium.com/) and change your password.

### Download

Altium is available for download on their [downloads page](https://www.altium.com/products/downloads). You will be prompted to log in, so make sure you have your account set up first! Download the lastest version (20.x.x - Q21). Most versions are backwards compatible, so it is not essential to stay completely up to date but it is recommended to always use the latest major release.

Default installation settings are recommended.

### Using a license

Before you can use Altium you must first sign into your account and check out one of the organization's seats. This can be done by clicking on the "Not Signed In" dropdown in the top right of the window and choosing "Sign in":

![Sign in Window](https://i.imgur.com/ysroxVE.png)

Once signed in, you must choose a license to take out in the License Management window. You can access this window by clicking "Licenses" from the same spot as shown above. To use a license, select it and click on the Use button below it. Make sure that the license's status is OK, and there are still unassigned seats. The team has 10 seats for now, so only 10 people can use the license at the same time.

![License Panel](https://i.imgur.com/Kl5esJi.png)

Please try to release your license whenever you are not working in Altium we don't run out of seats!

_Note:_ If you are having issues using a license, verify your system time is correct. This issue is common on Windows/Linux dual boots where rebooting back into Windows can offset the time.

### Part Library Setup

For the majority of projects the only library required is the JLCPCB Altium component library. It can be located in the [libraries](https://github.com/qfsae/pcb/tree/master/libraries) folder of this repository, under **"JLCSMT_LIB"**.

#### Adding Parts Libraries

You can add parts libraries to your Altium installation so their components are always available for use in any project. Most of these steps are applicable to any library, but first a word on getting the JLC library we use:

The JLC library is stored in our repository as a git submodule in the [libraries](https://github.com/qfsae/pcb/tree/master/libraries) folder. Locally, if this folder does not contain the JLC library make sure you set up the submodules using `git submodule update --init`.

With the library files savd locally (in this case the JLC library), open Altium and bring up the components panel if it is not already visible on the right of the window. This can be done by clicking on the **"Panels"** button in the bottom right corner and choosing **"Components"**. This panel is always useful to have open because it is where you search for parts to place.

Click on 3-lines icon and choose **"File-based Libraries Preferences"**

![library preferences](https://i.imgur.com/SKV5402.png)

In the pop-up window, make sure you are in the **"Installed"** tab, and click on **"Install"**. In the file chooser, make sure to change the visible items from **"Integrated Libraries"** to **"All Installable Libraries"**. Navigate to the downloaded JLC parts library and select all of the library files (not the folder).

![library preferences window](https://i.imgur.com/gVEcPqD.png)

Your final available libraries panel should look similar to the photo below. Be sure to also keep the Altium default libraries and search for parts when making your schematic through the integrated library (using the components panel) and not the schematic libraries themselves.

![Altium Panel](https://i.imgur.com/d9237hu.png)

For more information about available part libraries, see the [documentation](https://www.altium.com/documentation/altium-designer/integratedlibrary-dlg-addremovelibrariesformavailable-file-based-libraries-ad).

#### Other Libraries

For a broader selection of high quality footprints we use the open source Celestial Library. To install this library, follow the installation guide for the [Celestial Altium Library](https://altiumlibrary.com/GetStarted).

The component you are looking for will not always appear in the JLC PCB or Celestial libraries. If this is the case, then use Altium's manufacturer part search feature. Try to avoid using online part footprints wherever possible, as it can become difficult to maintain. If it is found that a number of common parts cannot be found in either library, we may start an internal QFSAE library with custom footprints.

### Design Rule Configuration

Design rules help ensure that the PCB you lay out can actually be manufactured. Once you have completed your design, a **design rule check** is run to validate that it does not violate any rules. In most cases, for example minimum component clearance, the violation will be shown visually in the PCB editor with hatched shading. It is vital that your design passes design rule checking before being manufactured. Since design rules pertain to PCBs and not schematics, \*\*it is recommended to design your schematic completely

Since our PCB's are primarily manufactured at JLCPCB, we must tailor our design rules to their capabilities. Thankfully, we can import sets of design rules depending on the type of board being designed. The design rules you import will depend on the layer count and copper density you want to use (JLCPCB offers 1oz and 2oz). The `.RUL` Altium design rule files can be found in the `pcb/libraries/jlcpcb-design-rules-stackups/design-rules/altium` folder. Instructions for importing the design rules into your project can be found [here](https://www.altium.com/documentation/altium-designer/constraining-the-design-design-rules-ad#!exporting-and-importing-rules).

## Version Control

Altium has integrated Git support. The instructions below show how to configure the Git extension. However, using command line git or some other client is also fine.

[Altium Git Integration](https://www.altium.com/documentation/altium-designer/using-version-control-ad)

# Design Review Checklists

## Schematic Checklist

- All important nets named
- No spaces in net names (use underscores)
- Net names do NOT begin with numbers or other special characters such as `+-/\`. This makes naming software variables corresponding to a certain net easier.
- No 4 point connections
- Short circuit protection via current monitor implementation or fuse, Specifically for power rails supplying expensive parts
- No circuit compilation errors
- Active low signals have `_n` at the end of their net name
- Differential pair nets are named with `_P` and `_N` endings. Both nets in the pair should also be marked with the differential pair schematic marking in Altium

## 2 Layer Boards

- No DRC errors
- All SMD parts on one layer
- IR Calculations for high current traces
  - The width should be large enough such that temperature increase for the expected current is no more than 5 to 10 degrees celsius
- Board is mechanically sound, dimensions are correct and component height does not create mechanical conflicts
- IO ports and connectors double checked such that they are accessible when the board is fully assembled
- No unconnected ground (remove dead copper button checked on Altium polygon object or add stitching via)
- Ground pour on top and bottom layers.
- Stitching vias
- Length matching for high speed signals and differential pairs
- Proper filter capacitor placement for MCU layout (as close to the pin as possible and in the path of current flow)

## 4 Layer Boards

- No DRC errors
- All SMD parts on one layer
- IR Calculations for high current traces
  - The width should be large enough such that temperature increase for the expected current is no more than 5 to 10 degrees celsius
- Ground and power plane
- Board is mechanically sound, dimensions are correct and component height does not create mechanical conflicts
- IO ports and connectors double checked such that they are accessible when the board is fully assembled
- Length matching for high speed signals and differential pairs
- Proper filter capacitor placement for MCU layout (as close to the pin as possible and in the path of current flow)
- No buried vias as JLCPCB cannot fabricate these.

## Polygons

- Check the pour order of polygons to ensure no shorting will take place between polygons (Should also be caught in DRC)
- Do NOT use polygons with curved edges or shallow angles, stick to 90 and 45 degree angles
- For hand soldering, all parts should have some form of thermal relief
- Remove all dead copper using the option in Altium
- Ensure that all Polygons are re-poured before running a DRC
- Ensure Polygons pour over all same net objects so they connect to traces of the same net
- Checklist does not apply to ground and power planes, only to polygons used in routing.
- Do NOT use overlapping polygons, combine the two polygons together into one and adjust the final shape accordingly.

## Release Checklist

The release checklist requires a sign-off meeting with a senior electrical team member. When you are ready to release your design to a vendor, please run through this checklist with a senior member to generate the fabrication files.

- DRC check has been run before creating the fabrication files (fab package) and there are no errors.
- All polygons have been repoured before generating fab package (Check for any shelved polygons too! DRC will warn of this as well).
- Fabrication files were generated using the output job to ensure the BOM, pick and place and gerbers are in sync with one another.
- Use [gerbv](https://sourceforge.net/projects/gerbv/) to open up the gerbers, a senior member can help with this. Look at the top and bottom layers and try to see if anything could be missing.
  - Is the silkscreen there? Is it correct?
  - Look through the paste layers, will paste be applied to all the correct pads? (needs to be correct for assembly or stencil use)
  - Look at the top and bottom solder, is copper exposed in the correct places? (needs to be correct for assembly or stencil use)
  - Is the correct board outline present? (Mechanical Layer 1, also called GM1)
  - Are board cutouts correct? Ex. Are the mounting holes actually drilled holes? (Make sure you are pulling in NC Drill file into gerbv)

# Contributing a New Design and Starting a Review

To contribute a new PCB design, follow these steps:

- Make sure you are up to date on master. To do this, you can run `git status` and confirm that you're currently tracking the master branch, and then run `git pull`. If you are not on master already, make sure any changes in the current branch are pushed or stashed and run `git checkout master`
- Start a new branch using `git checkout -b branchName`
- Commit the Altium project in its own folder at the top level of the repository on a new branch matching the project name
- Open a pull request on this branch, set it to merge to the `master` branch
- To initiate the design review, assign several other electrical team members to pull request via the request review feature on GitHub. At minimum, assign the electrical lead for review. Board change requests and feedback will be provided as comments on the pull request.
- Once each reviewer has verified that the PCB satisfies the relevant checklist above, the designer will generate Gerber files for the PCB and commit them
- After the Gerbers are double checked, the pull request is merged and the board can be ordered. If the PCB arrives and has errors, then the design is removed from `master` branch and the process starts again.
- Process Example: <https://github.com/qfsae/pcb/pull/2>

# Viewing Designs Without Opening Altium

Altium has a [web tool](https://www.altium.com/viewer/) that allows you to upload Altium SchDoc and PcbDoc files and view them in browser. This may be handy for Mac or Linux users who need to quickly reference or review designs without rebooting or accessing a VM. The tool provides visual renderings and BOM information allowing for full design access separate from Altium.
