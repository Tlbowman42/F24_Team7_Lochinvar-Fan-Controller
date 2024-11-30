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

*Constraints*
1. IEC 61010-2-081: The IEC 61010 standard is for the safety requirements for electrical equipment for measurement, control and laboratory use. The specific subsection that we will need to follow is subsection 2-081. This subsection applies to automatic and semi-automatic laboratory equipment for analysis and other purposes. In other words this section pertains to equipment for measuring or modifying one or more characteristics or parameters of samples. [2]
2. The Power subsystem must incorporate electrical isolation for its output due to the presence of 'dirty power' from input sources, ensuring the reliability and protection of downstream components. 

*Justification for Constraints*  

Constraint one is applicable to the Power Subsystem due to the electrical safety concerns for equipment that is used for measurement, control, and in laboratories.  

Constraint two applies to the Power Subsystem due to the nature of the DC voltage supply the Fan Diagnostic Tool will be supplied by. This constraint was never written in words; however, after discussing it with our customer, Lochinvar, we will need an isolated power output for our Diagnostic Tool.   

# Overview of Proposed Solution
The Power Subsystem will be comprised of a few main parts:  

1. A flyback converter with one isolated output
2. A diode-oring circuit to allow for two different sources to power the board
3. An LDO voltage regulator to step 5V DC down to 3.3V DC.
4. A reverse polarity protection circuit

First, the board will be connected by Molex connection to a controller. This controller will provide 10-40V DC, at a nominal voltage of 24V DC. First, the voltage will go through a reverse polarity protection circuit comprised of a PFET and a clamping diode. This circuit will ensure that in the case of the Vdd and Gnd getting swapped the circuit will not be damaged.  

Second, after the reverse polarity protection, the voltage will be fed into a flyback converter that will have one 5V DC output that will connect to the rest of the diagnostic tool. This will fulfill the second constraint of providing an isolated power supply for our diagnostic tool.  

Third the two 5V DC sources, one from a USB connection and one from the isolated output of the flyback converter, will enter into a diode-oring circuit. This circuit is set up so that the Molex connection will be given priority to power the board if it is available. This will fulfill the first specification, allowing for the board to be powered by two different sources.  

Lastly, after the diode-oring circuit, the voltage will be inputted into a Low Drop-Out Voltage Regulator to step down the voltage to 3.3V DC for the rest of the components on the board.  

# Interfacing with Other Subsystems
1. Microcontroller
   - The Microcontroller subsystem will receive an input power signal from the Power subsystem. The voltage will initially come from a Molex connection from the boiler controller or the USB. This will either be 24V DC or 5V DC respectively. The Power subsystem will then step down the voltage to a usable 3.3V for the microcontroller. It will additionally provide electrical isolation between the USB and Molex connector through the use of an opto-isolator. Therefore, the Power subsystem will be outputting a 3.3V DC power signal.

2. Display
   - The Display subsystem will also receive the same 3.3V DC power signal the microcontroller subsystem receives from the Power subsystem. Therefore, this signal will also be electrically isolated from any power surges. Finally, the Power subsystem will be outputting a 3.3V DC power signal.

3. Case
   - The Case and Power Subsystem are not connected with signals. They are connected through needing to allow slots for the flyback converter and the Molex connections to bring power in.

4. Pre-Processing
   - The Pre-Processing will receive the same 3.3V DC power signal the microcontroller subsystem receives from the Power subsystem. Therefore, this signal will also be electrically isolated from any power surges. Finally, the Power subsystem will be outputting a 3.3V DC power signal.  

5. Post-processing
   - The Post-Processing will be connected to the 24V DC power signal from the Molex's Vin terminal. This signal will not be electrically isolated from power surges due to its design; however, the optocoupler is electrically isolated from the Molex's power from the rest of the circuit. Finally, the Power subsystem will be outputting a 3.3V DC power signal. 

6. Memory
   - The Memory subsystem will also receive the same 3.3V DC power signal the microcontroller subsystem receives from the Power subsystem. Therefore, this signal will also be electrically isolated from any power surges. Finally, the Power subsystem will be outputting a 3.3V DC power signal.

