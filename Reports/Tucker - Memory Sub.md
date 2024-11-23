
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

The memory subsystem will be connect to the man PCB via through whole soldering points. Furthermore, the memory subsystem will be connected to the microcontrollers ST-morpho connectors allowing for read and write via a serial SPI interface.
  
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

![image](https://github.com/user-attachments/assets/799e6c8f-e0e2-4153-ae29-1e028998ebe8)

# PCB Layout

# BOM

| Manufacteror | Manufacteror Part Number | Distributor | Distributor Part Number | Quantity | Cost  | URL  | Component Name  |
| :---         | :---:                    | :---:       | :---:                   | :---:    | :---: | :--- | :--- |
| Microchip Technology | 25AA640-I/SN	| Digikey | 25AA640-I/SN-ND | 1 | $0.93 | https://www.digikey.com/en/products/detail/microchip-technology/25AA640-I-SN/318777 | EEPROM Memory IC 64Kbit SPI 1 MHz 8-SOIC |
| Total | | | | | $0.93 | |

# Analysis

The memory analysis will be done in one complete part including,  

1. Analysis of micrcontroller serial connections  
2. Uses/Functionality of the EEPROM memory  

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

