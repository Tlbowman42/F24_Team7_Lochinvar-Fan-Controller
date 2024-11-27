
# Function of the Subsystem

The role of the memory subsystem is to act as the non-volatile storage for the users testing configurations and the input and output of specific crucial data logs. The memory subsystem will handle the containment and output of such settings and log files when the diagnostic tool is off and on respectively.

# Specifications and Constraints
The memory subsystem shall adhere to the following specifications and constraints:

*Specifications*
1. The memory shall have a width of a byte.  
2. The memory shall be able to communicate with the microcontroller through a serial protocol.  

*Constraints*
1. The memory subsystem must be able to store and transfer user settings, input, and output data.  

The reason for this constraint came from Lochinvar. They stated that there might be some use in being able to store user configurations and output/input data. Thus, the EEPROM memory must be able to store user configurations and data, so it can be transferred to another device.  

# Overview of Proposed Solution
The memory subsystem contains only one main part.

1. The 25AA640-I/SN	64kbit EEPROM.  

The memory subsystem will be connected to the microcontrollers ST-morpho connectors allowing for R/W functions and power via serial SPI communication and power ports. This EEPROMs purposed will be fulfilled by saving user configurations and specific input/output data logs from the user. This will allow the user to be able to have a more flexible experience by giving them the option to save their settings and data.  
  
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
   -  The memory subsystem will interface to the microcontroller via an SPI connection containing 4 IO pins. These pins have various uses with three being meant for EEPROM functions such as serial clock (SCK), serial data out (SO), and serial data in (SI). The final pin is a simple IO pin that will determine the function of the EEPROM chip select for its integrated circuits. Furthermore, the memory subsystem will receive power from the microcontroller via the ST-morpho connectors +3.3V pin, allowing for proper power distribution to the EEPROM.  

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

1. Analysis of microcontroller serial connections  
2. Uses/Functionality of the EEPROM memory  

## Analysis over the EEPROM and its connections  

The choice for communication protocol started with determining if our microcontroller would have enough GPIO's to implement a 4 wire SPI interface rather than a 2 wire I2C. Upon estimating the diagnostic tools required GPIO's, the team felt as if there would be slight trouble in implementing an SPI communication channel to an EEPROM [2]. For this reason we initially went with an I2C design as this would allow for less IO's to be used while also keeping the communication channel simple and fast. Furthermore, using I2C we would be certain of our ability to keep an entire IO channel dedicated to the LCD for faster data transfer. However, we also wanted our memory to have a full-duplex communication channel allowing for simultaneous back and forth data transfer. Due to this, the possibility of an I2C EEPROM was thrown out, as I2C channels are only half duplex. Alongside I2C not having full-duplex we were also able to pin out the microcontroller such that we could implement the faster, full-duplex communication channel that we wanted originally. Thus, we chose to go with an SPI connection to the EEPROM as it would be a faster system that allowed for simulataneous back and forth communication whilst also not interfering with other subsystems [1].  

Currently the EEPROM will serve to hold user configurations and specific input and output logs in non-volatile memory on board the diagnostic tool. Thus, allowing for the memory to meet the specifications and constraints. In order to do so the team will focus on generating log files and saving configured user profiles when applicable or requested by user. Furthermore, the team will strive to keep the data logs and user configurations in as small of data packet as possible due to the EEPROMs lack of capacity in only 64k bits. By using the EEPROM to store user configurations and input/output data from the tool, proper analysis can be done on the resulting effects of a fan simulation.  

# References
[1] “25AA640/25LC640,” 21223H.book, https://ww1.microchip.com/downloads/en/DeviceDoc/21223H.pdf (accessed Nov. 20, 2024).  
[2] “UM1724 user manual - STM32 nucleo-64 boards (MB1136),” STM32 Nucleo-64 boards (MB1136) - UM1724, https://www.st.com/resource/en/user_manual/um1724-stm32-nucleo64-boards-mb1136-stmicroelectronics.pdf (accessed Nov. 20, 2024). 
