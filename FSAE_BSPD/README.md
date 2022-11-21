# Brake System Plausibility Device Testing Board

### Queen’s Racing Q23

## Brake System Plausibility Device (BSPD)

The BSPD is a non-programmable shutdown system with the intent to act as a fail-safe in case a vehicle’s throttle is stuck open. All Formula Society of Automotive Engineers (FSAE) teams are required to have a BSPD if their team is running an electric throttle unit. The BSPD will shut down power to the vehicle if any of the following conditions are true (FSAE 2023 Rules):

1. Both of the following for more than one second:
   - Hard braking (for example >0.8 g deceleration but without locking the wheels)
   - Throttle greater than 10% open
2. Loss of signal from the braking sensor(s) for more than 100 msec
3. Loss of signal from the throttle sensor(s) for more than 100 msec
4. Removal of power from the BSPD circuit
   In the Case of the Queen’s Racing Q23 Car, the team will be running the ‘QTRONIC ENGINEERING BSPD FSAE 2020 v0.4’ board which is adherent to the 2023 FSAE internal combustion (IC) rules

## Purpose

To be able to compete on track at an FSAE event, any FSAE team running an electric throttle unit must be able to confirm their BSPD functions to regulations. This is confirmed during a technical inspection at the competition. Teams will be required to prove the following

1. The BSPD signals and function must be able to be checked during Technical Inspection by having one of:
   - A separate set of detachable connectors for any signals from the braking sensor(s), throttle sensor(s) and removal of power to only the BSPD device.
   - An inline switchable breakout box available that allows disconnection of the brake sensor(s), throttle sensor(s) individually and power to only the BSPD device.
     The BSPD Test board was created to showcase the regulations above.
     The BSPD Test board was created to showcase the regulations above.

## Circuitry

### Power

The BSPD Test Board can be run off either a 12V battery pack, or a power supply that is capable of outputting 12V. To satisfy the input voltages for the ‘QTRONIC ENGINEERING BSPD FSAE 2020 v0.4’, both a 12V and a 5V rail are required. This is achieved by using a 12V-5V volt “Switch Mode Power Supply” set up. This method provides an efficient way of producing a 5V rail with minimal power loss; it prolongs battery life when using a battery pack.

### Communication

The BSPD Test Board has a 1x6 pin header that allows for communication to the BSPD. The tester board has three outputs TPS, BSE, and ‘BSPD_IN’ (5v), and one input ‘BSPD_OUT’. ‘BSPD_IN’ is a 5V output to the BSPD. TPS and BSE are talked about in detail in the next section. ‘BSPD_OUT’ is connected to a series of LEDs. Since BSPD_OUT is normally open (NO), the LEDs should be initially high. When the BSPD is triggered, the LEDs will transition to low.

### TSP and BSE input

The test board has two outputs that act as the Throttle Position Sensor (TPS) along with the Brake System Encoder (BSE). These two outputs are used to simulate break and throttle inputs to the BSPD and allow for the user to trigger the BSPD fault modes. Both the TPS and BSE output each have three switches that control the outputs. Switches one (SW1), three (SW3), and five (SW5) affect the BSE. Switches two (SW2), four (SW4), and six (SW6) affect TPS.

#### Switches Five (SW5) and Six (SW6)

Both SW5 and SW6 are used to drive the output high. When the switches are closed, the voltages seen by the input pin of SW3 or SW4 is five volts. Otherwise, five-volt input is set to float.
####Switches One (SW1) and Two (SW2)
SW1 and SW2 give the user the opportunity to change the output voltage. This is done by toggling between either a ten-kilohm resister, or a ten-kilohm variable resistor (potentiometer).

#### Switches Three (SW3) and Four (SW4)

SW3 and SW4 act as a gate to the BSPD. When the switches are set to pin 1, the BSPD can see the input. When the switches are set to pin 3, break/throttle inputs are disconnected, allowing the user to simulate sensor disconnect.

### Switch Truth Table

| SW5/SW6 | SW1/SW2 | SW4/SW3 | BSE/TPS Outputs |
| ------- | ------- | ------- | --------------- |
| P1      | P1      | P1      | 0.687V- 5V      |
| P1      | P1      | P3      | 0V              |
| P1      | P3      | P1      | 0.687V          |
| P1      | P3      | P3      | 0V              |
| P3      | P1      | P1      | 5V              |
| P3      | P1      | P3      | 0V              |
| P3      | P3      | P1      | 5V              |
| P3      | P3      | P3      | 0V              |
