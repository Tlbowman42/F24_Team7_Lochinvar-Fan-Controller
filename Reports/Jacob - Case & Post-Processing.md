# Function of the Subsystem  
The role of the post-processing subsystem is to step up the incoming Tach and PWM signals coming from the microcontroller. This subsystem will be responsible for electrically isolating the two different voltage levels using light to transfer the signal to the other circuit from the micro controller via an opto-coupler. It also will step up the signals to the necessary 10-12V and 24V DC. Then for the case the function is the protect and enclose the PCB and other components.

# Specifications and Constraints  
*Specifications*  
1. The Post-processing shall step up the tachometer and PWM signal, coming from the microcontroller, to send to the boiler controller.  
2. The Post-processing shall isolate the signal from backfeed.  
3. The case shall encase and protect the board.
4. The case shall have openings for the display, buttons, and ports.
5. The case shall have mounting points to secure the board.
6. The case shall include a raised bezel for the display for protection.  

*Constraints*  
1. The Post-processing must step up the PWM signal up from 3.3V to 24V.
2. The Post-processing must step up the Tach signal up from 3.3V to 10-12V
3. The case must fully protect all components inside of it.  
4. The subsystems must meet IPC J-STD-001.  

*Justifictation for Constraints*  
1. Constraint one applies because it is possible for the amplitude of the signals to be a range of values, but the pwm should be 24V and the tach will be 10V to 12V for accurate measurments.  
2. Constraint two applies because the case is useless if it doesn't provide adequate protection.  
3. Constraint three requires that proper soldering procedures, training, equipment, and materials are used. Following such guidelines will ensure safety and stable connections for the user of the tool and those working on it.

# Overview of Proposed Solution  
The post-processing system starts off with a tachometer and PWM signal (3.3V) that it steps up from the microcontroller to send to the boiler controller 10-12V for the tach signal or 24V for the pwm. It will also have a voltage regulator for the tach signal along with its supporting components. In addition to this, the signal must be isolated to protect the system from power surges. To accomplish this, an opto-coupler circuit will be implemented to meet both of these requirements. This circuit will consist of an opto-coupler, a current limiting resistor, and a pull up resistor. The case will be designed in solidworks then 3D printed.  

# Interfacing with Other Subsystems
Pre-Processing  
-The post-processing and case doesn't have any connection with the pre-processing sub system.  
Memory  
-The post-processing and the case doesn't have any connection with the memory sub system.
Microcontroller   
-The microcontroller subsystem will send a tachometer and PWM signal that has gone through the post-processing circuit.  
Display  
-The Display subsystem will display the interpreted version of the tachometer signal from the microcontroller.  
Case  
-The Case will account for the openings needed for the Molex connector and buttons.  
Power  
-The power system pulls up from the 24 V that went through the polarity checker.  
Display  
-The case will have an opening for the display.  
Ports and Buttons  
-The case will also have openings for all of the buttons and two openings for both of the molex connectors.  

