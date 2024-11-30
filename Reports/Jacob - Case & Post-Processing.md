# Function of the Subsystem  
The role of the post-processing subsystem is to step up the incoming Tach and PWM signals coming from the microcontroller. This subsystem will be responsible for isolation from the Molex connection. It also will step up the signals to the necessary 10-12V and 24V DC. Then for the case the function is the protect and enclose the PCB and other components.

# Specifications and Constraints  
*Specifications*  
1. The Post-processing shall step up the tachometer and PWM signal, coming from the microcontroller, to send to the boiler controller.  
2. The Post-processing shall isolate the signal from backfeed.  
3. The case shall encase and protect the board.
4. The case shall have openings for the display, buttons, and ports.
5. The case shall have mounting points to secure the board.
6. The case shall include a raised bezel for the display for protection.  

*Constraints*  
1. The Post-processing must step the signal up from 3.3V to either 24V or 10V depending if its the tach or pwm signal.  
2. The case must fully protect all components inside of it.  
3. The subsystems must meet IPC J-STD-001.  

*Justifictation for Constraints*  
1. Constraint one applies because it is possible for the amplitude of the signals to be a range of values, but the pwm should be 24V and the tach will be 10V to 12V for accurate measurments.  
2. Constraint two applies because the case is useless if it doesn't provide adequate protection.  
3. Constraint three requires that proper soldering procedures, training, equipment, and materials are used. Following such guidelines will ensure safety and stable connections for the user of the tool and those working on it.

# Overview of Proposed Solution  
The post-processing system starts off with a tachometer and PWMsignal (3.3V) that it steps up from the microcontroller to send to the boiler controller 10-12V or 24V for the pwm. It will also have a voltage regulator for the tach signal along with its supporting components. In addition to this, the signal must be isolated to protect the system from power surges. To accomplish this, an opto-coupler circuit will be implemented to meet both of these requirements. This circuit will consist of an opto-coupler, a current limiting resistor, and a pull up resistor. The case will be designed in solidworks then 3D printed.  

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
![Screenshot (187)](https://github.com/user-attachments/assets/0fdb1b9f-381f-4eac-a8ed-c6e90f26a2d8)
![Screenshot (186)](https://github.com/user-attachments/assets/6c45987b-5658-4cb2-9177-ca0bef23dbe7)

# PCB
![image](https://github.com/user-attachments/assets/a5741e4c-52d9-4d9b-85f0-4c882c560005)
![image](https://github.com/user-attachments/assets/5a6e39ef-8f56-4d20-a397-60724bc26a80)

# BOM
| Manufacturer | Manufacturer Part Number | Distributor | Distributor Part Number | Quantity | Cost  | URL  | Component Name|
| :---:         | :---:                    | :---:       | :---:                   | :---:    | :---: | :---: | :---: |
| Analog Devices Inc. | LTC3115EDHD-1#PBF | Digikey |505-LTC3115EDHD-1#PBF-ND | 1 | $15.15| https://www.digikey.com/en/products/detail/analog-devices-inc/LTC3115EDHD-1-PBF/3074265 | U3|
| Yageo | FMP200JR-52-1K8 | Digikey |1.8KZCT-ND | 2 | $0.62| https://www.digikey.com/en/products/detail/yageo/FMP200JR-52-1K8/2058663 | R3 and R6|
| Yageo | FMP200JR-52-5K1 | Digikey |5.1KZCT-ND | 2 | $0.64| https://www.digikey.com/en/products/detail/yageo/FMP200JR-52-5K1/2058704 | R4 and R5|
| Total       |       |     |     |   | $ |  |  |

# Analysis
This is the analysis of the post-procesing and case subsystem. The post-processing section is designed to take a PWM and TACH signale as an input from the microcontroller. Then the those signals will be stepped up to the appropriate voltage. The PWM will be go from 3.3V to 24V. While the TACH signal will go from 3.3V to 10V. The circuit starts off the PWM and TACH signal current flowing through a 210 Ohm resistor. This will make the forward current going through the opto-coupler's LED stay within the desired range to increase the longevity of the component and provide an accurate signal to read. I chose the 210 Ohm resistor by using this equation ((3.3V - 1.2V)/ 10mA) which is just ((V1-Vf)/i). On the other side of the opto-coupler for the PWM signal we have a 2k Ohm resistor which orignaly was a 1.2k Ohm resistor but we figured out through testing that the 2k Ohm resistor gives a better output signal. Next the TACH siganl was a little more complicated because lochinvar wanted it to only be stepped up to 10V. Like the PWM siganl we use a 2k Ohm resistor connected to the TACH_Out to provide a better signal. The difference between the two is that we had to use a 10V to 40V buck converter to get the desired 10V TACH output that we want.  


![Screenshot (185)](https://github.com/user-attachments/assets/f15b72b3-fc62-4a0c-a634-47accde9ad2d)

These picture shows the PWM and TACH out signals. The PWM shows the 24V output and the TACH shows the how the buck converter needs about 15ms to hit peak output voltage. Then the current going to the opto-coupler will be the same for both.  

PWM
![Screenshot (194)](https://github.com/user-attachments/assets/2528b5af-7f39-4a92-a6d9-34c36d87c5c9)
![Screenshot (196)](https://github.com/user-attachments/assets/e720a861-6325-4949-b159-21815681689c)  

 

TACH
![Screenshot (195)](https://github.com/user-attachments/assets/ecc39231-faba-461d-93f9-59bc61ffcf2e)
![Screenshot (197)](https://github.com/user-attachments/assets/0cff14e8-354f-42ea-a11a-0b78a0fbf5f5)




Then for the case it is pretty simple. The box/internal design shows the two holes needed for the controller and fan molex connectors. As well I rounded the corners on the inside of the case to allow room to be able screw the lid to the top of the box. Then the 4 pegs is where the LDO will be mounted and secured. Finally for the lid of the case we just have an opening for the LCD display and holes for all of the buttons.





