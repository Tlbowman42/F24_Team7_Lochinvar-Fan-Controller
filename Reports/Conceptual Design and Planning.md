# Introduction  

The ability to properly test and or simulate a system once completed is a fundamental cornerstone of engineering. Proper testing of manufactured and engineered goods allow us to hone in on a device's functionality as well as simulate various scenarios. The goal for this project is the conceptual and physical design of a boiler fan simulation unit. This fan diagnostic tool will simulate a boiler fan for our customer Lochinvar. The reason a product such as this should exist is to save time and money, and allow for a full range of boiler diagnostic testing for Lochinvar. This device will in turn allow for much faster testing procedures thus increasing productivity and saving the time and money of Lochinvar.

# Restate the Fully Formulate Problem

The problem is to create a diagnostic tool to help troubleshoot blower fans in boilers with the following specifications and constraints:  
*1) Case Specifications:*  
The tool shall have a case that is no larger than 12 by 12 inches in length and width.[13]    

*2) Power Specifications:*  
The tool shall be able to be powered by both the DC power bus from the boiler's fan, which is 10 to 40 volts, and by a USB connection if a fan is not present.[14] 
   

*3) Diagnostic Tool Specifications:*  
The following are the specifications for the diagnostic tool's hardware and software.  

1. The diagnostic tool shall have the hardware to accomplish all three modes.
2. The diagnostic tool shall allow the user to select one of the three modes, only the Fan Simulation mode will be functional.
3. The diagnostic tool shall have an LCD screen that will display the PWD signal, tachometer signal, and a user interface designed at a later date.
4. The diagnostic tool shall allow the user to change the minimum and maximum fan speed, the minimum PWM duty cycle needed for the fan to turn on, the minimum PWM duty cycle needed for the fan to continue running, and the fan speed to increase or decrease the transient timing factor.
5. The diagnostic tool will have buttons for the user to adjust which mode and/or the parameters for that mode.
6. The hardware shall be designed to accomplish the Fan Simulation Mode, the Fan Driving Mode, and the Monitoring Mode.
7. The following shall be possible in the Fan Simulation Mode:[13]  
   - Adjusting the minimum and maximum fan speed
   - Adjusting the minimum PWM duty cycle needed for the fan to turn on
   - Adjusting the minimum PWM duty cycle for the fan to continue running
   - The fan speed increasing and decreasing the transient timing factor

8. The following shall be possible in the Fan Driving Mode:[13]   
   - Setting a desired PWM signal to send to the fan
   - Setting a desired RPM to drive the fan at
   - User configurable PID settings for fan speed control, PWM frequency, Enable / Disable control takeover, and Enable / Disable Tachometer Pass-through

9. The following shall be possible in the Monitoring Mode:[13]    

**Physical Pass-through**
   - PWM signal from the control is physically connected to the boiler's fan, while the Fan Diagnostic Tool monitors the signal.
   - Tachometer signal from the fan is physically connected to the tachometer output for the boiler's controller, while the Fan Diagnostic Tool monitors the signal.

**Software Pass-through**  
  - PWM signal from the boiler's control is read by the diagnostic tool and is approximately replicated, duty cycle and frequency, in software. The simulated PWM signal is then sent to the fan.
  - Tachometer signal from the fan is read by the diagnostic tool and is approximately replicated, frequency, in software. The simulated tachometer signal is then sent to the boiler control.
  - Signal modifications such as: PWM duty cycle limiting, frequency changing, or duty cycle scaling.
  - The control can convert between pulses per revolution of the tachometer feedback
  - Ability to freeze PWM signal to the fan
  - Ability to set an overriding max and min RPM that will prevent the control from seeing a fan operating above a certain max speed or below a certain min speed.
  - Ability to set a cutoff / turn-on PWM cycle.
  - Ability to cause fan oscillation.
  - Ability to dampen PWM duty cycle changes that are sent to the fan.


*4) Budget Specifications:*  
The diagnostic tool's design and build phase shall not exceed the given $2,000 budget.[14]     

*Constraints*  
The following section outlines the constraint statements that the team will adhere to.  

  The diagnostic tool shall adhere to the following standards:  
  1. IPC-2221: This standard outlines how PCB's should be designed to ensure the reliability, quality, and safety.[15]  
  2. IPC J-STD-001: This standard is known as the "Requirements for Soldered Electrical and Electronic Assemblies". It correlates to the following key elements:[16]   
     - Materials and Equipment used
     - Solder Processes and Procedures (Such as hand soldering)
     - Workmanship and Inspection Criteria
     - Training and Certification 
   3. IEC 61010-2-081: The IEC 61010 standard is for the safety requirements for electrical equipment for measurement, control and laboratory use. The specific subsection that we will need to follow is subsection 2-081. This subsection applies to automatic and semi-automatic laboratory equipment for analysis and other purposes. In other words this section pertains to equipment for measuring or modifying one or more characteristics or parameters of samples.[17]