# 3D design for case
Lid  
![Screenshot (190)](https://github.com/user-attachments/assets/c09ec1a6-7c91-4c66-9755-fb48292fd73b)

Inside  
![Screenshot (192)](https://github.com/user-attachments/assets/30ee5df7-b71c-4121-8ca5-8531643d1ac8)





# Buildable Schematic
![Screenshot (204)](https://github.com/user-attachments/assets/018e694d-c6ce-43ee-a82b-ecea509981eb)  

![Screenshot (205)](https://github.com/user-attachments/assets/7568b00c-22f1-4010-8761-22a9aa9d935a)  

# PCB
![Screenshot (206)](https://github.com/user-attachments/assets/3f0b9a97-10c4-402f-93e3-ddbac962168a)  



# BOM
| Manufacturer | Manufacturer Part Number | Distributor | Distributor Part Number | Quantity | Cost  | URL  | Lt Spice Name| Device Designations Kicad |
| :---:         | :---:                    | :---:       | :---:                   | :---:    | :---: | :---: | :---: | :---: |
| Texas Instruments | LM317HVT/NOPB | Digikey |LM317HVT/NOPB-ND | 1 | $2.44| https://www.digikey.com/en/products/detail/texas-instruments/LM317HVT-NOPB/212662 | U1| U7 |
| KEMET | C333C104F5G5TA | Digikey |C333C104F5G5TA-ND | 1 | $6.10| https://www.digikey.com/en/products/detail/kemet/C333C104F5G5TA/6658919 | C1| C4 |
| Nichicon| UKL2A010KDD | Digikey |493-15407-ND | 1 | $0.43| https://www.digikey.com/en/products/detail/nichicon/UKL2A010KDD/2598552?s=N4IgjCBcoMxaBjKAzAhgGwM4FMA0IB7KAbXBgBYAGEAXXwAcAXKEAZUYCcBLAOwHMQAX3wA2AJzwQSSGix5CJEOTBgAHGIDstBs0htOvAcJAAmSuQnQpKDDnxFIpMAAIArQDFtIJiwCqPLkYAeWQAWWxUTABXDmwhfABaEUlpTij5B1I4fBNaYwTcq1SOdPtFAFY8wUEgA | C2| C5 |
| TE Connectivity Passive Product| LR1F240R| Digikey |A121513CT-ND | 1 | $0.10| https://www.digikey.com/en/products/detail/te-connectivity-passive-product/LR1F240R/2381208 | R1| R2d |
| Vishay Beyschlag/Draloric/BC Components | MRS25000C1651FCT00 | Digikey |56-MRS25000C1651FCT00CT-ND | 1 | $0.38| https://www.digikey.com/en/products/detail/vishay-beyschlag-draloric-bc-components/MRS25000C1651FCT00/5064119| R2| R21 |
| Vishay Dale | CMF5530R000FHEB | Digikey |541-CMF5530R000FHEBTR-ND | 1 | $0.80|https://www.digikey.com/en/products/detail/vishay-dale/CMF5530R000FHEB/3618953 | X | R22 |
| Stackpole Electronics Inc | RSMF1JT2K00 | Digikey |RSMF1JT2K00TR-ND | 2 | $0.40| https://www.digikey.com/en/products/detail/stackpole-electronics-inc/RSMF1JT2K00/1694491 | R3 and R4| R14 and R15 |
| Sharp Microelectronics | PC817X1YSZW | Mouser |852-PC817X1YSZW | 2 | $1.28| https://www.mouser.com/ProductDetail/Sharp-Microelectronics/PC817X1YSZW?qs=t7xnP681wgVcLhY5Ec%252BPYQ%3D%3D | U3 and U4| U5 and U6 |
| YAGEO | MFR-25FRF52-210R | Digikey |13-MFR-25FRF52-210RTR-ND | 2 | $0.20|https://www.digikey.com/en/products/detail/yageo/MFR-25FRF52-210R/14826?s=N4IgTCBcDaILIDEBKBaMBWZD1jQRgAYkQBdAXyA | R1 and R2| R16 and R17 |
| ANYCUBIC | PLA filament | Amazon |PLA filament| 2 | $11.99|https://www.amazon.com/ANYCUBIC-Printer-Filament-Dimensional-Accuracy/dp/B0834W2MQN/ref=asc_df_B0834W2MQN?mcid=aec3a78e66c631779c2da5151b689fd9&tag=hyprod-20&linkCode=df0&hvadid=693071814430&hvpos=&hvnetw=g&hvrand=9174619748980743316&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9013113&hvtargid=pla-1670291370690&psc=1 | Case| Case |
| Total       |       |     |     |   | $ 38.50|  |  |

# Analysis
This is the analysis of the post-procesing and case subsystem. The post-processing section is designed to take a PWM and TACH signal as an input from the microcontroller. Then the those signals will be stepped up to the appropriate voltage. The PWM will go from 3.3V to 24V. While the TACH signal will go from 3.3V to 10-12V. The PWM circuit will need 10mA while the tach circuit will need  The circuit starts off with the PWM and TACH signal current flowing through a 210 Ohm resistor. This will make the forward current going through the opto-coupler's LED stay within the desired range to increase the longevity of the component and provide an accurate signal to read. The opto-coupler chosen is a PC817A. This opto-coupler is good for the 6 kHz PWM signal that will need to be processed and can handle the above the maximum 40 Vdc that can be seen. The datasheet specifies a cutoff frequency of 80 kHz and includes rise and fall times of up to 18 µs, which supports operation well above 6 kHz. This means the component can handle the 6 kHz frequency signal without significant distortion or delay​. I chose the 210 Ohm resistor by using this equation ((3.3V - 1.2V)/ 10mA) which is just ((V1-Vf)/i). On the other side of the opto-coupler for the PWM signal we have a 2k Ohm resistor which orignaly was a 1.2k Ohm resistor but we figured out through testing that the 2k Ohm resistor gives a better output signal. Next the TACH siganl was a little more complicated because lochinvar wanted it to only be stepped up to 10V. Like the PWM siganl we use a 2k Ohm step up resistor to provide a better signal. The difference between the two is that we had to use a 10V to 40V buck/boost converter to get the desired 10-12V TACH output that we want. 

Tach
![Screenshot (207)](https://github.com/user-attachments/assets/8d1cadf1-399b-4363-92d9-3d8111220846)  

PWM
![Screenshot (202)](https://github.com/user-attachments/assets/66ba0ffc-c4e0-4318-ac71-99ebf315327a)  


These picture shows the PWM and TACH out signals. The PWM shows the 24V output and the TACH shows the how the buck/boost converter needs about 15ms to hit peak output voltage. Then the current going to the opto-coupler will be the same for both. Also you can see in the TACH ouput that it ramps up over time due to the buck/boost converter.

PWM
![Screenshot (199)](https://github.com/user-attachments/assets/fb598a0b-784a-4177-8319-dc9a951d6bfa)

![Screenshot (196)](https://github.com/user-attachments/assets/e720a861-6325-4949-b159-21815681689c)  

 

TACH
![Screenshot (208)](https://github.com/user-attachments/assets/8d78b4ef-27cf-4156-bf87-29df6faa6cc6)  
![Screenshot (209)](https://github.com/user-attachments/assets/7145de99-3fa6-4100-ba58-e3cca6755f6c)  






Then for the case it is pretty simple. The box/internal design shows the two holes needed for the controller and fan molex connectors. As well I rounded the corners on the inside of the case to allow room to be able screw the lid to the top of the box. Then the 4 pegs is where the flyback converter will be mounted and secured. Finally for the lid of the case we just have an opening for the LCD display and holes for all of the buttons. Although the case is subject to change due to the PCB layout being updated and improved through Bruce's guidance.

# References
[1] IEC 61010-2-081 - safety requirements for electrical equipment for measurement, control, and laboratory use – part 2-081: Particular requirements for automatic and semi-automatic laboratory equipment for analysis and other purposes | Engineering360,” GlobalSpec, https://standards.globalspec.com/std/13207536/IEC%2061010-2-081 (accessed Nov 22, 2024).

[2] "PC817X1YSZW" Sharp Electronics, https://www.mouser.com/datasheet/2/365/Sharpelectronics_08292023_73758-3310502.pdf (accessed Nov. 22, 2024).

[3] "https://www.digikey.com/en/products/detail/analog-devices-inc/LTC3115EDHD-1-PBF/3074265"

[4] "https://www.analog.com/media/en/technical-documentation/data-sheets/LTC3115-1.pdf"



