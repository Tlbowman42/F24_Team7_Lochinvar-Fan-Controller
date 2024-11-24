# Function of the Subsystem

The role of the microcontroller subsystem is to act as the brain and heart of the diagnostic tool. The microcontroller will handle all of the data processing and signal modulation within the diagnostic tool. Alongside signal processing the microcontroller will handle all of the user inputs and data being sent to the LCD and EEPROM respectively.  

# Specifications and Constraints
The microcontroller subsystem shall adhere to the following specifications and constraints:

*Specifications*
1. The microcontroller shall be able to take in and output both PWM and tachometer signals.  
2. The microcontroller shall be able to communicate to the display to update what is being displayed.  
3. The microcontroller shall be able to review user inputs through the form of push buttons to change selected parameters and/or change what is being displayed 4 when necessary.  
4. The microcontroller shall be able to clean and replicate the signals used in the software pass-through mode. (Hardware Specifications and not Software Specifications.)  

*Constraints*
1. The microcontroller must be able to take in both PWM/Tach signals at the same time whilst being able to clean and replicate the same signas on the PWM and Tach output ports.

*Justification for Constraints*  

Constraint one is applicable to the microcontroller due to the required fan pass through mode where the diagnostic tool must take in and output PWM and Tach signals at the same time after cleaning the input signals up. This constraint puts pressure on the microcontroller timer channels and requires proper IO pinouts in order to complete the signal pass through mode specified by Lochinvar.  
  
# Overview of Proposed Solution
The microcontroller subsystem consists of only two main parts.

1. The Nucleo-L452RE development board.  
2. The ST-morpho connectors on the PCB of the diagnostic tool.  

Firstly, the nucleo board will be connected to the main PCB via the CN7 and CN10 ST-morpho connectors on the nucleo board. Once bridged onto the main PCB, traces will take various IO's and other pins to different areas for their seperate processes. Connections to the memory, lcd, buttons, power, post, and pre processing subsystems will all be estalished in this step.  
  
Currently 36 GPIO pins have been used or mapped out for possible integration on further projects. The first four pins were given to the post and pre processing subsystems as these systems needed the most specialized pins. The chosen 4 pins allow for the most optimized signal intake and outputting allwoing for the fastest and clearrest signal processing when in the monitoring or subsequent modes.  
  
The second most important subsystem was deemed as the LCD, to said LCD 11 GPIO pins were used. These pins have been assigned as output IO's and of the 11 pins 8 were used for a parallel connection to ensure stable and fast data transfer to the screen. The subsequent three pins were used for various functions on the LCD such as register select, enable, and W/R select. The gpios were selected based off of their lack of specialty functions and their locations al being on a singular channel, PBx.  
  
The subsystem deemed third most important was the memory subsystem. This subsystem required specialized SPI pins as the selected EEPROM uses SPI communication for data transfer. Due to this we chose to give the memory 3 specialized pins in the SCK, MOSI, MISO, and a single IO pin for the onboard chip select.  
  
Finally, the other used pins were mapped out as not connected (NC), USART communication, I2C communication, or simple GPIO inputs for the 6 buttons the user can interact with. The USART and I2C communications were pinned out but not used as there is no need for these communication channels as of right now, but they may be used in the future. Furthermore, the GPIO input pins were configured as pull down buttons as to add to the simplicity of the circuit design. These IO buttons were deemed as the least important as they only serve to get user input in the form of up, down, left, right, ok, and back for the menus used.  
  
# Interfacing with Other Subsystems
1. Display
   - The display subsystem will take 11 pins of input from the microcontroller and ST-morpho connectors at all times. The first 8 account for DB0-DB7 also known as the data bus pins sent to the display and all reside on the same channel for added speed. The subsequent three pins left are used for the R/W select, enable, and register select functions.  

2. Case
   - The microcontroller subsystem does not interface with the case.  

3. Pre-Processing
   - The pre-processing subsystem is connected to the microcontoller through the on board ST-morpho connectors. Due to the pre-processing subsystem taking in both Tach and PWM input signals, two specialized pins were given to this subsystem. Both pins have on board timers allowing for the cleanest and fastest replication and processing of input signals.  

4. Post-processing
   - The post processing subsystem is connected to the nucleo board via the onboard ST-morpho connectors. Much like the pre-processing subsystem, the post requires specialized timer pins in order to output clear and correct PWM and Tach signals. Due to this two specialized pins were given to the post processing with both IO's being specialized for PWM and Tach out signals.  