# Comparative Analysis of Potential Solutions

Since Lochinvar already knows what type of tool they are wanting we will compare different solutions for the subsystems instead of overall solutions for the problem. A list of different solutions for each subsystem is shown below, along with design considerations, and the chosen solutions.  

## Potential Microcontroller Solutions

1. Single Microcontroller
   - If we used a single high performance microcontroller it would handle all the tasks for the tool.
   - Some advantages to this would be a simpler hardware design due to fewer components, more efficient communication due to all tasks being managed by the same microcontroller, and it would be easier to debug and maintain since it is a single microcontroller.
   - Some disadvantages are with a more advanced microcontroller it will be more expensive, there is a single point of failure, and the programming will take longer due to all of the tasks the microcontroller will need to complete.
     
2. Multiple Microcontrollers
   - If we used multiple lower performance microcontrollers we could distribute the tasks.
   - Some advantages to this would be that each microcontroller could be developed and tested independently leading to decreased design and debug time.
   - Some disadvantages are due to having multiple microcontrollers the communication between all of them could be more complex, increased delays due to having to communicate between the microcontrollers, and the design would need to incorporate more hardware.  

Our design needs to handle PWM and tachometer signal processing, user-inputs, different operating modes, communication with the display and other subsystems. Due to the design considerations we will be pursuing a single high performance microcontroller for our fan diagnostic tool.

## Potential Display Solutions

1. Character LCD Display (Liquid-Crystal Display)
   - Character LCD displays are able to display letters, numbers, and punctuation. [4]
   - Some advantages for this type of display are it is easy to program, it has low power consumption, and it is inexpensive. [4]
   - Some disadvantages for this type of display is it can only display letters, numbers, and punctuation. It also is limited on the colors it is able to display.
     
2. Graphical LCB Display (Liquid-Crystal Display)
   - Graphical LCD displays are able to display letters, numbers, punctuation, and custom graphics. [5]
   - Some advantages for this type of display is the flexibility to display any graphical information and they can offer a broader range of colors. [5]
   - Some disadvantages for this type of display is it requires more complex software , they consume more power, and they cost more when compared to character LCDs. [6]  
  
Our design needs to display both numbers and replicated signals as graphs. Our design also needs to take into account the clarity of the graphs. Due to the design considerations we will be pursuing a graphical LCD display for our fan diagnostic tool.

## Potential Power Solutions

1. Linear Voltage Regulators
   - Linear voltage regulators are a system that maintains a consistent output voltage level, regardless of changes in the input voltage or load conditions. [7]
   - Some advantages for this type of voltage regulation is it is simple in design, inexpensive, and has better noise rejection. [7] [8]
   - Some disadvantages for this type of voltage regulation is they can only step down voltage, thermal issues when there is a large difference between the input and output voltages, and they are not very efficient when there is a large difference between the input and output voltages. [7] [8]
  
2. Switching Voltage Regulators
   - Switching voltage regulators are a type of power supply that efficiently converts an input voltage into a steady output voltage. [9]
   - Some advantages for this type of voltage regulation is it can step-up, step-down, and invert voltages. This type is highly efficient, and due to this it is not prone to thermal issues. It can also handle a wide range of voltage levels. [8] [9]
   - Some disadvantages for this type of voltage regulation is due to the high frequency switching operation it has a medium to high amount of noise. Due to this increased noise the design needs to be more complex to combat that. Finally this type of voltage regulation is more expensive. [8][9]

Our design needs to handle a DC voltage range from 10-40 volts. The tool also needs to have room to grow, therefore versatility is an important considerations. Due to the design considerations we will be pursuing a switching voltage regulator design for our fan diagnostic tool.

## Potential Case Solutions

1. 3D Printed with Basic PLA
    - Basic PLA is a thermoplastic monomer. (A type of plastic) [10]
    - Some advantages to basic PLA is it is environmentally friendly, it has a good print quality, and it is easy to use. [11]
    - Some disadvantages to basic PLA is it has a lower strength and durability when compared to other 3D printing materials. It has a poor heat resistance and it is not easy to achieve a smooth polished finish. [11]

