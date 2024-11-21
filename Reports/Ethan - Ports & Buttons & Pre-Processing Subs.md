# Function of the Subsystem
The role of the Preprocessing subsystem is to prepare the incoming PWM and Tach signals to be read by the microcontroller. This subsystem will be responsible for isolation from the Molex connection. It also will step down the signals to the necessary 3.3V DC.

# Specifications and Constraints
1. The Pre-processing shall step down the input PWM  and Tach signal to send to the Microcontroller subsystem.
2. The Pre-processing shall isolate the signal from any fluctuations in the signal from the Molex.

# Overview of Proposed Solution
There will be two molex connectors on the board. One is for Fan Simulation mode, the Fan Molex, and the other is for Fan Simulation Mode, Control Molex. Both are used for the Monitoring mode. The Fan Molex has PWM Input and a Tach Output. The Control Molex has Tach Input and a PWM output. In other words, for the Fan Molex the board is receiving a PWM signal and sending a Tach signal and for the Control Molex the board is recieving a Tach signal and sending a PWM signal.
The input PWM and Tach signals must be stepped down to an amplitude suitable for our microcontroller, which is 3.3 V. In addition to this, the signal must be isolated to protect the system from power surges. To accomplish this, an opto-coupler circuit will be implemented to meet both of these requirements. This circuit will consist of an opto-coupler, a current limiting resistor, and a pull up resistor. After a signal is processed by this circuit it can be read and interpreted by the microcontroller.


# Interfacing with Other Subsystems
1. Microcontroller
   - The Microcontroller subsystem will receive the input Tach and PWM signals that has went through the pre-processing circuit.
2. Display
   - The Display subsystem will display the interpreted version of the signals from the microcontroller.
3. Case
   - The Case will account for the opening needed for the Molex connector.


# Buildable Schematic

<img width="372" alt="Preprocessing circuit kicad V4" src="https://github.com/user-attachments/assets/dcb9634a-3b48-49d6-a22f-8a0a1421f5a2">
<img width="501" alt="Buttons circuit kicad V2" src="https://github.com/user-attachments/assets/852243e5-a7fa-45b8-b416-8c54ed998564">


# PCB Layout

# BOM
| Manufacturor | Manufacturor Part Number | Distributor | Distributor Part Number | Quantity | Cost  | URL  | Component Name|
| :---         | :---:                    | :---:       | :---:                   | :---:    | :---: | :--- | :--- |
| Sharp Microelectronics | PC817X1YSZW | Mouser |852-PC817X1YSZW | 2 | $1.28| https://www.mouser.com/ProductDetail/Sharp-Microelectronics/PC817X1YSZW?qs=t7xnP681wgVcLhY5Ec%252BPYQ%3D%3D | U3 and U4|
| Vishay/Dale | CPF21K8000FKE14 | Mouser |71-CPF21K8000FKE14 | 2 | $4.12| https://www.mouser.com/ProductDetail/Vishay-Dale/CPF21K8000FKE14?qs=sGAEpiMZZMsPqMdJzcrNwgeiKxcYoFt34YmtFMkQd7c%3D | R3 and R6|
| Vishay/Dale | 71-CMF55300R00BER6 | Mouser |CMF55300R00BER6 | 2 | $5.52| https://www.mouser.com/ProductDetail/Vishay-Dale/CMF55300R00BER6?qs=%2FI5vA73T%252BYIBRycreqlPGg%3D%3D | R4 and R5|

# Analysis
<img width="959" alt="Preprocessing circuit ltspice_TACH" src="https://github.com/user-attachments/assets/d989a517-e490-45f3-83d0-7a34aacfb296">
<img width="959" alt="Preprocessing circuit ltspice_PWM" src="https://github.com/user-attachments/assets/69429fcf-42ba-41a1-bdc1-0ee5f6ae4b18">
<img width="556" alt="Preprocessing circuit ltspice" src="https://github.com/user-attachments/assets/87de5f02-f232-4d58-bccd-6764666816cd">

# References
