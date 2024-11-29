# Function of the Subsystem  
The role of the post-processing subsystem is to step up the incoming Tach signals coming from the microcontroller. This subsystem will be responsible for isolation from the Molex connection. It also will step up the signals to the necessary 5-12V DC. Then for the case the function is the protect and enclose the PCB.

# Specifications and Constraints  
The Post-processing shall step up the tachometer signal, coming from the microcontroller, to send to the boiler controller.  
The Post-processing shall isolate the signal from backfeed.  
The case shall encase and protect the board.
The case shall have openings for the display, buttons, and ports.
The case shall have mounting points to secure the board.
The case shall include a raised bezel for the display for protection.  

# Overview of Proposed Solution  
The post-processing system starts off with a tachometer signal (3.3V) that it steps up from the microcontroller to send to the boiler controller (5-12V). In addition to this, the signal must be isolated to protect the system from power surges. To accomplish this, an opto-coupler circuit will be implemented to meet both of these requirements. This circuit will consist of an opto-coupler, a current limiting resistor, and a pull up resistor. The case will be designed in solidworks then 3D printed.  

# Interfacing with Other Subsystems
Microcontroller   
-The microcontroller subsystem will send a tachometer signal that has gone through the post-processing circuit.  
Display  
-The Display subsystem will display the interpreted version of the tachometer signal from the microcontroller.  
Case  
-The Case will account for the openings needed for the Molex connector and buttons.  

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




