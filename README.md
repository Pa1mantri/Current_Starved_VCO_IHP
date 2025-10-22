# Current Starved Voltage Controlled Oscillator

## Table Of Contents

- [Abstract](#abstract)
- [Design Schematic](#design-schematic)
- [Simulation](#simulation)
- [Specification table](#specification-table)
- [Conclusion](#conclusion)
- [Acknowledgement](#acknowledgement)
- [References](#references)
  
## Abstract
Voltage Controlled Oscillator is the heart of the many modern electronics as well as communication system. A voltage controlled oscillator or VCO is an electronic oscillator designed for producing oscillation frequency by a controlled input voltage. The frequency of oscillation is varied by the applied controlled voltage. This project describes a design and implementation of three Stage Current Starved CMOS Voltage 
Controlled Oscillator for Phase Locked Loop. Current starved VCO is simple ring oscillator consisting of cascaded inverters. The proposed circuit is implemented in a 130nm CMOS technology using IHP PDK.

## Design Schematic
  - Inverter characterization
    Before designing a current starved VCO using a three stage inverter in a loop, Inverter is characterized to find the VM(swtiching threshold) and propogation delay (Tpd). W/L values of the PMOS and NMOS are choosen such that VM=VDD/2. Tpd value is calculated at a load of 10pf.  
  - VCO schematic
    Throttle transistors are used which will limit the current into the inverters. 
  - 
 
## Simulation
## Specification table
## Conclusion
## Acknowledgement
## References

