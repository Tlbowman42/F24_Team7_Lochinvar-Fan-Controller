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
1. Microcontroller
   - The Microcontroller subsystem will receive an input power signal from the Power subsystem. The voltage will initially come from a Molex connection from the boiler controller or to from the USB. This will either be 24V DC or 5V DC respectively. The Power subsystem will then step down the voltage to a useable 3.3V for the microcontroller. It will additionally provide electrical isolation between the USB and Molex connector through the use of an opto-isolator. Therefore the Power subsystem will be outputting a 3.3V DC power signal.

2. Display
   - The Display subsystem will also receive the same 3.3V DC power signal the microcontroller subsystem receives from the Power subsystem. Therefore this signal will also be electrically isolated from any power surges. Finally, the Power subsystem will be outputting a 3.3V DC power signal.

3. Case
   - The Case and Power subsystems are not connected.

4. Pre-Processing
   - The Pre-Processing will recieve the same 3.3V DC power signal the microcontroller subsystem receives from the Power subsystem. Therefore this signal will also be electrically isolated from any power surges. Finally, the Power subsystem will be outputting a 3.3V DC power signal. ***The Pre-Processing may need to be updated due to the current design of the optocouplers pulling up to 3.3 and 24V***  

5. Post-processing
   - The Post-Processing will recieve the same 3.3V DC power signal the microcontroller subsystem receives from the Power subsystem. Therefore this signal will also be electrically isolated from any power surges. Finally, the Power subsystem will be outputting a 3.3V DC power signal. ***The Post-Processing may need to be updated due to the current design of the optocouplers pulling up to 3.3 and 24V***  

6. Memory
   - The Memory and Power subsystems are not connected.

7. Ports and Buttons
   - The Ports and Buttons subsystem is directly connected to the Power subsystem. Specifically the Molex and USB Ports providing the 24V DC and 5V DC needed to power the tool. Therefore the Ports and Buttons subsystem will be outputting the DC power signals to the Power Subsystem, in other words the DC voltage will be an input to the Power subsystem.

# Buildable Schematic

![image](https://github.com/user-attachments/assets/799e6c8f-e0e2-4153-ae29-1e028998ebe8)

# PCB Layout

# BOM

| Manufacteror | Manufacteror Part Number | Distributor | Distributor Part Number | Quantity | Cost  | URL  | Component Name  |
| :---         | :---:                    | :---:       | :---:                   | :---:    | :---: | :--- | :--- |
| Texas Instruments | LM5180EVM-S05 | Digikey | 296-LM5180EVM-S05-ND | 1 | $118.80 | https://www.digikey.com/en/products/detail/texas-instruments/LM5180EVM-S05/10434463 | N/A |
| Texas Instruments | TPS79633DCQR | Digikey | 296-13766-1-ND - Cut Tape (CT) | 1 | $2.92 | https://www.digikey.com/en/products/detail/texas-instruments/TPS79633DCQR/509964 | U2 |
| Infineon Technologies | IRF9540NPBF | Digikey | IRF9540NPBF-ND | 1 | $1.99 | https://www.digikey.com/en/products/detail/infineon-technologies/IRF9540NPBF/812088?utm_adgroup=SKU&utm_source=bing&utm_medium=cpc&utm_campaign=EN_Supplier_Infineon&utm_term=irf9540npbf&utm_content=SKU&utm_id=bi_cmp-274565063_adg-1311717702316159_ad-81982426159089_kwd-81982547982542:loc-190_dev-c_ext-_prd-&msclkid=84791e75f0e21e813ab1794f7705a4d1 | Q1 |
| Molex | 39-30-3058 | Mouser Electronics | 538-39-30-3058 | 2 | $2.84 | https://www.mouser.com/ProductDetail/Molex/39-30-3058?qs=404muyNbhLG7BJxtPMLWWg%3D%3D | J1 and J2 |
| TE Connectivity AMP Connectors | 2-215307-0 | Digikey | A106399-ND | 2 | $5.34 | https://www.digikey.com/en/products/detail/te-connectivity-amp-connectors/2-215307-0/1149668 | J3 and J4 |
| Würth Elektronik | 691137710002 | Digikey | 732-10955-ND | 2 | $0.40 | https://www.digikey.com/en/products/detail/w%C3%BCrth-elektronik/691137710002/6644051 | J5 and J6 |
| Onsemi | MBRS410LT3G | Mouser Electronics | 863-MBRS410LT3G | 1 | $1.81 | https://www.mouser.com/ProductDetail/onsemi/MBRS410LT3G?qs=3JMERSakebpTz7AxvU6YQw%3D%3D | D1 |
| Onsemi / Fairchild | 1N4743A | Mouser Electronics | 512-1N4743A | 1 | $0.16 | https://www.mouser.com/ProductDetail/onsemi-Fairchild/1N4743A?qs=SSucg2PyLi6p0vxmcuBOaA%3D%3D | D2 |
| Diotec Semiconductor | 1N4007 | Digikey | 4878-1N4007CT-ND - Cut Tape (CT) | 1 | $0.10 | https://www.digikey.com/en/products/detail/diotec-semiconductor/1N4007/18833652 | D3 |
| C&K | S102031MS02Q | Mouser Electronics | 611-S1020301 | 1 | $3.50 | https://www.mouser.com/ProductDetail/CK/S102031MS02Q?qs=qUgWstB0J2PTi4u40fuqgg%3D%3D | N/A |
| Micro USB |  | Digikey |  | 1 |  |  |
| TDK Corporation | FK28X5R1A105KN000 | Digikey | 445-FK28X5R1A105K-ND | 1 | $0.36 | https://www.digikey.com/en/products/detail/tdk-corporation/FK28X5R1A105KN000/1008877 | C3 |
| TDK Corporation | FG28X7R1A225KRT06 | Digikey | 445-173582-1-ND - Cut Tape (CT) | 1 | $0.33 | https://www.digikey.com/en/products/detail/tdk-corporation/FG28X7R1A225KRT06/5803196?s=N4IgTCBcDaIGIHEwA4AaB2ASgRgIJjAFYBpTAFQAYA2EAXQF8g | C1 |
| KEMET | C322C103K3G5TA | Mouser Electronics | 80-C322C103K3G5TA | 1 | $0.51 | https://www.mouser.com/ProductDetail/KEMET/C322C103K3G5TA?qs=h3%2Fj8evtlm2CUEq59T%2FBjg%3D%3D | C2 |
| Stackpole Electronics Inc | RSMF1FT10K0 | Digikey | 738-RSMF1FT10K0CT-ND - Cut Tape (CT) | S0.26 | 1 | https://www.digikey.com/en/products/detail/stackpole-electronics-inc/RSMF1FT10K0/1686586 | R1 |
| Total | | | | | $147.64   | |

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

