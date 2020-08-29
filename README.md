# QFSAE PCB Projects

This repository stores the various PCB designs made by the QFSAE team as well as useful reference designs.

# Altium Designer

The QFSAE team designs its boards using Altium. If you do not have Altium Designer (hereby referred to as "Altium") installed, Please contact Logan or Brent to obtain the appropriate licensing information to get Altium up and running on your computer. In regards to manufacturing, the team most often makes use of [JLCPCB](https://jlcpcb.com/). Traditionally, PCBs made by QFSAE members have been populated by hand in house. However, due to the restrictions imposed on team operation by the ongoing COVID-19 pandemic, it has become of utmost importance to create an Altium workflow which allows us to outsource our board assembly in an efficient manner. JLCPCB offers an economical assembly service for surface mount components with the following caveats.

- All surface mount components must be on one side of the board
- Through hole parts will not be soldered
- Board must be at least 20 x 20 mm
- The components must be from the JLCPCB parts that they keep in stock at their manufacturing facility.
- The part being populated on the board must be within the size and clearance constraints given by JLC PCB.

In order to meet these manufacturing conditions, we must restrain the SMD parts we use to those offered by JLCPCB and use Altium design rules that reflect the manufacturing capabilities of JLCPCB when checking our PCB layouts. The parts library is quite vast with over 30,000 components. With that being said, there will still be cases where a custom footprint or one from another library must be used. In that case, check with another team member to verify that it can be hand soldered properly. The sections below provide instructions on importing the JLC parts libraries, which are included in this repository as well as design rules.

## Library Setup
The JLC PCB Altium component libraries are located in the libraries folder of this repository. Import the libraries using the instructions [here](https://www.altium.com/documentation/altium-designer/integratedlibrary-dlg-addremovelibrariesformavailable-file-based-libraries-ad). Your final available libraries panel should like the photo below. Be sure to also keep the Altium default libraries and search for parts when making your schematic through the integrated library and not the schematic libraries. 

![Altium Panel](https://i.imgur.com/d9237hu.png)

## Design Rule Configuration

The design rules you import will depend on the layer count and copper density you want to use (JLCPCB offers 1oz and 2oz). The `.RUL` Altium design rule files can be found in `pcb/libraries/jlcpcb-design-rules-stackups/design-rules/altium`. The instructions for importing the design rules into your project can be found [here](https://www.altium.com/documentation/altium-designer/constraining-the-design-design-rules-ad#!exporting-and-importing-rules).

## Version Control

Altium has integrated Git support. The instructions below show how to configure the Git extension. However, using command line git or some other client is also fine. 

[Altium Git Integration](https://www.altium.com/documentation/altium-designer/using-version-control-ad)

# Design Review Checklists

## Schematic Checklist
- All important nets named
- No 4 point connections
- Short circuit protection via current monitor implementation or fuse, Specifically for power rails supplying expensive parts
- No circuit compilation errors
- Active low signals have `_n` at the end of their net name
- Differential pair nets are named with `_P` and `_N` endings. Both nets in the pair should also be marked with the differential pair schematic marking in Altium

## 2 Layer Boards

- No DRC errors
- All SMD parts on one layer
- IR Calculations for high current traces
  * The width should be large enough such that temperature increase for the expected current is no more than 5 to 10 degrees celsius
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
  * The width should be large enough such that temperature increase for the expected current is no more than 5 to 10 degrees celsius
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

# Contributing a New Design and Starting a Review

To contribute a new PCB design, follow these steps:

- Commit the Altium project in its own folder at the top level of the repository on a new branch matching the project name
- Open a pull request on this branch set to merge to the `master` branch
- To initiate the design review, assign several other electrical team members to pull request via the request review feature on GitHub. Board change requests and feedback will be provided as comments on the pull request.
- Once each reviewer has verified that the PCB satisfies the relevant checklist above, the designer will generate Gerber files for the PCB and commit them
- After the Gerbers are double checked, the pull request is merged and the board is ordered. If the PCB arrives and has errors, then the design is removed from `master` branch and the process starts again.
- Process Example: https://github.com/qfsae/pcb/pull/2
