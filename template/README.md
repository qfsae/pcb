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

- Functional Description of the PCB
  - What purpose will it serve?
  - Is it for the car or is it support equipment?
  - What manufacturer is being targeted and what libraries are in use?
  - List any design requirements discussed here. These could be size, height, power constraints etc.
  - Provide any useful figures that help visualize these constraints. This will clarify what is in scope for the particular design.

## Implementation Description

- Provide implementation details here.

### Hardware
- What are the key components of the circuit?
- What I/O is on the board? What types of connectors are employed?
- What reference designs have you used? For example, if you followed the Mock ECU schematic to implement to a voltage regulator, explain the design choice and any changes you made to the circuit. Also refer to any datasheets or other resources used to build the correct circuit around a given part. 
- Include a system block diagram.

### Software
- What software resources (if any) are needed to get the board up and running? Do the software already exist or must new libraries / tools be designed from scratch?


