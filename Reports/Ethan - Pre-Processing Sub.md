# Function of the Subsystem
The role of the Preprocessing subsystem is to prepare the incoming PWM and Tach signals to be read by the microcontroller. This subsystem will be responsible for isolation from the Molex connection. It also will step down the signals to the necessary 3.3V DC.

# Specifications and Constraints
The Preprocessing subsystem shall adhere to the following specifications and constraints:

*Specifications*
1. The Preprocessing shall step down the input PWM and Tach signal to send to the Microcontroller subsystem.
2. The Preprocessing shall electrically isolate the signal from any fluctuations in the signal from the Molex.

*Constraints*
1. The Preprocessing must step the signal down to a clear 3.3 V from a range of 10-40 V.
2. The subsystem must meet IPC J-STD-001.

*Justifictation for Constraints*
1. Constraint one applies because it is possible for the amplitude of the signals to be a range of values, but a constant 3.3 V will be wanted by the microcontroller to accurately read the signal.
2. Constraint two requires that proper soldering procedures, training, equipment, and materials are used. Following such guidelines will ensure safety and stable connections for the user of the tool and those working on it.

# Overview of Proposed Solution
There will be two Molex connectors on the board. One is for Fan Driving mode, the Fan Molex, and the other is for Fan Simulation Mode, Control Molex. Both are used for the Monitoring mode. The Fan Molex has PWM Input and a Tach Output. The Control Molex has Tach Input and a PWM output. In other words, for the Fan Molex the board is receiving a PWM signal and sending a Tach signal and for the Control Molex the board is recieving a Tach signal and sending a PWM signal.  

The input PWM and Tach signals must be stepped down to an amplitude suitable for our microcontroller, which is 3.3 V. In addition to this, the signal must be isolated. To accomplish this, an opto-coupler circuit will be implemented to meet both of these requirements. An opto-coupler provides electrical isolation between two different voltage levels using light to transfer the signal to the other circuit. This differs from surge protection in that surge protection absorbs spikes in voltage and redirects it to ground. This circuit will consist of an opto-coupler, a current limiting resistor, and a pull up resistor. After a signal is processed by this circuit it can be read and interpreted by the microcontroller. The current limiting resistor allows the LED of the opto-coupler to operate at a reliable current level and the pull up resistor will allow the output of the opto-coupler to reach 3.3 V and replicate the PWM or Tach signal.


# Interfacing with Other Subsystems
1. Microcontroller
   - The Microcontroller subsystem will receive the input Tach and PWM signals that has went through the pre-processing circuit.
2. Display
   - The Display subsystem will display the interpreted version of the processed signals from the microcontroller.
3. Case
   - The Case and Preprocessing are not connected.
4. Power
   - The Power subsystem will provide the 3.3 V that the preprocessing will use to pull up to for the PWM and Tach signals.
5. Post-processing
   - The Post-Processing and Pre-Processing and not connected. 
6. Memory
   - The Memory and Pre-processing subsystems are not connected.
7. Ports and Buttons
   - The Ports and Buttons subsystem provides the PWM and Tach inputs for the Pre-processing.



# Buildable Schematic
<img width="378" alt="Preprocessing circuit kicad V5" src="https://github.com/user-attachments/assets/1d3b6077-40df-40d8-b309-3004df6fd68e">

