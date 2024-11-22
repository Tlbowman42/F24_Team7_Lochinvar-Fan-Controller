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
1. As of current circumstances the microcontroller does not face any known constraints.  
  
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
   - The memory and microcontroller are connected via the ST-morpho connectors on the PCB. From there traces are ran from 3 dedicated SPI pins and 1 standard GPIO pin. The three spi pins constitute the serial clock, mosi, and miso connections to the memory thus, allowing for proper clock generation and data transferral. The final GPIO pin sent to the memory allows for the EEPROM to use a chip select function for the inetgrated circuitry within the EEPROM.  

6. Ports and Buttons
   - The ports and buttons subsystem is connected to various ports on the nucleo via the PCB's onboard ST-morpho connectors. First the buttons are connected to 6 GPIO pins on the nucleo board. These IO's have no special functionaility as they are simply movement commands for the diagnostic tools menus, however these pins are configured as active low as to make analysis easier for the team. The ports subsystem is connected to the nucleo physically through a USB-A to mini USB connection. This connection allows for power and data to be driven to the microcontroller for further processing and peripheral uses.  

7. Power
   - The power subsystem is connected to the microcontroller via the PCB's St-morpho connectors. This power will be taken from the molex connection and stepped down to a usable 3.3V for the microcontroller, ensuring proper use and safety for the microcontroller. Furthermore, the microcontroller will be electrically isolated from the rest of the power circuit allowing for the utmost safety to the microcontroller and its peripherals.  

# Buildable Schematic

![image](https://github.com/user-attachments/assets/799e6c8f-e0e2-4153-ae29-1e028998ebe8)

# PCB Layout

# BOM

| Manufacteror | Manufacteror Part Number | Distributor | Distributor Part Number | Quantity | Cost  | URL  | Component Name  |
| :---         | :---:                    | :---:       | :---:                   | :---:    | :---: | :--- | :--- |
| TE Connectivity AMP connectors | 2-215307-0 | Digikey | A106399-ND | 2 | $10.68 | https://www.digikey.com/en/products/detail/te-connectivity-amp-connectors/2-215307-0/1149668 | N/A |
| STM Electronics | Nucleo-L452RE | Digikey | 497-17008-ND | 1 | $14.85 | https://www.digikey.com/en/products/detail/stmicroelectronics/NUCLEO-L452RE/6559190 | Nucleo-L452RE | 
| Total | | | | | $25.53 | |

# Analysis

I will split my analysis into three main parts.  

1. Analysis over the Reverse Polarity Protection Circuit
2. Analysis over the Flyback Converter with an Isolated Output
3. Analysis over the Diode-oring Circuit and the LDO Voltage Regulator

## Analysis over the Reverse Polarity Protection Circuit

I have shown my Ltspice circuit diagram below. The simulation is stepping through source voltages, it will step from the voltage source being +10 volts to it being +40 volts in steps of one. I am then measuring the voltage after the PFET (V_pol), and this voltage will be what is given to the flyback converter. The results of this simulation can be found in the text document labeled "Polarity Checker Error Log (Positive Voltage)", or I have also shown the transient graphs below.  

Comparing the first two graphs titled "Transient Graph for V_pol (Positive Source)" and "Transient Graph for V_pol (Negative Source)" we observe the following: 

1. When the source voltage is positive the flyback converter will be recieving the voltage given by the molex connecter. This is due to the Vgs or threshold voltage being high enough for the PMOS to be in the saturation region.
2. When the source voltage is negative the flyback converter will be recieving little to no voltage since the PFET will open due to its Vgs voltage not being high enough. The voltage that does get through is the result of leakage and because the Vgs value is hovering close enough to the threshold voltage of -2 to -4 volts for the IRF9540NPBF PMOS.

Comparing the second two graphs titled "Transient Graph for Vg - V_pol (Positive Source)" and "Transient Graph for Vg - V_pol (Negative Source)" we observe the following: 

1. The diode will clamp the Vgs voltage to around -13V when needed. The reason for this is to not violate the Vgs rating for the IRF9540NPBF PMOS which is plus or minus 20 volts.
2. If the source is negative the Vgs voltage will not be in the threshold region of -2V to -4V therefore the PMOS will be acting in the cutoff region.

Therefore this circuit helps to achieve constraint one, due to allowing for a more electrically safe circuit due to polarities not being reversed. 

***Circuit Diagram in Ltspice***

![image](https://github.com/user-attachments/assets/93e606e2-be11-4cc5-ba8d-1f1a40a96382)

***Transient Graph for V_pol (Positive Source)***

![image](https://github.com/user-attachments/assets/120dfb87-78d4-4fae-8f15-4f35389870af)

***Transient Graph for V_pol (Negative Source)***

![image](https://github.com/user-attachments/assets/c0ca110f-5fe5-4110-b4c1-413cf7daf43c)

***Transient Graph for Vg - V_pol (Positive Source)***

![image](https://github.com/user-attachments/assets/2c51b049-99f0-46af-9963-c7fdbdfeb89f)

***Transient Graph for Vg - V_pol (Negative Source)***

![image](https://github.com/user-attachments/assets/e41b66e6-d378-49e2-93ec-252ee4787c82)

## Analysis over the Flyback Converter with an Isolated Output

I am using the LM5180EVM-S05 Flyback Converter for our design. The purpose of this flyback converter is to step down our 10-40V DC source from the fan controller and output an isolated 5V DC for our diagnostic tool. The datasheet states, " The LM5180-Q1 single-output EVM is designed to use a regulated or non-regulated high-voltage input rail ranging from 10 V to 65 V to produce a tightly-regulated, isolated output voltage of 5V at load currents of 1 A(or higher depending on VIN)." [4]

![image](https://github.com/user-attachments/assets/7da3340c-f8d6-419a-9f0f-548b510badf8)



## Analysis over the Diode-oring Circuit and the LDO Voltage Regulator

# References
[1] A. Ward, “Questions for Initial Lochinvar Meeting (1) - Answered.” Lochinvar, Cookeville, Sep. 11, 2024  
[2]  “IEC 61010-2-081 - safety requirements for electrical equipment for measurement, control, and laboratory use – part 2-081: Particular requirements for automatic and semi-automatic laboratory equipment for analysis and other purposes | Engineering360,” GlobalSpec, https://standards.globalspec.com/std/13207536/IEC%2061010-2-081 (accessed Sep. 21, 2024).  
[1] “IRF9540NPBF,” Infineon Technologies, https://www.infineon.com/dgdl/irf9540npbf.pdf?fileId=5546d462533600a401535611cfa21dc8 (accessed Nov. 21, 2024).  
[4] “Ti,” Texas Instruments, https://www.ti.com/lit/ug/slvu261/slvu261.pdf?ts=1719995246833&ref_url=https%253A%252F%252Fwww.ti.com%252Fproduct%252FTPS61500%253Fbm-verify%253DAAQAAAAJ_____9MmIuL_yBQIIZ_XbUMP7Hy669m5KhAc66gboQ_qz98FypIehgkez1fwBw-DwTL1fvTIi5dUWsQAhqRgd8atqHnL9vzYwWqX5UjgEs9IuKniEUz7mniIxQyloEzs0Z4McU5-MRMCUG9NoCHWNH1QACawps0fBNVFaeMSUeU66PAmgiylHob45TdnbC89xvDUYzBTbRLkKgLp2q_CUWA0I99tiu0NDrq5wYGQhKu0aXECLj9RpgP33Z3w4ahQQ8ZbkfaYRWgso2j7mYY2WvKetO2fq8BdVfUUgzHGhVwWKfzBXQ (accessed Nov. 21, 2024).  