2. 3D Printed with PLA+
    - PLA plus is an enhanced version of the basic PLA, that boosts the materials strength. [12]
    - Some advantages to PLA plus is it is stronger, has higher heat resistance, and can achieve a polished finish easier when compared to basic PLA. [12]
    - Some disadvantages to PLA plus is it takes longer to print, it is a harder to print with, and is more expensive when compared to basic PLA. [12]

Our design needs a case that will encase and protect all other subsystems. Due to the design considerations we will be pursuing PLA+ for our fan diagnostic tool.

## Potential Memory Solutions

1. 64Kbit EEPROM Chip
   - Non-volatile memory with easy microcontroller W/R integration over an I2C bus.[18]
   - Higher 8x8Kbit memory capabilities for greater storage.
   - Compact size and low power consuming design allow for perfect integration with low power microcontrollers.[18]
  
2. 32Kbit EEPROM Chip
   - Lower cost per unit and power consumption than other higher memory EEPROMs.
   - smaller storage size yet slightly faster read/write speeds.
   - Good for small data sets such as basic settings or small logs.[18]  

Our design will require an EEPROM with larger storage capacity rather than as opposed to slightly faster access speeds. Due to this we have chosen to go with the 64Kbit EEPROM chip as it fills our need for greater storage capacity while also maintaining fast read/write speeds.  

## Potential Pre-processing Solutions

1. Resistive Voltage Divider
   - A simple design to implement.
   - Does not work very well at high frequencies. (Can add in a parallel capacitance to correct this) [19]
   - This circuit does not have any isolation capabilities.

2. Opto-Isolator
   - Can electrically isolate the circuit.
   - They can handle high switching speeds or data rates. [20]
   - They may distort the signals, so they will not give you highly precise signals at high frequency rates. [20]

Our design needs to isolate the signal as well as step the voltage down. Due to the design considerations we will be pursuing an opto-isolator circuit for our fan diagnostic tool.
     
## Potential Post-processing Solutions

1. Op-Amp Circuit
   - Lots of versatility and availability, due to this it adds a lot of freedom to circuit design.
   - They are cost effective.
   - Many companies offering op-amps provide simulation support which is important for initial designing and testing. [21]

2. BJT Transistor Circuit
   - BJTs can be used in many different circuit configurations to amplify specific parameters depending on what you need (CB, CE, and CC Amplifier) [22]
   - These are also cost-effective solutions.
   - These circuits produce more noise.
  
Our design would benefit the versatility and simulation support that Op-Amps can provide. Due to the design considerations we will be pursuing an op-amp circuit for our fan diagnostic tool.

## Potential Ports & Buttons Solutions

The Ports will not have any possible solutions. We are to use the Ports Lochinvar has requested. Those connectors are a Molex and usb connection.

1. Push Button
   - They are simple to use.
   - They are durable.
   - The more you use it the more wear it will receive. [23]

2. Rotary Encoder
   - They are very reliable.
   - There different types of rotary encoders to choose from depending on all of our needs (Absolute, Rotary, and Incremental)
   - They are more susceptible to dirt and grime due to them being raised. [24]
  
Due to this tool being used in a testing environment and potentially in the field in future applications we will choose to use push buttons on our fan diagnostic tool.

# High Level Solution

The diagnostic tool will be developed primarily using a display and a microcontroller. 
The microcontroller will take in a desired signal and output a desired signal corresponding to a set of user-defined parameters 
(depending on the mode of operation these will be some variation of PWM and TACH). 
The user will use the buttons connected to the microcontroller to set desired settings, 
and the display will be used to view the menus required to do so. 
The display will also display the PWM and TACH signals in relation to a mode chosen by the user in order for the user troubleshoot the issues regarding the blower fan properly.  
This setup will allow for the stakeholders to receive the product that was promised. It will fall within the standards mentioned prior. This solution will work due to its simple setup. This helps mitigate risk and optimize resource utilization by reducing the likelihood of a potential failure.  

# Hardware Block Diagram