# PCB Layout
![image](https://github.com/user-attachments/assets/a5741e4c-52d9-4d9b-85f0-4c882c560005)
![image](https://github.com/user-attachments/assets/5a6e39ef-8f56-4d20-a397-60724bc26a80)

# BOM
| Manufacturer | Manufacturer Part Number | Distributor | Distributor Part Number | Quantity | Cost  | URL  | Component Name|
| :---:         | :---:                    | :---:       | :---:                   | :---:    | :---: | :---: | :---: |
| Sharp Microelectronics | PC817X1YSZW | Mouser |852-PC817X1YSZW | 2 | $1.28| https://www.mouser.com/ProductDetail/Sharp-Microelectronics/PC817X1YSZW?qs=t7xnP681wgVcLhY5Ec%252BPYQ%3D%3D | U3 and U4|
| Yageo | FMP200JR-52-1K8 | Digikey |1.8KZCT-ND | 2 | $0.62| https://www.digikey.com/en/products/detail/yageo/FMP200JR-52-1K8/2058663 | R3 and R6|
| Yageo | FMP200JR-52-5K1 | Digikey |5.1KZCT-ND | 2 | $0.64| https://www.digikey.com/en/products/detail/yageo/FMP200JR-52-5K1/2058704 | R4 and R5|
| Total       |       |     |     |   | $2.54 |  |  |

# Analysis
This is the analysis of the preprocessing circuit that the incoming Tach and PWM signals will go through before going to the microcontroller. As shown in the LTSpice simulation, two pulse signals are generated to simulate a Tach and PWM input signal. The incoming signal then goes through a 1800 Ohm current limiting resisitor. This will make the forward current going through the opto-coupler's LED stay within the desired range to increase the longevity of the component and provide an accurate signal to read. The incoming signals could be 10-40 Vdc, so this resistor was picked so that at 10 V the forward current is roughly 5 mA and at 40 V the current is roughly 20 mA. This is based on the LED's forward voltage being 1.2 V. So if the desired current is 5 mA at 10 V, then using the equation V-Vf/If = R = (10 - 1.2) / 0.005 ≈ 1800 Ohms. This current range ensures a reliable signal while not overheating the component. On the output side of the opto-coupler, a 300 Ohm resistor is used to pull up to the 3.3 V coming from the LDO. The output, now isolated, 3.3 V, and switching at the frequency of the incoming signal is ready to be read by the microcontroller. The opto-coupler chosen is a PC817A. This opto-coupler is good for the 6 kHz PWM signal that will need to be processed and can handle the above the maximum 40 Vdc that can be seen. The datasheet specifies a cutoff frequency of 80 kHz and includes rise and fall times of up to 18 µs, which supports operation well above 6 kHz. This means the component can handle the 6 kHz frequency signal without significant distortion or delay​ [2].

<img width="546" alt="Preprocessing circuit ltspice V2" src="https://github.com/user-attachments/assets/0680a3c8-14f2-42e0-abc8-1b5adba8ef31">

In the LTSpice circuit the Tach and PWM signals being read are simulated at being 24 V and being at the maximum possible frequencies that will need to be processed. For the PWM that is 6000 Hz and the Tach would be 20,000 rpm at 5 pulses per revolution equating to 100,000 rpm or 1666.7 Hz.  

**Input Current** 
<img width="959" alt="Preprocessing circuit ltspice_TACH_CURRENT" src="https://github.com/user-attachments/assets/3f18157c-823c-4b63-b5d5-bcd59df698e2">
<img width="959" alt="Preprocessing circuit ltspice_PWM_CURRENT" src="https://github.com/user-attachments/assets/cef58671-24c7-40ff-9caf-4c9a4cd27f40">
  
The above graphs show the forward current for the input side of the opto-coupler. With an input of 24 V that makes the forward current 12.67 mA, which can be calulated by (24 - 1.2) / 1800 = 12.56 mA. The LTSpice simulation reads at approximately 12.7 mA.  

**Output Voltage**
<img width="959" alt="Preprocessing circuit ltspice_TACH" src="https://github.com/user-attachments/assets/d989a517-e490-45f3-83d0-7a34aacfb296">
<img width="959" alt="Preprocessing circuit ltspice_PWM" src="https://github.com/user-attachments/assets/69429fcf-42ba-41a1-bdc1-0ee5f6ae4b18">
For the output side, the replicated signals are shown above. The Tach is the top and the PWM is the bottom. Both of these signals are replicated at 3.3 V and are close in shape to the original signals with some slight distortion. The 300 Ohm resistor was selected because this was the lowest resistance that can be used because going lower causes the signal to not go back down to 0 V. This is because a lower resistance increases current and in turn the opto-coupler's saturation voltage goes much further above the normal 0.2 V, which is why the graph shows the peaks at 3.3 V and 0.2 V.

This simulation shows that the chosen components will process and output the proper signal to the microcontroller. It will also be able to do so while remaining isolated from the input side of the circuit, protecting the board and various components.


# References
[1] IEC 61010-2-081 - safety requirements for electrical equipment for measurement, control, and laboratory use – part 2-081: Particular requirements for automatic and semi-automatic laboratory equipment for analysis and other purposes | Engineering360,” GlobalSpec, https://standards.globalspec.com/std/13207536/IEC%2061010-2-081 (accessed Nov 22, 2024).  
[2] "PC817X1YSZW" Sharp Electronics, https://www.mouser.com/datasheet/2/365/Sharpelectronics_08292023_73758-3310502.pdf (accessed Nov. 22, 2024).  
[3] "FMP200JR-52-1K8" Yageo, https://www.yageo.com/upload/media/product/app/datasheet/lr/yageo-fmp_datasheet.pdf  
[4] "FMP200JR-52-5K1" Yageo, https://www.yageo.com/upload/media/product/app/datasheet/lr/yageo-fmp_datasheet.pdf  
[5] "FMP200JR-52-5K1" Stackpole Electronics Inc, https://www.seielect.com/catalog/sei-rsf_rsmf.pdf
