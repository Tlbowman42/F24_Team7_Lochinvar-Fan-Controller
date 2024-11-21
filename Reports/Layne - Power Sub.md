# Function of the Subsystem

The role of the Power subsystem is to ensure stable power throughout the diagnostic tool. Specifically, this subsystem accepts power from a DC bus or USB connection, stepping the input voltage down to a manageable 3.3V DC that will power the tool's microcontroller, display, and all other components. Additionally, this subsystem will offer electrical isolation from the fan controller's Molex connection and the diagnostic tool.  

# Specifications and Constraints
The power subsystem shall adhere to the following specifications and constraints:

*Specifications*
1. The tool shall be able to be powered by both the DC power bus from the boiler's fan, which is 10 to 40 volts, and by a USB connection if a fan is not present. [1]
2. The Power shall encompass safe and proper Ports between all subsections of the project.
3. The Power shall be able to take in various DC voltage loads (24V & 5V) and adjust those voltages to usable levels (3.3V).
4. The device shall be powered by the fan DC power bus as well as by the USB connection in case no fan is connected.
5. The Power shall be placed in a design such that all I/O ports are properly mapped and subsection Ports are clear and efficient.
6. The Power shall output DC power to the display and microcontroller.
7. The Power shall ensure stable power is output to all sensitive components such as the microcontroller.
8. The Power shall have safety measures in place to deal with noise and surges.

***I may end up taking away some of these specifications depending on what the group consensus is***  

*Constraints*
1. IEC 61010-2-081: The IEC 61010 standard is for the safety requirements for electrical equipment for measurement, control and laboratory use. The specific subsection that we will need to follow is subsection 2-081. This subsection applies to automatic and semi-automatic laboratory equipment for analysis and other purposes. In other words this section pertains to equipment for measuring or modifying one or more characteristics or parameters of samples. [2]
2. The Power subsystem must incorporate electrical isolation for its output due to the presence of 'dirty power' from input sources, ensuring the reliability and protection of downstream components. 

*Justification for Constraints*  

Constraint one is applicable to the Power Subsystem due to the electrical safety concerns for equipment that is used for measurement, control, and in laboratories.  

Constraint two is applicable to the Power Subsystem due to the nature of the DC voltage supply the Fan Diagnostic Tool will be supplied by. This constraint was never written in words; however, through discussion with our customer, Lochinvar, we will need an isolated power output for our Diagnostic Tool.  

# Overview of Proposed Solution
The Power Subsystem will be comprised of a few main parts:  

1. A flyback converter with one isolated output
2. A diode-oring circuit to allow for two different sources to power the board
3. A LDO voltage regulator to step 5V DC down to 3.3V DC.
4. A reverse polarity protection circuit

First the board will be connected by Molex connection to a controller. This controller will provide 10-40V DC, at a nominal voltage of 24V DC. First the voltage will go through a reverse polarity protection circuit comprised of a PFET and clamping diode. This circuit will ensure that in the case of the Vdd and Gnd getting swapped the circuit will not be damaged.  

Second after the reverse polarity protection the voltage will be fed into a flyback converter that will have one 5V DC output that will connect to the rest of the diagnostic tool. This will fufill the second constraint of providing an isolated power supply for our diagnostic tool.  

Third the two 5V DC sources, one from a USB connection and one from the isolated output of the flyback converter, will enter into a diode-oring circuit. This circuit is set up so that the molex connection will be given priority to power the board if it is available. This will fulfill the first specification, allowing for the board to be powered by two different sources.  

Lastly after the diode-oring circuit the voltage will be inputted into an Low Drop-out Voltage Regulator to step down the voltage to 3.3V DC for the rest of the components on the board.  

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

![image](https://github.com/user-attachments/assets/5372b5e2-c959-4062-a198-a93db6a56d5c)


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
| C&K | S102031MS02Q | Mouser Electronics | 611-S1020301 | 1 | $3.50 | https://www.mouser.com/ProductDetail/CK/S102031MS02Q?qs=qUgWstB0J2PTi4u40fuqgg%3D%3D |
| Micro USB |  | Digikey |  | 1 |  |  |
| TDK Corporation | FK28X5R1A105KN000 | Digikey | 445-FK28X5R1A105K-ND | 1 | $0.36 | https://www.digikey.com/en/products/detail/tdk-corporation/FK28X5R1A105KN000/1008877 | C3 |
| TDK Corporation | FG28X7R1A225KRT06 | Digikey | 445-173582-1-ND - Cut Tape (CT) | 1 | $0.33 | https://www.digikey.com/en/products/detail/tdk-corporation/FG28X7R1A225KRT06/5803196?s=N4IgTCBcDaIGIHEwA4AaB2ASgRgIJjAFYBpTAFQAYA2EAXQF8g | C1 |
| KEMET | C322C103K3G5TA | Mouser Electronics | 80-C322C103K3G5TA | 1 | $0.51 | https://www.mouser.com/ProductDetail/KEMET/C322C103K3G5TA?qs=h3%2Fj8evtlm2CUEq59T%2FBjg%3D%3D | C2 |
| 100k Resistor |  | Digikey |  | 1 |  |  |
| Total | | | | | $147.64   | |

# Analysis

I will split my analysis into 

# References
[1] A. Ward, “Questions for Initial Lochinvar Meeting (1) - Answered.” Lochinvar, Cookeville, Sep. 11, 2024  
[2]  “IEC 61010-2-081 - safety requirements for electrical equipment for measurement, control, and laboratory use – part 2-081: Particular requirements for automatic and semi-automatic laboratory equipment for analysis and other purposes | Engineering360,” GlobalSpec, https://standards.globalspec.com/std/13207536/IEC%2061010-2-081 (accessed Sep. 21, 2024).  