5. Memory
   - The memory and microcontroller are connected via the ST-morpho connectors on the PCB. From there traces are ran from 3 dedicated SPI pins and 1 standard GPIO pin. The three spi pins constitute the serial clock, mosi, and miso connections to the memory thus, allowing for proper clock generation and data transferral. The final GPIO pin sent to the memory allows for the EEPROM to use a chip select function for the inetgrated circuitry within the EEPROM. Furthermore, outside of specialized IO pins, the microcontroller will handle powering the EEPROM by passing it a 3.3V power from its own +3.3V pin.

6. Ports and Buttons
   - The ports and buttons subsystem is connected to various ports on the nucleo via the PCB's onboard ST-morpho connectors. First the buttons are connected to 6 GPIO pins on the nucleo board. These IO's have no special functionaility as they are simply movement commands for the diagnostic tools menus, however these pins are configured as active low as to make analysis easier for the team. The ports subsystem is connected to the nucleo physically through a USB-A to mini USB connection. This connection allows for power and data to be driven to the microcontroller for further processing and peripheral uses.  

7. Power
   - The power subsystem is connected to the microcontroller via the PCB's St-morpho connectors. This power will be taken from the molex connection and stepped down to a usable 3.3V for the microcontroller, ensuring proper use and safety for the microcontroller. Furthermore, the microcontroller will be electrically isolated from the rest of the power circuit allowing for the utmost safety to the microcontroller and its peripherals.  

# Buildable Schematic

![alphabet](https://github.com/user-attachments/assets/fb824be5-3427-47e1-886e-de183852b5f9)

![Capstone pinout](https://github.com/user-attachments/assets/ac7318b6-d384-4e06-8a9a-fc43d43533bb)

# PCB Layout  

![image](https://github.com/user-attachments/assets/849807e7-b4b8-4666-b9a1-199ce473185d)

![image](https://github.com/user-attachments/assets/0314ce70-081b-4594-97d4-b031bf1be61e)

# Operational Flowchart  

Due to the microcontrollers software being primarily behind the scenes the flowchart is primarily composed of the necessary functions to take in and modulate the PWM and Tach signals.  


# BOM

| Manufacteror | Manufacteror Part Number | Distributor | Distributor Part Number | Quantity | Cost  | URL  | Component Name  |
| :---         | :---:                    | :---:       | :---:                   | :---:    | :---: | :--- | :--- |
| TE Connectivity AMP connectors | 2-215307-0 | Digikey | A106399-ND | 2 | $10.68 | https://www.digikey.com/en/products/detail/te-connectivity-amp-connectors/2-215307-0/1149668 | N/A |
| STM Electronics | Nucleo-L452RE | Digikey | 497-17008-ND | 1 | $14.85 | https://www.digikey.com/en/products/detail/stmicroelectronics/NUCLEO-L452RE/6559190 | Nucleo-L452RE | 
| Total | | | | | $25.53 | |

# Analysis

My analysis will be encapsulated in one large complete analysis.  

## Analysis of the microcontroller and ST-morpho connections
Analysis of the microcontroller subsystem begins with our choice for microcontrollers. The choice began with two major considerations, those being availability of the microcontroller and functionality of the pins. Availability was quickly determined based on the prior use of STM32 products and advice from our capstone advisor. Furthermore, with continuous advising we landed at the need for a development board that felt like something we had worked with previously. Thus, we bagan looking into the STM32 family of chips and development boards, with careful consideration we chose to use the STM32L family of chips. This selecton was made because of the low power functionaility of the chip and eventually led us to the Nucleo-L452RE board. Bringing this to our advisor we were made aware of our advisors OS he had created and how portable it was to the nucleo board.  

After determining the availability of the nucleo board the team moved to assessing the functionality and use of the board and its peripherals. First we calculated the determined of pins we would need compared to the amount that we had on board. With further examination we determined that the board had enough pins thus, we moved to the functionality of the pins and peripherals of the board. Beginning with the PWM and Tach signals we were able to determine that the board had both dedicated channels for PWM out as well as enough timers for all the needed signals. Next we assessed the possibility of I2C and SPI connectivity and determined that we had the choice for either on board. All of these considerations combined allowed for us to choose our other subsequent subsystems with ease as we had open availability for almost any communication protocol or IO function. 

# References


