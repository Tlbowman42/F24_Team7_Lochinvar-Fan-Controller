
# Function of the Subsystem

The role of the memory subsystem is to act as the non-volatile storage for the diagnostic tools data logs and error messages. The memory subsystem will handle the containment and output of important log files when the diagnostic tool is off and on respectively.

# Specifications and Constraints
The memory subsystem shall adhere to the following specifications and constraints:

*Specifications*
1. The memory shall have a width of a byte.  
2. The memory shall be able to communicate with the microcontroller though a serial protocol  

*Constraints*
1. As of current circumstances the memory subsystem does not face any known constraints.  
  
# Overview of Proposed Solution
The memory subsystem contains only one main part.

1. The 25AA640-I/SN	64kbit EEPROM.  

The memory subsystem will be connect to the man PCB via through whole soldering points. Furthermore, the memory subsystem will be connected to the microcontrollers ST-morpho connectors allowing for R/W functions and power via serial SPI communication and power ports. This EEPROM will contain log files for the diagnostic tools data as well as error messages and further small sized information packets.
  
# Interfacing with Other Subsystems
1. Display
   - The memory subsystem does not interface with the display LCD.  

2. Case
   - The memory subsystem does not interface with the case.  

3. Pre-Processing
   - The memory subsystem does not interface with the pre-processing subsystem.   

4. Post-processing
   - The memory subsystem does not interface with the post-processing subsystem.  

5. Microcontroller
   -  The memory subsystem will interface to the microcontroller via an SPI connection containing 4 IO pins. These pins have various uses with three being meant for EEPROM functions such as serial clock (SCK), serial data out (SO), and serial data in (SI). The final pin is a simple IO pin that will determine the functin of teh EEPROMS chip select for its integrated circuits. Furthermore, the memory subsystem will recieve power from the mircocontroller via the ST-morpho connectors +3.3V pin, allowing for proper power distribution to the EEPROM.  

7. Ports and Buttons
   - The memory subsystem does not interface with the ports and buttons subsystem.  

8. Power
   - The memory subsystem does not interface with the power subsystem.   

# Buildable Schematic

![alphabet 2](https://github.com/user-attachments/assets/7303b3c5-7d4c-4509-b72c-2ce9a38cd636)

# PCB Layout

![image](https://github.com/user-attachments/assets/7716fa9d-f74b-4b8b-9dda-23448095bf58)

![image](https://github.com/user-attachments/assets/dac80311-7e87-4ce8-bed9-0c62a2ce0c5a)

# BOM

| Manufacteror | Manufacteror Part Number | Distributor | Distributor Part Number | Quantity | Cost  | URL  | Component Name  |
| :---         | :---:                    | :---:       | :---:                   | :---:    | :---: | :--- | :--- |
| Microchip Technology | 25AA640-I/SN	| Digikey | 25AA640-I/SN-ND | 1 | $0.93 | https://www.digikey.com/en/products/detail/microchip-technology/25AA640-I-SN/318777 | EEPROM Memory IC 64Kbit SPI 1 MHz 8-SOIC |
| Total | | | | | $0.93 | |

# Analysis

The memory analysis will be done in one complete part including,  

1. Analysis of micrcontroller serial connections  
2. Uses/Functionality of the EEPROM memory  

## Analysis over the EEPROM and its connections  





# References
[1] A. Ward, “Questions for Initial Lochinvar Meeting (1) - Answered.” Lochinvar, Cookeville, Sep. 11, 2024  
[2]

