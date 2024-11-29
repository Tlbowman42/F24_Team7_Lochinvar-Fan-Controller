# Function of the Subsystem
The role of the Ports and Buttons subsystem is for taking in power and signals to distribute throughout the board.

# Specifications and Constraints
The Ports and Buttons subsystem shall adhere to the following specifications and constraints:

*Specifications*
1. There shall be a Molex port and port to connect to the flyback converter. 
2. There shall be buttons to allow the user to navigate the menu on the display.

*Constraints*
1. The subsystem must meet IPC J-STD-001.

*Justifictation for Constraints*
Constraint one requires that proper soldering procedures, training, equipment, and materials are used. Following such guidelines will ensure safety and stable connections for the user of the tool and those working on it.

# Overview of Proposed Solution
There will be two Molex connectors on the board. One is for Fan Driving mode, the Fan Molex, and the other is for Fan Simulation Mode, Control Molex. Both are used for the Monitoring mode. The Fan Molex has PWM Input and a Tach Output. The Control Molex has Tach Input and a PWM output. In other words, for the Fan Molex the board is receiving a PWM signal and sending a Tach signal and for the Control Molex the board is recieving a Tach signal and sending a PWM signal.  

There will be two 40 pin receptacle connectors for the 80 Morpho pins on the Nucleo board. This will be what allows the rest of the board to send and recieve signals from the microcontroller.

There will be two 2 wire terminal blocks for the board to connect to the external flyback converter that takes in 24 V and will return 5 V. The flyback converter is a seperate smaller PCB from the main PCB

Finally, there will be 6 SPST push buttons so that the user can interface with the board to adjust parameters and navigate the menu of the diagnostic tool.

# Interfacing with Other Subsystems
1. Microcontroller
   - The Microcontroller subsystem will be connected to the PCB by the morpho pin receptacle connectors. It will also recieve the user's inputs from the push buttons
2. Display
   - The Display will react to the user's inputs based on what button is pressed.
3. Case
   - The Case must have openings for the ports and the buttons so that they are accessible to the user.
4. Power
   - The Power subsystem will recieve power from the Molex ports and the terminal blocks to be able to distribute power throughout the board. The buttons will pull down 3.3 V to send a signal to the microcontroller when they are pressed.
5. Post-processing
   - The Post-Processing recieves Tach and PWM signals from the Molex ports.
6. Pre-processing
   - The Pre-Processing recieves Tach and PWM signals from the Molex ports.
7. Memory
   - The Memory Subsystem and the Ports and Buttons Subsystems are not connected.



# Buildable Schematic
As shown in the photo below, there are 6 SPST switches that will act as left, right, up, down, ok, and back. They use 5000 Ohm pull down resistors to send a 3.3 V signal to their corresponding microcontroller pins. A pull down resistor circuit is chosen because that means power is only flowing to the pin when a button is pressed as opposed to pull up where power to all 6 pins would flow if they remain unpressed. This will cause less load demand from our power system.

*Buttons*

<img width="501" alt="Buttons circuit kicad V2" src="https://github.com/user-attachments/assets/c7abbf63-b4a9-4be4-9a27-9e698f18407b">  
  
*Ports*

<img width="394" alt="Portsandbuttonsbuildableschematic" src="https://github.com/user-attachments/assets/ef3c10f8-6d92-41cf-bca7-c7da5a17ddef">


# PCB Layout
![image](https://github.com/user-attachments/assets/a5741e4c-52d9-4d9b-85f0-4c882c560005)
![image](https://github.com/user-attachments/assets/5a6e39ef-8f56-4d20-a397-60724bc26a80)

# BOM
| Manufacturer | Manufacturer Part Number | Distributor | Distributor Part Number | Quantity | Cost  | URL  | Component Name|
| :---         | :---:                    | :---:       | :---:                   | :---:    | :---: | :--- | :--- |
| Molex | 39-30-3058 | Mouser Electronics | 538-39-30-3058 | 2 | $2.84 | https://www.mouser.com/ProductDetail/Molex/39-30-3058?qs=404muyNbhLG7BJxtPMLWWg%3D%3D | J1 and J2 |
| TE Connectivity AMP Connectors | 2-215307-0 | Digikey | A106399-ND | 2 | $5.34 | https://www.digikey.com/en/products/detail/te-connectivity-amp-connectors/2-215307-0/1149668 | J3 and J4|
| Würth Elektronik |691137710002| Digikey | 732-10955-ND | 2 | $0.72 | https://www.digikey.com/en/products/detail/w%C3%BCrth-elektronik/691137710002/6644051 | J5 and J6|
| C&K |D6C90 F2 LFS| Digikey | 401-1988-ND | 6 | $7.47 | https://www.digikey.com/en/products/detail/c-k/D6C90-F2-LFS/1466345 | S1 to S6|

# Analysis
A 5 kOhm pull down resistor is chosen as opposed to a typical 10 kOhm because the lower resistance will use 0.66 mA as opposed to 0.33 mA. This higher current will allow the signal to be stronger and have more immunity to noise. This current is not high enough to cause a large drain in power or introduce exesscive heat, therefore it will benefit the system to use the lower resistance so that when a button is pressed there will be no doubt that it was a press based on the signal the microcontroller recieves. This clear signal will allow the user to focus on what decisions they need to make next instead of dealing with misinputs.

<img width="367" alt="Buttons circuit digital" src="https://github.com/user-attachments/assets/0720f8b8-fbec-4c69-850d-7378e6eab843">


# References
[1] Flex PCB, “Joint Industry Standard (J-std-001): All you Need To Know,” Flex PCB, https://flexpcb.org/joint-industry-standard-j-std-001-all-you-need-to-know/#:~:text=What%20is%20the%20J-STD-001%20Standard%3F%20The%20J-STD-001%2C%20also,that%20provides%20guidelines%20for%20producing%20high-quality%20soldered%20interconnections. (accessed Sep. 21, 2024).
[2] "39-30-3058" Molex, https://www.molex.com/en-us/products/part-detail/39303058?display=pdf
[3] "2-215307-0" TE Connectivity AMP Connectors, https://www.te.com/usa-en/product-2-215307-0.datasheet.pdf
[4] "691137710002" Würth Elektronik, https://www.we-online.com/components/products/datasheet/691137710002.pdf
[5] "D6C90 F2 LFS" C&K, https://www.ckswitches.com/media/1341/d6.pdf
