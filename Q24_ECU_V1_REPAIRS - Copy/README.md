# Template PCB Readme

## Purpose

- Write a few sentences here about what features the board will have.
- What problems does it solve?
- How will it fit into the broader electrical system?

## Scope

- Discuss what your design will be responsible for here.
- Include assumptions about what will need to be provided in order for the board to work. For example, the power requirements, software libraries etc.
- Write about specific features required for the board to serve its purpose. For example, "the dash PCB must be able to both send and receive CAN bus messages."
- Are there any uncertainities? Could the outcome of a different project effect the scope of this one?

## Design / Mechanical Requirements

- List specific design requirements here.
- These could be things like board height and shape constraints.
- What mounting holes are needed to fit the board into the corresponding mechanical assembly?

## Manufacturing

- This section is for you to state how the board will be manufactured. This will effect the final board layout.
- How many layers are needed?
- What specific manufacturer will you work with?
- Will the board be assembled or hand soldered? If it is assembled, what parts library are you using and will the manufacturer be able to source those parts? This is important as some fab houses like JLC PCB will have limited part selection to choose from.

## Timeline

- Give a rough timeline of when each stage of the project will be complete
  - When will schematics be finished?
  - How much time is required to complete the layout?
  - Time set aside for design reviews
  - Manufacturing of the board and associated lead time
  - Time required to bring-up and test the board

## Implementation Description

- Provide implementation details here.

### Hardware

- What are the key components of the circuit?
- What I/O is on the board? What types of connectors are employed?
- What reference designs have you used? For example, if you followed the Mock ECU schematic to implement to a voltage regulator, explain the design choice and any changes you made to the circuit. Also refer to any datasheets or other resources used to build the correct circuit around a given part.
- Include a system block diagram.

### Software

- What software resources (if any) are needed to get the board up and running? Do the software already exist or must new libraries / tools be designed from scratch?
- Link to relevant software resources in the zenith repository

## Test Plan

TODO

- Should include checking all power rails for shorts
- Power on test (status LED turns on)

- Are the rails all producing the correct voltages? (it is helpful to include your DMM readings here)
- Are the clock signals on the board the correct speed? If there is an MCU, is it making use of the external clock?
  - If an oscilloscope is available, consider capturing a plot of the clock signal that includes frequency and peak to peak voltage.
- I/O Testing. This should be an exhaustive test of all the input and outputs of your board. Some examples are given below.
  - If there is an MCU, can you program it with the qfsae debugger? Does the debugger provide enough power or are external sources needed?
  - Do LEDs connnected to the MCU work?
  - Does CAN bus work?
- Also remember to explain the steps you took when something did not work as expected. For example, "The neopixel were not working correctly, I discovered that the voltage translator required an output enable signal to be enabled to push the data through."
- There is no prescribed format for this section but it should clearly test each part of the board and provide background on problems with the design and how to fix them if possible.
