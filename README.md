# QFSAE PCB Projects

This repository stores the various PCB designs made by the QFSAE team as well as useful reference designs.

# Altium

The QFSAE team designs its boards using Altium. If you do not have Altium installed, Please contact Logan or Brent to obtain the appropriate licensing information to get Altium up and running on your computer. In regards to manufacturing, the team most often makes use of [JLCPCB](https://jlcpcb.com/). Traditionally, PCBs made by QFSAE members have been populated by hand in house. However, due to the restrictions imposed on team operation by the ongoing COVID-19 pandemic, it has become of utmost importance to create an Altium workflow which allows us to outsource our board assembly in an efficient manner. JLCPCB offers an economical assembly service for surface mount components with the following caveats.

- All surface mount components must be on one side of the board
- Through hole parts will not be soldered
- The components must be from the JLCPCB parts that they keep in stock at their manufacturing facility.
- The part being populated on the board must be within the size and clearance constraints given by JLC PCB.

In order to meet these manufacturing conditions, we must restrain the SMD parts we use to those offered by JLCPCB and use Altium design rules that reflect the manufacturing capabilities of JLCPCB when checking our PCB layouts. The parts library is quite vast with over 30,000 components. With that being said, there will still be cases where a custom footprint or one from another library must be used. In that case, check with another team member to verify that it can be hand soldered properly. The sections below provide instructions on importing the JLC parts libraries, which are included in this repository as well as design rules.

## Library Setup
The JLC PCB Altium component libraries are located in the libraries folder of this repository. Import the libraries using the instructions [here](https://www.altium.com/documentation/altium-designer/integratedlibrary-dlg-addremovelibrariesformavailable-file-based-libraries-ad). Your final available libraries panel should like the photo below. Be sure to also keep the Altium default libraries.

![My Altium Lib Panel](https://imgur.com/XRmxG6a)

## Design Rule Configuration

TODO 

## Version Control

Altium has integrated Git support. The instructions below show how to configure the Git extension. However, using command line git or some other client is also fine. 

[Altium Git Integration](https://www.altium.com/documentation/altium-designer/using-version-control-ad)

# Design Review Checklists

## Schematic Checklist
- All important nets named
- No 4 point connections
- Short circuit protection via current monitor implementation or fuse, Specifically for power rails supplying expensive parts
- No circuit compilation errors

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

# Contributing a New Design and Starting a Review
To contribute a new PCB design, commit the Altium project in its own folder at the top level of the repository on a new branch matching the project name. Open a pull request for this branch to merge it to the `master` branch. To initiate the design review, assign several other electrical team members to the pull request. Board change requests and feedback will be provided as comments on the pull request. Once each reviewer has verified that the PCB satisfies the relevant checklist above, the designer will generate Gerber files for the PCB and commit them. After the Gerbers are double checked, the pull request is merged and the board is ordered. If the PCB arrives and has errors, then the design is removed from `master` branch and the process starts again.

