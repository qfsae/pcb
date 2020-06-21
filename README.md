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
TODO

## Design Rule Configuration

TODO 

## Version Control

Altium has integrated Git support. The instructions below show how to configure the Git extension. However, using command line git or some other client is also fine. 

TODO

# Design Review Checklist

TODO

- No DRC errors?
- all SMD parts on one layer? (might be able to get this into a custom design rule)
- IR calculations for high current traces?
- Proper filter capacitor placement (important for STM32 MCU)
- All important nets named?
- No 4 point connections?
- Ground and power planes for 4 layer boards
- Ground pours on top and bottom with stitching vias for 2 layer boards?
- Length matching for differential signals like CAN.
- Ground plane far away from CAN or other differential traces (Ie USB) to make sure they reference one another and not ground.

# Contributing a New Design
TODO
- Pull request
- work through design review in comments of PR
- Board is only merged to master branch when it is ready to order
- Any new board or revision that had problems is marked as such to prevent flawed circuits from being copied in other designs.


