# Automotive electronics system project

This repository contains the hardware design, electronic schematics, simulations, and manufacturing files for an integrated automotive control unit. The system is designed to manage power supply, drive a DC motor/pump, measure current precisely, and handle data communication, all integrated into a sealed enclosure with a dedicated I/O connector. For this project, I utilized all the simulation and design software required by the task specifications (LTSpice, TwisterSIM, ST eDesignSuite, Altium), but I additionally designed the complete PCB layout in Altium Designer.

-PCB Design & Mechanical Integration: The board was designed to fit the mechanical constraints of the aipxe-325x4b enclosure, integrating a dual-chamber ATM13-12PA-12PB-BM03 I/O connector with associated 3D models. While the baseline output was generated in Altium, the PCB layout and routing were also fully executed in Altium.

-Input Protection: I designed a protection circuit using two back-to-back P-channel MOSFETs (e.g., HAT1072) to safeguard against reverse polarity and inrush currents, validating the functionality through fast transient simulations in LTSpice.

-Power Supply Tree: The power architecture was evaluated using STMicroelectronics eDesignSuite to analyze SMPS versus LDO options. It is designed to deliver a minimum of 1.7A on the 5V line and 1A on the 3.3V line.

-DC Motor / Pump Driver: The power stage, featuring High-Side and Low-Side switches, was designed using TwisterSIM to drive an actuator with 4mH inductance and 0.3 ohms resistance at a maximum current of 7.5A.

-Current Measurement (Shunt): The implementation includes a simulated shunt measurement circuit for currents up to 15A on a 10mΩ shunt. I evaluated the performance, temperature influence, and resistor tolerance using a standard differential OpAmp (LM2904) compared against a dedicated measurement IC (INA180).

-CAN FD Interface with Wake-Up: The communication module uses an automotive CAN FD transceiver (e.g., TCAN1043) capable of shutting off all board power to maintain an idle current of <1mA. The entire circuit powers on exclusively via a specific CAN wake-up pattern, with a 32-bit microprocessor handling the general logic.