7. Ports and Buttons
   - The Ports and Buttons subsystem is directly connected to the Power subsystem. Specifically, the Molex and USB Ports provide the 24V DC and 5V DC needed to power the tool. Therefore, the Ports and Buttons subsystem will be outputting the DC power signals to the Power Subsystem, in other words, the DC voltage will be an input to the Power subsystem.

# Buildable Schematic

![image](https://github.com/user-attachments/assets/799e6c8f-e0e2-4153-ae29-1e028998ebe8)

# PCB Layout

![image](https://github.com/user-attachments/assets/a5741e4c-52d9-4d9b-85f0-4c882c560005)

![image](https://github.com/user-attachments/assets/5a6e39ef-8f56-4d20-a397-60724bc26a80)

# BOM

| Manufacteror | Manufacterrr Part Number | Distributor | Distributor Part Number | Quantity | Cost  | URL  | Component Name  |
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
| TDK Corporation | FK28X5R1A105KN000 | Digikey | 445-FK28X5R1A105K-ND | 1 | $0.36 | https://www.digikey.com/en/products/detail/tdk-corporation/FK28X5R1A105KN000/1008877 | C3 |
| TDK Corporation | FG28X7R1A225KRT06 | Digikey | 445-173582-1-ND - Cut Tape (CT) | 1 | $0.33 | https://www.digikey.com/en/products/detail/tdk-corporation/FG28X7R1A225KRT06/5803196?s=N4IgTCBcDaIGIHEwA4AaB2ASgRgIJjAFYBpTAFQAYA2EAXQF8g | C1 |
| KEMET | C322C103K3G5TA | Mouser Electronics | 80-C322C103K3G5TA | 1 | $0.51 | https://www.mouser.com/ProductDetail/KEMET/C322C103K3G5TA?qs=h3%2Fj8evtlm2CUEq59T%2FBjg%3D%3D | C2 |
| Stackpole Electronics Inc | RSMF1FT10K0 | Digikey | 738-RSMF1FT10K0CT-ND - Cut Tape (CT) | 1 | S0.26 | https://www.digikey.com/en/products/detail/stackpole-electronics-inc/RSMF1FT10K0/1686586 | R1 |
| JLCPCB | N/A | N/A | N/A | 5 | $16.60 | https://cart.jlcpcb.com/quote?rand=0.22722900529384749 | N/A |
| Total | | | | | $164.50   | |

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

***Reverse Polarity Protection Circuit Diagram in Ltspice***

![image](https://github.com/user-attachments/assets/c9acf289-bb04-4b74-a05f-86253ec2bb07)

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

As shown in the image below, the Vin can be from 10V to 65V with a nominal voltage of 24V, which also aligns with the nominal voltage of the controller voltage that we will be provided. This voltage will then be stepped down to 4.95V to 5.1V with a nominal voltage of 5.025V. I have also shown the Kicad schematic downloaded from Texas Instruments website for reference. [5]  

***LM5180EVM-S05 User's Guide***

![image](https://github.com/user-attachments/assets/7da3340c-f8d6-419a-9f0f-548b510badf8)

***Kicad Schematic of the LM5180EVM-S05 board from Texas Instruments***

![image](https://github.com/user-attachments/assets/1d33beff-ed7e-4b84-bdc2-cee85cc021db)

The flyback converter shown above will also achieve constraint 1. By allowing our diagnostic tool to be electrically isolated from the "dirty" power supply.  

## Analysis over the Diode-oring Circuit and the LDO Voltage Regulator

Since our design should incorporate being powered by two different sources, I chose a diode-oring circuit. The circuit is comprised of the 5.025 nominal DC voltage from the flyback converter, a Schottky diode, a standard diode, and the 5V DC coming from the USB. As shown below in the circuit diagram the flyback converter is connected to the anode end of the Schottky diode, and the USB 5V is connected to the anode of the standard diode. Then the two cathodes are connected. In this connection, the diode-oring circuit will output the highest voltage on the cathode end. The reason one diode is a Schottky diode and the other is a standard diode lies in their foward voltage drops. The Schottky diode has a forward voltage of approximately 0.3V and this will ensure the flyback converter (5.025V nominal) takes priority when both power supplies are connected. [6] The standard diode has a voltage drop of approximately 0.7V, this helps to ensure the USB voltage (5V nominal) will only power the board if the flyback converter is unavailable. [7] This configuartion ensures that the Molex connection (coming out of the flyback converter) will have the priority to power the board. If the Molex connection is not available then the USB 5V will be higher and therefore power the board. 

Next, the output of the diode-oring circuit is then inputted into the TPS79633DCQR LDO Voltage Regulator. As shown on the datasheet the Vin value for the TPS79633DCQR LDO is from 2.7 to 5.5 volts. In the case the Molex connector is chosen by the diode circuit the Vin would be approximately 4.7V and if the USB connection is chosen the Vin is approximately 4.3V. Therefore, the Vin parameter should not be violated. Additionally, the TPS79633DCQR model is specifically designed to output 3.3V at 1A max. The LDO circuit will need to output voltage and current to the following components: four opto-couplers (2 for Pre-Processing, 2 for Post-Processing), the microcontroller, the display, six buttons, and the EEPROM. The opto-couplers will need 50mA max during operation, therefore 200mA max will need to be allocated for the Pre-Processing and Post-Processing subsystems. [8] The nucleo-board that houses the microcontroller will need max 300mA if it is being powered by USB power. This can also go down to 100mA max depending on if the JP1 jumper is set to "On". [9] To be conservative we will allocate 300mA max for the nucleo-board and microcontroller subsystem. The display will need a max operating current of 2.5mA, with a max backlight current of 180mA. [10] Therefore the display will be allocated 182.5mA of current. The buttons are simply pulling up to the 3.3V, and will not draw any current since these are mechanical switches relying on force to activate them. The EEPROM will need 5mA max in write mode and 5mA max in read mode. [11] Therefore the Memory subsystem will be allocated 10mA of current. Therefore the total max current drawn will be approximately 700mA, and the chosen LDO can output 1A max, so the design should be able to provide enough current for the device to run at max values. [12]

***Diode-oring with LDO Voltage Regulator Circuit Diagram in Ltspice***

![image](https://github.com/user-attachments/assets/7bea0a73-2286-4cbd-8a55-7e614296ffb3)

***Transient Graph for Vout (Both Sources Connected)***

![image](https://github.com/user-attachments/assets/08569702-9d76-4118-b2b6-773877ce32f6)

***Transient Graph for Vout (Only Molex Connected)***

![image](https://github.com/user-attachments/assets/fa2fa99f-8bc8-470f-b301-63e2a1bbc997)

***Transient Graph for Vout (Only USB Connected)***

![image](https://github.com/user-attachments/assets/c1ab5732-d870-4444-9bd8-54b407603398)

***TPS79633DCQR Data Sheet***

![image](https://github.com/user-attachments/assets/f246cfa1-831e-49d3-baef-85470b1604a9)

The diode-oring circuit will allow us to power the board through two different sources. It will also give us a managable 3.3V for our smaller components to run off.  

## Current Capacity and Power Dissipation Analysis

The LDO circuit will need to output voltage and current to the following components: four opto-couplers (2 for Pre-Processing, 2 for Post-Processing), the microcontroller, the display, six buttons, and the EEPROM. The opto-couplers will need 50mA max during operation, therefore 200mA max will need to be allocated for the Pre-Processing and Post-Processing subsystems. [8] The nucleo-board that houses the microcontroller will need max 300mA if it is being powered by USB power. This can also go down to 100mA max depending on if the JP1 jumper is set to "On". [9] To be conservative we will allocate 300mA max for the nucleo-board and microcontroller subsystem. The display will need a max operating current of 2.5mA, with a max backlight current of 180mA. [10] Therefore the display will be allocated 182.5mA of current. The buttons are simply pulling up to the 3.3V, and will not draw any current since these are mechanical switches relying on force to activate them. The EEPROM will need 5mA max in write mode and 5mA max in read mode. [11] Therefore the Memory subsystem will be allocated 10mA of current. Therefore the total max current drawn will be approximately 700mA, and the chosen LDO can output 1A max, so the design should be able to provide enough current for the device to run at max values. [12]

For power dissipation we will look at the following components: the Schottky diode of the diode-oring circuit, the standard diode of the diode-oring circuit, the TPS79633DCQR LDO Voltage regulator, the IRF9540NPBF power mosfet, the 1N4743A zener diode for the polarity checking circuit, and the current limiting resistor in the polarity checking circuit.  

The Schottky diode does not have a max power dissaption listed; however, we can estimate the power dissipation. The max current it can handle is 4A, and the max current that can be outputted by the flyback converter is 1A. Therefore we will use 1A max that the Schottky diode will see. The power dissipated through a Schottky diode can be found using the following formula P = Vf * If, where Vf is the forward voltage and the If is the foward current. The power dissipated would be P = 0.3 * 1 = 0.3W. We will now use that power dissipated in the junction temperature calculation to ensure the diode does not overheat. The following calculation for the junction temperature will be used: Tj = Ta + (P x Roja), where Tj is the junction temperature, Ta is the ambient temperature, P is the power dissipated, and Roja is the thermal resistance. We will esitmate the thermal resistance is about 59 degrees celsuis since the pad size on the PCB is ~1 in. [6] We will also assume an ambient temperature of 25 degrees celsuis (77 degrees fahrenheit). Therefore the junction temperature will be 42.7 degrees celsuis which is well below the maximum junction temperature of 125 degrees celsuis. [6] Therefore the Schottky diode will preform as expected.  

The standard diode has a max power dissipation of 1W. The power dissipated will use the same equation as the Schottky diode. P = Vf * If. The forward voltage is ~0.7V at 300mA (The max current the USB can output to external connections to the nucleo-board). [7] [9] Therefore the power dissipated would be 210mW which is well below the 1W max.  

The TPS79633DCQR LDO Voltage regulator does not have a listed max power dissipation; however, we will need it to calculate the thermal limitations. The power dissipation can be calculated by P = (Vin - Vout) x Iout. If the Molex power supply is selected from the diode-oring circuit then the power dissipated will be P = (4.7 - 3.3) x 1 = 1.4W. If the USB power supply is selected from the diode-oring circuit then the power dissipated will be P = (4.3 - 3.3) x 1 = 1W. We will use the largest power dissipated for our calculations to be conservative. The junction temperature can be calculated by the same equation as the Schottky diode, Tj = Ta + (P x Roja). We will use the same ambient temperature assumption of 25 degrees celsuis, and the Roja value will be 70.4 degrees celsuis. [12] Therefore the junction temperature will be 123.56 degrees celsuis. Because of this we will need to provide adequate thermal management to ensure it does not overheat.  

The IRF9540NPBF power mosfet can dissipate 140W. Therefore with the max voltage of 40V and assuming the current of 10A. the Power dissipated will be P = Id^2 x Rdson, where Id is 10A and Rdson is ~0.1 Ohm. [3] The dissipated power would be 10W, so the power dissipation limitation will not be violated. The junction temperature can be found using the same equation as the Schottky diode. The junction temperature will be Tj = Ta + (P x Roja) = 25 + (10 x 62) = 645 degrees celsuis. This is far beyond the 125 degrees celsuis max that the mosfet can handle therefore a heat sink will be needed for this chip.  

The 1N4743A zener diode for the polarity checking circuit can dissipate 1W of power. Using the Ltspice circuit shown below the current flowing through the diode for the max 40V input would be 2.68mA. Therefore the dissipated power can be calculated through P = Vf * If = 13 * 2.68m = 34.8mW. Therefore the diode will work as intended. [13]  

![image](https://github.com/user-attachments/assets/c2600de8-c021-457e-a493-42c112fefb3d)


The current limiting resistor in the polarity checking circuit has a max power dissipation of 1W. As shown below the current flowing through the resistor would be 2.68mA. Therefore the power dissipated would be P = I^2 x R = (2.68m)^2 x 10000 = 71.8mW. Therefore the power dissipation limit will not be violated. [14]  

# References
[1] A. Ward, “Questions for Initial Lochinvar Meeting (1) - Answered.” Lochinvar, Cookeville, Sep. 11, 2024  
[2]  “IEC 61010-2-081 - safety requirements for electrical equipment for measurement, control, and laboratory use – part 2-081: Particular requirements for automatic and semi-automatic laboratory equipment for analysis and other purposes | Engineering360,” GlobalSpec, https://standards.globalspec.com/std/13207536/IEC%2061010-2-081 (accessed Sep. 21, 2024).  
[3] “IRF9540NPBF,” Infineon Technologies, https://www.infineon.com/dgdl/irf9540npbf.pdf?fileId=5546d462533600a401535611cfa21dc8 (accessed Nov. 21, 2024).  
[4] “Ti,” Texas Instruments, https://www.ti.com/lit/ug/slvu261/slvu261.pdf?ts=1719995246833&ref_url=https%253A%252F%252Fwww.ti.com%252Fproduct%252FTPS61500%253Fbm-verify%253DAAQAAAAJ_____9MmIuL_yBQIIZ_XbUMP7Hy669m5KhAc66gboQ_qz98FypIehgkez1fwBw-DwTL1fvTIi5dUWsQAhqRgd8atqHnL9vzYwWqX5UjgEs9IuKniEUz7mniIxQyloEzs0Z4McU5-MRMCUG9NoCHWNH1QACawps0fBNVFaeMSUeU66PAmgiylHob45TdnbC89xvDUYzBTbRLkKgLp2q_CUWA0I99tiu0NDrq5wYGQhKu0aXECLj9RpgP33Z3w4ahQQ8ZbkfaYRWgso2j7mYY2WvKetO2fq8BdVfUUgzHGhVwWKfzBXQ (accessed Nov. 21, 2024).  
[5] “LM5180EVM-S05,” LM5180EVM-S05 Evaluation board | TI.com, https://www.ti.com/tool/LM5180EVM-S05?keyMatch=LM5180EVM-S05&tisearch=universal_search&usecase=hardware#design-files (accessed Nov. 21, 2024).  
[6] “MBRS410LT3G,” Onsemi, https://www.onsemi.com/pdf/datasheet/mbrs410lt3-d.pdf (accessed Nov. 30, 2024).  
[7] “1n4001.pdf,” Diotec, https://diotec.com/request/datasheet/1n4001.pdf (accessed Nov. 30, 2024).  
[8] “PC817XxNSZ1B datasheet,” Mouser, https://www.mouser.com/datasheet/2/365/PC817XxNSZ1B_07Oct16_Spec_ED-16P010-1360269.pdf (accessed Nov. 30, 2024).  
[9] “STM32 nucleo-64 Board user Manual - STMicroelectronics,” ST, https://www.st.com/resource/en/user_manual/dm00105823-stm32-nucleo-64-boards-mb1136-stmicroelectronics.pdf (accessed Nov. 30, 2024).  
[10] “NHD-0420H1Z-FL-GBW-33V3 Character Liquid Crystal Display Module ,” Newhavendisplay, https://newhavendisplay.com/content/specs/NHD-0420H1Z-FL-GBW-33V3.pdf (accessed Nov. 30, 2024).  
[11] “25AA640A/25LC640A 64K SPI bus serial EEPROM,” Microchip, https://ww1.microchip.com/downloads/aemDocuments/documents/MPD/ProductDocuments/DataSheets/25AA640A-25LC640A-64K-SPI-Bus-Serial-EEPROM-20001830G.pdf (accessed Nov. 30, 2024).  
[12] “Datasheet - Texas Instruments,” Texas Instruments, https://www.ti.com/lit/ds/symlink/tps796.pdf (accessed Nov. 30, 2024).  
[13] “ONSM-S-A0003585147-1.PDF,” On Semiconductor, https://rocelec.widen.net/view/pdf/7qfz7dzkx8/ONSM-S-A0003585147-1.pdf?t.download=true&u=5oefqw (accessed Nov. 30, 2024).  
[14] “RSF / RSMF series,” Seilect, https://www.seielect.com/catalog/sei-rsf_rsmf.pdf (accessed Nov. 30, 2024).  
