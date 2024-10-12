# Introduction  

**Tucker Basham**  
The ability to properly test and or simulate a system once completed is a fundamental cornerstone of engineering. Proper testing of manufactured and engineered goods allow us to hone in on a device or machines functionality as well as simulate and assess the what if's and worst or best cases. Thus, for this project we have been tasked with the conceptual and physical design of a boiler fan simulation unit. This, appropriately deemed, fan diagnostic tool will simulate a boiler fan for our customer Lochinvar and will do so by taking in a PWM signal and returning a TACH signal. The reason a product such as this should exist is to save time and money, and allow for a full range of boiler diagnostic testing for Lochinvar. This device will in turn allow for much faster testing procedures thus increasing productivity and saving the time and money of Lochinvar.

# Restate the Fully Forumlate Problem

**Conner Vick**  
The problem is to create a diagnostic tool to help troubleshoot blower fans in boilers with the following specifications and constraints:  
*1) Case Specifications:*  
The tool shall have a case that is no larger than 12 by 12 inches in length and width.  

*2) Power Specifications:*  
The tool shall be able to be powered by both the DC power bus from the boiler's fan, which is 10 to 40 volts, and by a USB connection if a fan is not present.  

*3) Diagnostic Tool Specifications:*  
The following are the specifications for the diagnostic tool's hardware and software.  

1. The diagnostic tool shall have the hardware to accomplish all three modes.
2. The diagnostic tool shall allow the user to select one of the three modes, only the Fan Simulation mode will be functional.
3. The diagnostic tool shall have an LCD screen that will display the PWD signal, tachometer signal, and a user interface designed at a later date.
4. The diagnostic tool shall allow the user to change the minumum and maximum fan speed, the minumum PWM duty cycle needed for the fan to turn on, the minumum PWM duty cycle needed for the fan to continue running, and the fan speed to increase or decrease the transient timing factor.
5. The diagnostic tool will have buttons for the user to adjust which mode and/or the parameters for that mode.
6. The hardware shall be designed to accomplish the Fan Simulation Mode, the Fan Driving Mode, and the Monitoring Mode.
7. The following shall be possible in the Fan Simulation Mode:  
   - Adjusting the minimum and maximum fan speed
   - Adjusting the minimum PWM duty cycle needed for the fan to turn on
   - Adjusting the minimum PWM duty cycle for the fan to continue running
   - The fan speed increasing and decreasing the transient timing factor

8. The following shall be possible in the Fan Driving Mode:    
   - Setting a desired PWM signal to send to the fan
   - Setting a desired RPM to drive the fan at
   - User configuarble PID settings for fan speed control, PWM frequency, Enable / Disable control takeover, and Enable / Disable Tachometer Pass-through

9. The following shall be possible in the Monitoring Mode:    

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
The diagonostic tool's design and build phase shall not exceed the given $2,000 budget.   

*Constraints*  
The following section outlines the constraint statements that the team will adhere to.  

  The diagnostic tool shall adhere to the following standards:  
  1. IPC-2221: This standard outlines how PCB's should be designed to ensure the reliability, quality, and safety.  
  2. IPC J-STD-001: This standard is known as the "Requirements for Soldered Electrical and Electronic Assemblies". It correlates to the following key elements:  
     - Materials and Equipment used
     - Solder Processes and Procedures (Such as hand soldering)
     - Workmanship and Inspection Criteria
     - Training and Certification 

# Comparative Analysis of Potential Solutions

Since Lochinvar already knows what type of tool they are wanting we will compare different solutions for the subsystems instead of overall solutions for the problem. A list of different solutions for each subsystem is shown below, along with design considerations, and the chosen solutions.  

## Potential PCB Solutions

1. Single-Layer PCB
   - Single-layer PCBs consists of a single layer of conductive material with components and traces on one side. [1]
   - They are relatively simple and cost-effective, making them ideal for basic electronic devices. [1]
   - Some advantages for the single-layer PCB are the following: they are inexpensive, they can be manufactored faster, and since it is a single layer the designs are easier to produce. [1]
   - Some disadvantages are they operate at a slower speed, they have less freedom for the layout of the design, and they are larger. [2]
     
