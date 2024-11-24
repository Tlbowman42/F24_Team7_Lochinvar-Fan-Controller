
# Function of the Subsystem

The role of the memory subsystem is to act as the non-volatile storage for the users testing configurations and the input and output of specific crucial data logs. The memory subsystem will handle the containment and output of such settings and log files when the diagnostic tool is off and on respectively.

# Specifications and Constraints
The memory subsystem shall adhere to the following specifications and constraints:

*Specifications*
1. The memory shall have a width of a byte.  
2. The memory shall be able to communicate with the microcontroller though a serial protocol  

*Constraints*
1. The memory subsystem must be able to store and transfer user settings, input, and output data.  

The reasons for this constraint come from suggestions directly from Lochinvar. Lochinvar stated that there might be some use in being able to store user configurations and output/input data so returning to a project or saving an erronious output was much easier. Thus, the EEPROM memory must be able to store and transfer user configurations and data both to the microcontroller and connected PC's.  

# Overview of Proposed Solution
The memory subsystem contains only one main part.

1. The 25AA640-I/SN	64kbit EEPROM.  

The memory subsystem will be connect to the man PCB via through whole soldering points. Furthermore, the memory subsystem will be connected to the microcontrollers ST-morpho connectors allowing for R/W functions and power via serial SPI communication and power ports. Thsi EEPROMs purposed will be fulfilled by saving user configurations and specific input/output data logs from the user. This way ease of retesting a certain enviroment or set of configurations is made much faster while also allowing for data to be pulled from the board for further analysis.
  
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
   -  The memory subsystem will interface to the microcontroller via an SPI connection containing 4 IO pins. These pins have various uses with three being meant for EEPROM functions such as serial clock (SCK), serial data out (SO), and serial data in (SI). The final pin is a simple IO pin that will determine the function of teh EEPROMS chip select for its integrated circuits. Furthermore, the memory subsystem will recieve power from the mircocontroller via the ST-morpho connectors +3.3V pin, allowing for proper power distribution to the EEPROM.  

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

The choice for communication protocol started with determining if our microcontroller would have enough GPIO's to implement a 4 wire SPI interface rather than a 2 wire I2C. Upon estimating the diagnostic tools required GPIO's, the team felt as if there would be slight trouble in implementing an SPI communication channel to an EEPROM. For this reason we initially went with an I2C design as this would allow for less IO's to be used while also keeping the communication channel simple and fast. Furthermore, using I2C we would be certain of our ability to keep an entire IO channel dedicated to the LCD for faster data transferal. However, we also wanted our memory to have a full-duplex communication channel allowing for simultanious back and forth data transfer. Due to this the possibilty of an I2C EEPROM was thrown out as I2C channels are only hald duplex. Alongside I2C not having full-duplex we were also able to pin out the microcontroller such that we could implement the faster, full-duplex communication channel that we wanted originally. Thus, we chose to go with an SPI connection to the EEPROM as it would be a faster system that allowed for simulatanious back anf forth communication whilst also not interfering with other subsystems.  

Currently the EEPROM will serve to hold user configurations and specific input and output logs in non-volatile memory on board the diagnostic tool. This was decided as the use for the EEPROM based on a suggestion for this exact mode from Lochinvar. Implementing this would allow users to hold certain testing configurations and important or erronious data logs on board the diagnostic tool to later be used or transferred to a computer for analysis. In doing so the user would have a much faster and easier time returning to a project that they had been previously working on while also being able to port these configurations or logs off the tool and into external storage. Furthermore, the team will strive to keep the data logs and user configurations in as small of data packet as possible due to the EEPROMs lack of capacity in only 64k bits.  

# References

