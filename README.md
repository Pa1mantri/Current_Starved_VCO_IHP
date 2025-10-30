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

Block-diagram of VCO:

<img width="1106" height="653" alt="Image" src="https://github.com/user-attachments/assets/82057109-0639-4b07-b530-c7a562216872" />

The frequency of the Voltage Controlled Oscillator is expressed in terms of centre frquency using the formula  

fout is the output frequency of the VCO. 

fcenter (centre frequency) - The point where your circuit is designed to operate most linearly and stably.

Vcontrol is the applied control voltage.(Vctrl)

Vcenter is the control voltage corresponding to the centre frequency.


## Design Schematic

### VCO schematic
    
A ring oscillator consists of an odd number of delay stages connected in a loop, with the output of the last stage feedback to the input of the first stage. In the schematic, the middle two transistors form a  CMOS inverter, while the upper PMOS and lower NMOS transistors function as current-limiting devices. These transistors regulate the current flowing into the inverter block, effectively “starving” it of current depending on the applied control voltage Vctrl(V2).Throttle transistors(M4,M5,M8,M9,M12,M13) are used to limit the current into the inverters, making them current-starved.
    
 <img width="1003" height="691" alt="Image" src="https://github.com/user-attachments/assets/3f80084d-23aa-4de7-9b7e-b3b8bb7cdb44" />

 At the end, two inverters connected back to back to form a buffer. Transistors M15,M16,M17,M18 forms a buffer. V1 provides the Vdd and V2 is the Vctrl(control voltage).

 
## Simulation

Simulation is performed using the eSim tool

<img width="1852" height="899" alt="Image" src="https://github.com/user-attachments/assets/8ce8ccdc-a384-4f13-9891-6c0b8dc75517" />

After doing transient simulation frequency=0.9GHz


<img width="1843" height="917" alt="Image" src="https://github.com/user-attachments/assets/cbcae399-6dbf-4f2d-83ad-bb1fb92696fd" />

Output waveform at Vctrl=3v frequency of 0.97GHz

<img width="1845" height="919" alt="Image" src="https://github.com/user-attachments/assets/60fec00a-e878-4190-88ab-7aba7af57795" />

Output waveform at Vctrl=2v frequency of 565MHz

<img width="1848" height="917" alt="Image" src="https://github.com/user-attachments/assets/8b579734-0d2a-495e-9557-be1a4c501930" />

Netlist file (Spice deck) of VCO:

<img width="1846" height="890" alt="Image" src="https://github.com/user-attachments/assets/3c8dc013-00ab-4d19-90f1-713f569c630a" />


## Specification table

| Parameter                 | Symbol | Value      | Remarks                                         |
| :------------------------:| :-----:| :---------:| :-----------------------------------------------|
|Technology                 |        | 130-nm CMOS| IHP SG13G2                                      |
|Supply Voltage             |  VDD   |  3.3V      | HV(High Voltage, Thick oxide CMOS               |
|Operating Temperaure Range |  T     |   27C      | Characterized at room temperature (-40C to +125C|
|Control Voltage            | Vctrl  |  1.2V-3    | Maximum linearity observed in this range        |
|Output VCO Frequency       | Vout   | 120MHz-1GHz| Maximum frequency of 1.03GHz                    |
|Centre frequency           |  fo    |  550MHz    | @Vctrl = 2V                                     |
|Frequenct Range            |  Δ𝑓    |   1GHz     | Wide tuning range                               |
|VCO gain                   | KVCO   |   496MHz/V | Linear in 1.2-3V range                          | 
|Power consumption          |  Pavg  | 1.65mW     | At VDD=3.3V, Vctrl=2.0V                         |


<img width="1080" height="720" alt="Image" src="https://github.com/user-attachments/assets/99678a61-f0d3-4649-b474-21e081c1dc96" />

R² value determines the linearity. R²=1 means perfectly linear relation. In the graph above R² = 0.983 (all data) R² = 0.988 (for 1.2 V – 3.0 V range). That means output frequency changes almost linearly with control voltage over usable tuning range. This linearty is a prerequisite for the VCO to be used in a PLL.

KVCO is the gain of the oscillator. For every +1 V increase in Vctrl, the oscillation frequency increases by ≈ 0.5 GHz (496 MHz). That's the sensitivity of the oscillator.

## Inverter characterization 

Before designing a current starved VCO using a three stage inverter in a loop, Inverter is characterized to find the VM(swtiching threshold) and propogation delay (Tpd). W/L values of the PMOS and NMOS are choosen such that VM=VDD/2. Tpd value is calculated at a load of 10pf.
    
    Inverter schematic in eSim tool
    
<img width="1849" height="867" alt="Image" src="https://github.com/user-attachments/assets/0cf3d9dd-2cd0-4c06-a148-39fb5271b829" />

Inverter netlist file 

<img width="1846" height="892" alt="Image" src="https://github.com/user-attachments/assets/f89e92ab-1a66-4059-b9f4-308172c417ca" />

    Propagation delay with a load of 10pf is 50.5Ps at Wp=3.7Wn
    
<img width="1843" height="614" alt="Image" src="https://github.com/user-attachments/assets/bf3df52d-636c-4588-be8d-a4c7cca8b99e" />

    Vm = VDD/2 =1.65V at Wp=3.7Wn
    
<img width="1852" height="870" alt="Image" src="https://github.com/user-attachments/assets/f87083a9-bc1c-40ab-90bb-afd2fcbf0acf" />


## Conclusion

 In this work, a VCO with enhanced frequency performance is presented. The circuit achieves a maximum frequency of 1 GHz while consuming only 1.65 mW of power from a 3.3 V DC supply. The center oscillation frequency, currently 550 MHz, is primarily influenced by transistor sizing. These results highlight the potential of the proposed VCO design for integration into phase-locked loops (PLLs) requiring energy efficiency and a wide tuning range.  Future integration of this VCO with a charge pump and loop filter will complete the PLL design, enabling closed-loop verification of locking behavior and overall system stability.
 
## Acknowledgement

1. eSim,fossee team,IITB
2. Sumanto kar, Assistant Project Manager, FOSSEE, IITB.

## References

 1. B. Razavi, Design of Analog CMOS Integrated Circuits, 3rd ed. New York, NY, USA: McGraw-Hill, 2016.
 2. A. R. Patil, "Design of Current Starved VCO Using SkyWater 130 nm PDK," International Research Journal of Engineering and Technology (IRJET), vol. 5, no. 3, pp. 1231–1234, Mar. 2018. [Online]. Available:
 https://www.irjet.net/archives/V5/i3/IRJET-V5I3191.pdf
 3. eSim User Manual, FOSSEE, IIT Bombay. [Online]. Available: https://esim.fossee.in/documentation