2. Multi-Layer PCB
   - Multi-layer PCBs consists of multiple layers of conductive material, with insulated layers in between with the traces and components on both sides. [1]
   - They can accommodate more complex circuit designs, which results in more flexibility for routing traces. [1]
   - Since the PCB has multiple layers of conductive material this helps to reduce signal noise and interference between components. [1]
   - Some advantages for the multi-layer PCB are the following: they have a more compact size, they have improved signal integrity due to being able to place the power and ground planes inbetween components, and they can operate at a faster speed. [3]
   - Some disadvantages are they cost more to produce, they are more complex to design, and they are harder to debug due to the inner layers. [3]
  
Our design needs to handle PWM and tachometer signals with high signal integrity due to the nature of the diagnostic tool. **This needs more added to it** Due to the design considerations we will be pursuing a multi-layered PCB design for our fan diagnostic tool.
   
## Potential Microcontroller Solutions

1. Single Microcontroller
   - If we used a single high preformance microcontroller it would handle all the tasks for the tool.
   - Some advantages to this would be a simplier hardware design due to fewer components, more efficient communication due to all tasks being managed by the same microcontroller, and it would be easier to debug and maintain since it is a single microcontroller.
   - Some disadvantages are with a more advanced microcontroller it will be more expensive, there is a single point of failure, and the programming will take longer due to all of the tasks the microcontroller will need to complete.
     
2. Multiple Microcontrollers
   - If we used multiple lower prefomance microcontrollers we could distribute the tasks.
   - Some advantages to this would be that each microcontroller could be developed and tested independently leading to decreased design and debug time.
   - Some disadvantages are due to having multiple microcontrollers the communication between all of them could be more complex, increased delays due to having to communicate between the microcontrollers, and the design would need to incorporate more hardware.  

Our design needs to handle PWM and tachometer signal processing, different operating modes, and communication with the display and other subsystems.  **This needs more added to it** Due to the design considerations we will be pursuing a single high preformance microcontroller for our fan diagnostic tool.

## Potential Display Solutions

1. Charatcer LCD Display (Liquid-Crystal Display)
   - Character LCD displays are able to display letters, numbers, and punctuation. [4]
   - Some advantages for this type of display are it is easy to program, it has low power consumption, and it is inexpensive. [4]
   - Some disadvantages for this type of display is it can only display letters, numbers, and punctuation. It also is limited on the colors it is able to display.
     
2. Graphical LCB Display (Liquid-Crystal Display)
   - Graphical LCD displays are able to display letters, numbers, punctuation, and custom graphics. [5]
   - Some advantages for this type of display is the flexibility to display any graphical information and they can offer a broader range of colors. [5]
   - Some disadvatanges for this type of display is it requires more complex software , they consume more power, and they cost more when compared to character LCDs. [6]  
  
Our design needs to display both numbers and replicated signals  **This needs more added to it** Due to the design considerations we will be pursuing a graphical LCD display for our fan diagnostic tool.

## Potential Power/Circuitry Solutions

1. Linear Regulators
   - haha
2. Switching Regulators
   - haha
3. Protective Power Circuitry
   - haha

## Potential Case Solutions

1. Plastic
    - haha
2. 3-D Printed
    - hhaha
   
# High Level Solution

**Conner Vick**  
The diagnostic tool will be developed primarily using a display and a microcontroller. 
The microcontroller will take in a desired signal and output a desired signal corresponding to a set of user-defined parameters 
(depennding on the mode of operation these will be some variation of PWM and TACH). 
The user will use the buttons connected to the microcontroller to set desired settings, 
and the display will be used to view the menus required to do so. 
The display will also display the PWM and TACH signals in relation to a mode chosen by the user in order for the user troubleshoot the issues regarding the blower fan properly. 
# Hardware Block Diagram