![Hardware Block Diagram V2](https://github.com/user-attachments/assets/b71d9996-ef65-4308-be23-6796f1e56375)

# Operational Flow Chart

![Operational Flow Chart](https://github.com/user-attachments/assets/1dbedbe4-67ea-484a-a8bd-07bfb2d6a8da)


# Atomic Subsystem Specifications  

The PCB will be imperative for most if not all of our subsystems, therefore the PCB shall follow the specifications listed below.  

1. The PCB shall have the connectors for the USB, power, fan interface, and controller interface near the edges to ensure easy access.
2. The PCB shall clearly label designators for easy assembly and debugging (e.g., R1, C2, etc.).
3. The PCB shall incorporate thermal management techniques where applicable to reduce overheating and increase longevity of the board.
4. The PCB shall incorporate testing points to allow for easy probing during debugging.  

The PCB is responsible for linking together the various components and allows them to receive the power and signals necessary. To adhere with the IPC-2221 standard, once the PCB is designed, the board will be produced by a company that creates boards in accordance with all the regulations covered in the standard. To adhere to IPC-J-STD-001 group members must be informed on the acceptable practices and materials used for soldering. All members of the team have completed the HSI soldering safety certification. The team must also ensure that suppliers of components and materials meet these requirements. Finally, preventing contamination of materials, tools, and surfaces is also required to meet this standard. The components will need to be properly soldered to the board to attach them physically and to ensure a good electrical connection.  

## Microcontroller 

1. The microcontroller shall be able to take in and output both PWM and tachometer signals.
2. The microcontroller shall be able to communicate to the display to update what is being displayed. 
3. The microcontroller shall be able to review user inputs through the form of push buttons to change selected parameters and/or change what is being displayed when necessary.
4. The microcontroller shall be able to clean and replicate the signals used in the software pass-through mode. (Hardware Specifications and not Software Specifications.)

The microcontroller is responsible for handling the various GPIO applications as well as the background signal processing and control systems. The microcontroller will be able to take in TACH and PWM signals as well as output such signals. The microcontroller encompasses both the hardware and software to complete the desired simulation modes as well as leaves room for future improvement.     

Below describes the interfaces between the microcontroller subsystem and the other subsystems:
1. Display
   - The microcontroller will send graphical information for display on the systems LCD via serial communication.
2. Power
   - The microcontroller will receive a 3.3V DC input power from the Power subsystem.
3. Memory
   - The microconroller subsystem will be connected to the memory subsystem via an I2C connection. This connection allows both proper and fast data transfer between the microcontroller and memory subsytem allowing for ease of data transfer and storage.
4. Ports and Buttons
   - The microcontoller will receive input from the ports and buttons subsection allowing for changes in the display menu and values in both the PWM and Tach signals.
5. Case
   - The microcontroller and case subsystems share no connection.
6. Pre-Processing
   - The microcontroller will receive a stepped down voltage signal from the pre-processing subsystem that will allow for the logging and modulation of PWM and Tach signals based off the selected diagnostic mode.
7. Post-Processing
   - The microcontroller will output a PWM or Tach signal based off the diagnostic mode selection to the post processing subsystem where the signal will be stepped up to match the voltage of the boiler unit.

## Display Design

1. The display shall show the PWM signal.  
2. The display shall show the tachometer signal.  
3. The display shall show the different options for the user interface.  
4. The display shall show the correct operations based on the user input.  

The Display is responsible for showing the PWM and TACH signals to the user and the menus needed to operate the device. This also includes the code responsible for making this happen. Even though the microcontroller is technically responsible for this on a component level, this subsystem will include this for the sake of dividing work up appropriately.  

Below describes the interfaces between the Display subsystem and the other subsystems:
1. Microcontroller
   - The Microcontroller subsystem will send graphical information to the Display subsystem through a serial UART connection.
2. Power
   - The Display subsystem will also receive an input 3.3V DC power signal from the Power subsystem.
## Power 

1. The Power shall encompass safe and proper Ports between all subsections of the project.
2. The Power shall be able to take in various DC voltage loads (24V & 5V) and adjust those voltages to usable levels (3.3V).
3. The device shall be powered by the fan DC power bus as well as by the USB connection in case no fan is connected. 
4. The Power shall be placed in a design such that all I/O ports are properly mapped and subsection Ports are clear and efficient. 
5. The Power shall output DC power to the display and microcontroller.
6. The Power shall ensure stable power is output to all sensitive components such as the microcontroller.
7. The Power shall have safety measures in place to deal with noise and surges.
8. The Power shall use an LED to display the state of the power within the board.

The Power subsystem is responsible for delivering power to all components throughout the Fan Diagnostic Tool. It includes voltage regulation, power distribution and features to protect against overvoltage or overcurrent events. Additionally, this subsystem will be responsible for ensuring the sensitive components such as the microcontroller receives stable power without noise or surges. The subsystem will receive power through an external source. Either the boiler controller will act as that source and will power the device through a Molex connection, or the power will come from an USB connection. This subsystem will have LEDs to indicate the power status of other subsystems. Finally this subsystem will also incorporate the electrical isolation through the use of opto-isolators.

Below describes the interfaces between the Power subsystem and the other subsystems:
1. Microcontroller
   - The Microcontroller subsystem will receive an input power signal from the Power subsystem. The voltage will initially come from a Molex connection from the boiler controller or to from the USB. This will either be 24V DC or 5V DC respectively. The Power subsystem will then step down the voltage to a useable 3.3V for the microcontroller. It will additionally provide electrical isolation between the USB and Molex connector through the use of an opto-isolator. Therefore the Power subsystem will be outputting a 3.3V DC power signal.  
2. Display
   - The Display subsystem will also receive the same 3.3V DC power signal the microcontroller subsystem receives from the Power subsystem. Therefore this signal will also be electrically isolated from any power surges. Finally, the Power subsystem will be outputting a 3.3V DC power signal.
3. Case
   - The Case and Power subsystems are not connected.
4. Pre-Processing
   - The Case and Power subsystems are not connected.
5. Post-processing
   - The Case and Power subsystems are not connected.  
6. Memory
   - The Case and Power subsystems are not connected.  
7. Ports and Buttons
   - The Ports and Buttons subsystem is directly connected to the Power subsystem. Specifically the Molex and USB Ports providing the 24V DC and 5V DC needed to power the tool. Therefore the Ports and Buttons subsystem will be outputting the DC power signals to the Power Subsystem, in other words the DC voltage will be an input to the Power subsystem.

## Case  

1. The case shall encase and protect the board.  
2. The case shall have openings for the display, buttons, and ports.  
3. The case shall have mounting points to secure the board.
4. The case shall include a raised bezel for the display for protection.  

The case is responsible for completely enclosing the PCB and protecting it. It will have various openings for the display, buttons, and ports. The only true connection the case has with any of the other subsections is the PCB. Via screws or some other form of physical connection.  

Interfaces with other subsystems:  

1. PCB  
   - The PCB is the only true connection physical connection with the case.  

2. Ports and buttons  
   - The case will have to have openings for the various ports and buttons.  

## Memory  

1. The memory shall have a width of a byte.  
2. The memory shall be able to communicate with the microcontroller though a serial protocol  

The memory subsystem is the EEPROM responsible for the display setting and log storage. The EEPROM will also be responsible for holding the boot settings for the diagnostic tool as well as other small memory caches such as the error codes, calibration data, and hardware lifetime counters and timestamps.
  
1.  Microcontroller
    - The memory subsystem will be connected to the microcontroller via the I2C port on the microcontroller, thus allowing for proper data storage and interfacing.
2.  Power
    - The memory subsystem will receive a stepped down input voltage of 3.3v DC from the power subsystem in order to be powered on.
3.  Ports & Buttons
    - The memory subsystem will connect to the ports/buttons subsystem via the FTDI connection to the microcontroller.
4.  Case
    - The case and memory subsystems are not connected.
5.  Post-Processing
    - The memory and post-processing subsystems are not connected.
6.  Pre-Processing
    - The memory and pre-processing subsystems are not connected.
7.  Display
    - The memory subsystem wont have a physical connection to the display however, the EEPROM will contain data logs from the periheral devices on the board such as the display. This information will most likely be data logs and error messages pertaining to the display.

## Pre-processing 

1. The Pre-processing shall step down the PWM signal to send to the Microcontroller subsystem.
2. The Pre-processing shall isolate the signal from any fluctuations in the signal from the Molex.

The Molex connector will provide a PWM signal to the tool to take in as the fan speed. In order to process the signal an opto-couple circuit will be implemented to both adjust the signal so that it can be read by the microcontroller and will be used to protect the circuit from any power surge from the Molex connector. Afterwards, signal is then ready to be sent to the microcontroller.

Below describes the interfaces between the Pre-processing subsystem and the other subsystems:
1. Microcontroller
   - The Microcontroller subsystem will receive a PWM signal that has went through the pre-processing circuit.
2. Display
   - The Display subsystem will display the interpreted version of the PWM signal from the microcontroller.
3. Case
   - The Case will account for the opening needed for the Molex connector.

## Post-processing  

1. The Post-processing shall step up the tachometer signal, coming from the microcontroller, to send to the boiler controller.
2. The Post-processing shall isolate the signal from backfeed.

The post-processing system starts off with a tachometer signal (3.3V) that it steps up from the microcontroller to send to the boiler controller (24V). In order to isolate the post-processing signal, we will use an opto-coupler. This will protect our device from any power surges.  

Below are the interfaces between the Post-processing and the other subsystems:   
1.  Microcontroller  
   -The microcontroller subsystem will send a tachometer signal that has gone through the post-processing circuit.  
2. Display  
   - The Display subsystem will display the interpreted version of the tachometer signal from the microcontroller.  
3. Case  
   - The Case will account for the opening needed for the Molex connector.  
   
## Ports & Buttons  
 
1. There shall be a molex and a USB port.  
2. There shall be buttons to allow the user to easily navigate the menu on the display.  

The tool needs ports for both the molex connector and USB connector. The molex connection will provide both 24 Vdc for power, a PWM signal as input, and an additional pin will be used to send a tachometer signal. The USB port will provide 5 Vdc if the user chooses. The device will have multiple buttons which the user will use to navigate the menu and adjust the 6 parameters for the fan driving mode.  

Below describes the interfaces between the Ports and Buttons subsystem and the other subsystems:
1. Microcontroller
   - The Microcontroller subsystem will recieve power through either the USB or Molex port. These ports are also where the PWM and Tachometer signals will be sent and recieved from. The signals recieved from the buttons will be used by the microcontroller to both update the fan or boiler's parameters and the screen for the user.
2. Display
   - The Display subsystem will display the interpreted version of the PWM signal from the microcontroller. THe display will also change based on the user's inputs.
3. Case
   - The Case will account for the opening needed for the Molex, USB, and the buttons.
     
## Resources  
   
*Subsection:*
1. Microcontroller
   - Customer: Matthew Conner Vick
   - Solution: Tucker Basham
2. Display
   - Customer: Jacob Brewer
   - Solution: Matthew Conner Vick
3. Power
   - Customer: Tucker Basham
   - Solution: Layne Bowman
4. Memory
   - Customer: Matthew Conner Vick
   - Solution: Tucker Basham & Matthew Conner Vick
5. Case
   - Customer: Ethan Haynes
   - Solution: Jacob Brewer
6. Pre-processing
   - Customer: Layne Bowman
   - Solution: Ethan Haynes
7. Post-processing
   - Customer: Ethan Haynes
   - Solution: Jacob Brewer
8. Ports & Buttons
   - Customer: Jacob Brewer
   - Solution: Ethan Haynes

   
*Skill Sets Required:*  
To ensure the proper functionality of the device skills in circuity design, programming, CAD design, and embedded systems are required. While every team member has foundation of basic circuit and coding skills, the project requires on building these skills.

- PCB design
- Circuit design
- CAD
- C++
- Embedded system design

Softwares will need to be learned by various members to design subsystems of the project. Possible softwares that could be used include KiCad, for PCB and circuitry design, and Inventor, for the case design. The board will also require the use of soldering skills to attach the components.

*Costs:*  
Below is a rough estimation of some of the known major components needed for the project. These estimates are based upon items with similar functionalities of that required by the corresponding subsections.

| Component        | Part Number             |Estimated Cost |
| --------         | -------                 |-------        |
| Microcontroller  | STM32L4S9ZIJ6           | $15|
| Memory           | 25AA640-I/SN            | $15|
| PCB              | NA                      |$100|
| Display          | 4DLCD-35480320-IPS      |$34 | 
| Case             | PA07011                 |$30 |  
| Opto-isolators   | ACPL-C87A-500E, ISO1211 |$10 |  
| USB Port         | UJ2-AV-1-SMT-TR         | $1.45 |
| | | |
| Total | | $205.45 |

*Gantt Chart:*  
![Gantt Chart 10-22-24_page-0001](https://github.com/user-attachments/assets/d7147e24-e9b9-404d-b42e-017b4b2c08b5)
![Gantt Chart 10-22-24_page-0004](https://github.com/user-attachments/assets/0eec46d2-4e7f-4231-8570-d61e6be901a7)
![Gantt Chart 10-22-24_page-0003](https://github.com/user-attachments/assets/5dae89a3-bab6-4c39-905d-8c29512b1e42)
![Gantt Chart 10-22-24_page-0002](https://github.com/user-attachments/assets/b079c820-a0b8-4d22-bd4c-f7863db4724c)

# Ethical, Professional, and Standards Considerations
Our diagnostic tool enhances workplace efficiency by reducing the time needed to test and evaluate boiler controls and fans. This improvement not only lowers production costs but also has the potential to reduce consumer prices, benefiting Lochinvar’s customers. In turn, this could attract more customers, driving increased revenue for the company and its employees. Additionally, the tool establishes a solid baseline product that can be further customized with additional modes for various applications.

As Electrical Engineering students, we are committed to adhering to the IEEE Code of Ethics, prioritizing safety, and ensuring the well-being of both Lochinvar’s team and our peers. In line with these principles, our group has explored design enhancements such as incorporating hermetically sealed buttons to minimize contamination risk and adding protective devices to guard against overcurrent and voltage spikes.

For our standards we will be in compliance with the IPC-2221 ,IPC-J-STD-001, and IEC 61010-2-081. To comply with the IPC-2221 standard, the PCB will be manufactured by a company that follows all specified regulations within that standard. For IPC-J-STD-001, team members will be informed about the approved practices and materials for soldering. All team members have completed the HSI soldering safety certification, and the team must also confirm that component and material suppliers meet these standards. 

To comply with IEC 61010-2-082 standard, we will ensure protection against electrical shock through isolation, proper grounding, and insulation. Next we will make sure that our temperature never exceeds the limits set in this standard to protect our equipment and ourselves. Then, we will adhere to any mechanical hazards by using adequate guards or locking mechanisms. Lastly, we will adhere to the standards on software control by rigorusly testing our product to ensure safety.

# Appendix
### Citations:   
[1] “Single-layer vs. multi-layer PCBS: What’s the difference?,” ElectronicsHacks, https://electronicshacks.com/single-layer-vs-multi-layer-pcbs/ (accessed Oct. 11, 2024).  
[2] Ibe, “Single-layer PCB and its types - the ultimate guide,” IBE Electronics, https://www.pcbaaa.com/single-layer-pcb/ (accessed Oct. 11, 2024).  
[3] “Advantages and disadvantages of multilayer PCBS,” Highleap Electronic, https://hilelectronic.com/multilayer-pcbs/#:~:text=Disadvantages%20of%20Multilayer%20PCBs%201%201.%20Increased%20Complexity,Design%20Time%20...%205%205.%20Thermal%20Management%20Challenges (accessed Oct. 11, 2024).  
[4] “Pros and cons of a character LCD displays,” Focus LCDs, https://focuslcds.com/journals/pros-and-cons-of-a-character-lcd/ (accessed Oct. 11, 2024).  
[5] “Graphic lcds: How it works, application & advantages,” Electricity Magnetism, https://www.electricity-magnetism.org/graphic-lcds/ (accessed Oct. 11, 2024).  
[6] “What is the difference between character and graphic LCD module?,” Shijiazhuang Dianguang Hi Tech Electronics Co., Ltd., https://www.dght-oledlcd.com/news/what-is-the-difference-between-character-and-graphic-lcd-module.html#:~:text=Both%20Character%20LCD%20and%20Graphic%20LCD%20modules%20have,excel%20in%20providing%20high-resolution%20graphics%20and%20dynamic%20content. (accessed Oct. 11, 2024).  
[7] “Linear Voltage Regulator: How It Works, Application & Advantages,” Electricity Magnetism, https://www.electricity-magnetism.org/linear-voltage-regulator/ (accessed Oct. 11, 2024).  
[8] B. Schweber, “Understanding the advantages and disadvantages of linear regulators,” DigiKey, https://www.digikey.com/en/articles/understanding-the-advantages-and-disadvantages-of-linear-regulators?msockid=29ca711416706eb91ae8630a175c6f61 (accessed Oct. 11, 2024).  
[9] “Switching voltage regulator: How it works, application & advantages,” Electricity Magnetism, https://www.electricity-magnetism.org/switching-voltage-regulator/ (accessed Oct. 11, 2024).  
[10] “What is pla? (everything you need to know),” TWI, https://www.twi-global.com/technical-knowledge/faqs/what-is-pla#WhatisitUsedFor (accessed Oct. 11, 2024).  
[11] Z. Warner, “Advantages and disadvantages of PLA material in 3D printing,” Overture 3D, https://overture3d.com/blogs/beginners-guide/advantages-and-disadvantages-of-pla-material-in-3d-printing#:~:text=In%20conclusion%2C%20PLA%20material%20offers%20several%20advantages%20in,and%20durability%2C%20poor%20heat%20resistance%2C%20and%20limited%20flexibility. (accessed Oct. 11, 2024).  
[12] “Pla vs pla+: Is pla plus filament better for 3D printing?,” 3DSourced, https://www.3dsourced.com/3d-printer-materials/pla-vs-pla-plus-filament/#:~:text=PLA%2B%20is%20an%20enhanced%20version%20of%20regular%20PLA,conventional%20PLA%2C%20but%20it%20will%20also%20costs%20more. (accessed Oct. 11, 2024).  
[13] “Fan Diagnostic Tool.” Lochinvar, Cookeville, Sep. 11, 2024  
[14] A. Ward, “Questions for Initial Lochinvar Meeting (1) - Answered.” Lochinvar, Cookeville, Sep. 11, 2024  
[15] “Generic Standard on Printed Board Design,” Lawrence Berkley National Laboratory , https://www-eng.lbl.gov/~shuman/NEXT/CURRENT_DESIGN/TP/MATERIALS/IPC_2221.pdf (accessed Sep. 13, 2024).  
[16] Flex PCB, “Joint Industry Standard (J-std-001): All you Need To Know,” Flex PCB, https://flexpcb.org/joint-industry-standard-j-std-001-all-you-need-to-know/#:~:text=What%20is%20the%20J-STD-001%20Standard%3F%20The%20J-STD-001%2C%20also,that%20provides%20guidelines%20for%20producing%20high-quality%20soldered%20interPorts. (accessed Sep. 21, 2024).  
[17] “IEC 61010-2-081 - safety requirements for electrical equipment for measurement, control, and laboratory use – part 2-081: Particular requirements for automatic and semi-automatic laboratory equipment for analysis and other purposes | Engineering360,” GlobalSpec, https://standards.globalspec.com/std/13207536/IEC%2061010-2-081 (accessed Sep. 21, 2024).  
[18] R. Awati, “What is EEPROM (electrically erasable programmable read-only memory)?,” WhatIs, https://www.techtarget.com/whatis/definition/EEPROM-electrically-erasable-programmable-read-only-memory#:~:text=Finally%2C%20different%20voltages%20are%20required,data%20from%20or%20onto%20EEPROM. (accessed Oct. 25, 2024).  
[19] D. Mercer and Antoniu Miclaus Download PDF and A. Miclaus, “ADALM1000 SMU training topic 11: Frequency compensated voltage dividers,” ADALM1000 SMU Training Topic 11: Frequency Compensated Voltage Dividers | Analog Devices, https://www.analog.com/en/resources/analog-dialogue/studentzone/studentzone-november-2018.html#:~:text=A%20problem%20seen%20at%20high%20frequencies%20is%20that,to%20introduce%20capacitors%20in%20parallel%20to%20the%20resistors. (accessed Oct. 25, 2024).  
[20] Electrical4U, “Optoisolators: What they are and how they work,” Electrical4U, https://www.electrical4u.com/optoisolator-construction-and-operating-principle-of-optoisolator/#:~:text=Some%20of%20the%20advantages%20of%20optoisolators%20are%3A%201,can%20handle%20high%20switching%20speeds%20and%20data%20rates. (accessed Oct. 25, 2024).  
[21] Ovaga |, “Advantages and disadvantages of operational amplifier (op-amp),” Ovaga, https://www.ovaga.com/blog/package/advantages-and-disadvantages-of-operational-amplifier (accessed Oct. 25, 2024).  
[22] A. T. Editor, “Advantages and disadvantages of Bipolar Junction Transistor (BJT),” Polytechnic Hub, https://www.polytechnichub.com/advantages-disadvantages-bipolar-junction-transistor-bjt/ (accessed Oct. 25, 2024).  
[23] G. Wood, “Push Buttons vs switches: What are the pros and cons?,” aviewfromthehill.com.au, https://aviewfromthehill.com.au/push-buttons-vs-switches-what-are-the-pros-and-cons/ (accessed Oct. 25, 2024).  
[24] Admin, “What is rotary encoder? Construction & Working of rotary encoder,” How To Electronics, https://how2electronics.com/construction-working-rotary-encoder/#:~:text=Advantages%20%26%20Disadvantages%20of%20Rotary%20Encoders%3A%201%201.,incorporated%20into%20existing%20applications%207%207.%20Compact%20size (accessed Oct. 25, 2024).  


### Statement of Contribution:  
Layne Bowman - I contributed to the Microcontroller subsystem specifications, the Pre-processing subsystem, the potential solutions section, the hardware block diagram, the flow chart, and how the Power subsystem interfaces with all the other subsystems.  
Ethan Haynes - Resources and timeline, case specificaitons, post-processing specifications, ports and buttons solution, and pre-processing solution.  
Tucker Basham - Introduction, customer specifications for Power subsystem, microcontroller interface section, memory interface section, and potential solution section for memory subsystem.    
Matthew Vick- Display solution, PCB specifications, High-level solution, and re-introduce the problem.  
Jacob Brewer - Specifications for the display also Ethical, Professional, and Standards Considerations section. Then did the customers specs for the buttons & connections. Finally the details and connections for the post-processing system.  
