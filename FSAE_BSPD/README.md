# Brake System Plausibility Device (BSPD)

> The BSPD is a non-programmable shutdown system with the intent to act as a fail-safe in case a vehicle’s throttle is stuck open. All Formula Society of Automotive Engineers (FSAE) teams are required to have a BSPD if their team is running an electric throttle unit. The BSPD will shut down power to the vehicle if any of the following conditions are true (FSAE 2023 Rules):

1. Both of the following for more than one second:
   a. Hard braking (for example >0.8 g deceleration but without locking the wheels)
   b. Throttle greater than 10% open
2. Loss of signal from the braking sensor(s) for more than 100 msec
3. Loss of signal from the throttle sensor(s) for more than 100 msec
4. Removal of power from the BSPD circuit
   > In the Case of the Queen’s Racing Q23 Car, the team will be running the ‘QTRONIC ENGINEERING BSPD FSAE 2020 v0.4’ board which is adherent to the 2023 FSAE internal combustion (IC) rules

#Purpose

> To be able to compete on track at an FSAE event, any FSAE team running an electric throttle unit must be able to confirm their BSPD functions to regulations. This is confirmed during a technical inspection at the competition. Teams will be required to prove the following

1. The BSPD signals and function must be able to be checked during Technical Inspection by having one of:
   a. A separate set of detachable connectors for any signals from the braking sensor(s), throttle sensor(s) and removal of power to only the BSPD device.
   b. An inline switchable breakout box available that allows disconnection of the brake sensor(s), throttle sensor(s) individually and power to only the BSPD device.
   The BSPD Test board was created to showcase the regulations above.

> The BSPD Test board was created to showcase the regulations above.

##Circuitry