![Hardware Block Diagram](https://github.com/user-attachments/assets/ca0c93cc-edce-4dcb-9229-e3a34758b63b)

# Operational Flow Chart

![Operational Flow Chart](https://github.com/user-attachments/assets/1dbedbe4-67ea-484a-a8bd-07bfb2d6a8da)


# Atomic Subsytem Specifications

**Please place your customer specifications in your specific subsection so the designer can start their work**

## Microntroller 

1. The microcontroller shall be able to take in and output both PWM and tachometer signals.
2. The microcotroller shall be able to communicate to the display to update what is being displayed. 
3. The microcontroller shall be shall to review user inputs through the form of push buttons to change selected parameters and/or change what is being displayed when necessary.
4. The microcontroller shall be able to clean and replicate the signals used in the software pass-through mode. (Hardawre Specifications and not software specifications.) 

## Display Design

1. The display shall show the PWM signal.  
2. The display shall show the tachometer signal.  
3. The display shall show the different options for the user interface.  
4. The display shall show the correct operations based on the user input.  
5. The display shall have working buttons for the user to operate the diagnostic tool.  

## Power / Ciruitry   

1. The power/circuitry shall encompass safe and proper connections between all subsections of the project.
2. The power/circuitry shall be able to take in various DC voltage loads and adjust values appropriately.
3. The device shall be powered by the fan DC power bus as well as by the USB connection in case no fan is connected. 
4. The power/circuitry shall be able to take in TACH and PWM signal as well as output either. **Should this be in this section?**
5. The power/circuitry shall be presented via a block diagram. **Should I make a block diagram for this subsection**
6. The power/circuitry shall be placed in a design such that all I/O ports are properly mapped and subsection connections are clear and efficient. **Should this be in the PCB section**
7. The power/circuitry shall output DC power to the display and microcontroller.
8. The power/circuitry shall ensure stable power is output to all sensitive components such as the microcontroller.
9. The power/circuitry shall have safety measures in place to deal with noise and surges.
10. The power/circuitry shall use an LED to display the state of the power within the board.

The Power/Circuitry subsystem is responsible for delivering power to all components throughout the Fan Diagnostic Tool. It includes voltage regulation, power distribution and features to protect against overvoltage or overcurrent events. Additionally, this subsystem will be responsible for ensuring the sensitive components such as the microcontroller recieves stable power without noise or surges. Additionally this subsystem will have LEDs to indicate the power status of other subsystems.


Below describes the interfaces between the Power/Circuitry subsystem and the other subsystems:
1. External Connections
   - The Power/Circuitry subsystem will recieve power through an external source. Either the boiler controller will act as that source and will power the device through a molex connection, or the power will come from an USB connection.
2. Microcontroller
   - The Microcontroller subsystem will recieve an input power signal from the Power/Circuitry subsystem. Therefore the Power/Circuitry subsystem will be outputting a DC power signal.
3. Display
   - The Display subsystem will also recieve an input power signal from the Power/Circuitry subsystem. Therefore the Power/Circuitry subsystem will be outputting a DC power signal.
4. PCB
    - The PCB subsystem will be the physical integration of the Power/Circuitry subsystem. The Power/Circuotry subsystem will output DC power to the PCB and the PCB will distribute the power throughout to all necessary components.
5. Case
   - The Case and Power/Circuitry subsystems are not connected.

## PCB Design

1. The PCB shall have the connectors for the USB, power, fan interface, and controller interface near the edges to ensure easy access.
2. The PCB shall clearly label designators for easy assembly and debugging (e.g, R1, C2, etc.).
3. The PCB shall incorporate thermal managment techniques to reduce overheating and increase longivity of the board.
4. The PCB shall incorporate testing points to allow for easy probing during debugging.  

The PCB is responsible for linking together the various components and allows them to recieve the power and signals necessary. To adhere with the IPC-2221 standard, once the PCB is designed, the board will be produced by a company that creates boards in accordance with all the regulations covered in the standard. To adhere to IPC-J-STD-001 group members must be informed on the acceptable practices and materials used for soldering. The team must also ensure that suppliers of components and materials meet these requirements. Finally, preventing contamination of materials, tools, and surfaces is also required to meet this standard.  

## Case  

1. The case shall encase the the board.
2. The case shall protect the board if a drop occurs.
3. The case shall have openings for the display, controls, and ports.
   
# Resources and Timeline

**Ethan Haynes**

*Skill Sets Required:*    
To ensure the proper functionality of the device skills in circuity design, programming, CAD design, and embedded systems are required. While every team member has foundation of basic circuit and coding skills, the project requires on building these skills.

- PCB design
- Circuit design
- CAD
- C++
- Embedded system design

Softwares will need to be learned by various members to design subsystems of the project. Possible softwares that could be used include KiCad, for PCB and circuitry design, and Inventor, for the case design. The board will also require the use of soldering skills to attach the components.

*Costs and Timeline:*  
  
*Gantt Chart:*  



# Ethical, Professional, and Standards Considerations
**Jacob Brewer**  
Our diagnostic tool enhances workplace efficiency by reducing the time needed to test and evaluate boiler controls and fans. This improvement not only lowers production costs but also has the potential to reduce consumer prices, benefiting Lochinvar’s customers. In turn, this could attract more customers, driving increased revenue for the company and its employees. Additionally, the tool establishes a solid baseline product that can be further customized with additional modes for various applications.

As Electrical Engineering students, we are committed to adhering to the IEEE Code of Ethics, prioritizing safety, and ensuring the well-being of both Lochinvar’s team and our peers. In line with these principles, our group has explored design enhancements such as incorporating hermetically sealed buttons to minimize contamination risk and adding protective devices to guard against overcurrent and voltage spikes.



# Appendix
### Citations:   
[1] “Single-layer vs. multi-layer PCBS: What’s the difference?,” ElectronicsHacks, https://electronicshacks.com/single-layer-vs-multi-layer-pcbs/ (accessed Oct. 11, 2024).  
[2] Ibe, “Single-layer PCB and its types - the ultimate guide,” IBE Electronics, https://www.pcbaaa.com/single-layer-pcb/ (accessed Oct. 11, 2024).  
[3] “Advantages and disadvantages of multilayer PCBS,” Highleap Electronic, https://hilelectronic.com/multilayer-pcbs/#:~:text=Disadvantages%20of%20Multilayer%20PCBs%201%201.%20Increased%20Complexity,Design%20Time%20...%205%205.%20Thermal%20Management%20Challenges (accessed Oct. 11, 2024).  
[4] “Pros and cons of a character LCD displays,” Focus LCDs, https://focuslcds.com/journals/pros-and-cons-of-a-character-lcd/ (accessed Oct. 11, 2024).  
[5] “Graphic lcds: How it works, application & advantages,” Electricity Magnetism, https://www.electricity-magnetism.org/graphic-lcds/ (accessed Oct. 11, 2024).  
[6] “What is the difference between character and graphic LCD module?,” Shijiazhuang Dianguang Hi Tech Electronics Co., Ltd., https://www.dght-oledlcd.com/news/what-is-the-difference-between-character-and-graphic-lcd-module.html#:~:text=Both%20Character%20LCD%20and%20Graphic%20LCD%20modules%20have,excel%20in%20providing%20high-resolution%20graphics%20and%20dynamic%20content. (accessed Oct. 11, 2024). 


### Statement of Contribution:  
Layne Bowman  
Ethan Haynes  
Tucker Basham - Introduction and customer specifications for power/circuitry section.  
Matthew Vick- Back-end specifications, (I can do intro as well and restate the problem)  
Jacob Brewer - Specifications for the display also Ethical, Professional, and Standards Considerations section.







