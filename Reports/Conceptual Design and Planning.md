# Introduction  

**Tucker Basham**  
The ability to properly test and or simulate a system once completed is a fundamental cornerstone of engineering. Proper testing of manufactured and engineered goods allow us to hone in on a device's functionality as well as simulate various scenarios. The goal for this project is the conceptual and physical design of a boiler fan simulation unit. This fan diagnostic tool will simulate a boiler fan for our customer Lochinvar. The reason a product such as this should exist is to save time and money, and allow for a full range of boiler diagnostic testing for Lochinvar. This device will in turn allow for much faster testing procedures thus increasing productivity and saving the time and money of Lochinvar.

# Restate the Fully Forumlate Problem

**Conner Vick**  
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
4. The diagnostic tool shall allow the user to change the minumum and maximum fan speed, the minumum PWM duty cycle needed for the fan to turn on, the minumum PWM duty cycle needed for the fan to continue running, and the fan speed to increase or decrease the transient timing factor.
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
   - User configuarble PID settings for fan speed control, PWM frequency, Enable / Disable control takeover, and Enable / Disable Tachometer Pass-through

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
The diagonostic tool's design and build phase shall not exceed the given $2,000 budget.[14]     

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
  
Our design needs to handle PWM and tachometer signals with high signal integrity due to the nature of the diagnostic tool. We also need to take into account size accomadations for our tool. Due to the design considerations we will be pursuing a multi-layered PCB design for our fan diagnostic tool.
   
## Potential Microcontroller Solutions

1. Single Microcontroller
   - If we used a single high preformance microcontroller it would handle all the tasks for the tool.
   - Some advantages to this would be a simplier hardware design due to fewer components, more efficient communication due to all tasks being managed by the same microcontroller, and it would be easier to debug and maintain since it is a single microcontroller.
   - Some disadvantages are with a more advanced microcontroller it will be more expensive, there is a single point of failure, and the programming will take longer due to all of the tasks the microcontroller will need to complete.
     
2. Multiple Microcontrollers
   - If we used multiple lower prefomance microcontrollers we could distribute the tasks.
   - Some advantages to this would be that each microcontroller could be developed and tested independently leading to decreased design and debug time.
   - Some disadvantages are due to having multiple microcontrollers the communication between all of them could be more complex, increased delays due to having to communicate between the microcontrollers, and the design would need to incorporate more hardware.  

Our design needs to handle PWM and tachometer signal processing, user-inputs, different operating modes, communication with the display and other subsystems. Due to the design considerations we will be pursuing a single high preformance microcontroller for our fan diagnostic tool.

## Potential Display Solutions

1. Charatcer LCD Display (Liquid-Crystal Display)
   - Character LCD displays are able to display letters, numbers, and punctuation. [4]
   - Some advantages for this type of display are it is easy to program, it has low power consumption, and it is inexpensive. [4]
   - Some disadvantages for this type of display is it can only display letters, numbers, and punctuation. It also is limited on the colors it is able to display.
     
2. Graphical LCB Display (Liquid-Crystal Display)
   - Graphical LCD displays are able to display letters, numbers, punctuation, and custom graphics. [5]
   - Some advantages for this type of display is the flexibility to display any graphical information and they can offer a broader range of colors. [5]
   - Some disadvatanges for this type of display is it requires more complex software , they consume more power, and they cost more when compared to character LCDs. [6]  
  
Our design needs to display both numbers and replicated signals as graphs. Our design also needs to take into account the clarity of the graphs. Due to the design considerations we will be pursuing a graphical LCD display for our fan diagnostic tool.

## Potential Power/Circuitry Solutions

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
   
# High Level Solution

**Conner Vick**  
The diagnostic tool will be developed primarily using a display and a microcontroller. 
The microcontroller will take in a desired signal and output a desired signal corresponding to a set of user-defined parameters 
(depennding on the mode of operation these will be some variation of PWM and TACH). 
The user will use the buttons connected to the microcontroller to set desired settings, 
and the display will be used to view the menus required to do so. 
The display will also display the PWM and TACH signals in relation to a mode chosen by the user in order for the user troubleshoot the issues regarding the blower fan properly.  
This setup will allow for the stakeholders to receive the product that was promised. It will fall within the standards mentioned prior. This solution will work due to its simple setup. This helps mitigate risk and optimize resource utilization by reducing the likelihood of a potential failure.  
# Hardware Block Diagram

![Hardware Block Diagram](https://github.com/user-attachments/assets/ca0c93cc-edce-4dcb-9229-e3a34758b63b)

# Operational Flow Chart

![Operational Flow Chart](https://github.com/user-attachments/assets/1dbedbe4-67ea-484a-a8bd-07bfb2d6a8da)


# Atomic Subsytem Specifications

**Please place your customer specifications in your specific subsection so the designer can start their work**

## Microcontroller 

1. The microcontroller shall be able to take in and output both PWM and tachometer signals.
2. The microcotroller shall be able to communicate to the display to update what is being displayed. 
3. The microcontroller shall be able to review user inputs through the form of push buttons to change selected parameters and/or change what is being displayed when necessary.
4. The microcontroller shall be able to clean and replicate the signals used in the software pass-through mode. (Hardware Specifications and not Software Specifications.)

The microcontroller is responsible for handling the various GPIO applications as well as the background signal processing and control systems. The microcontroller will be able to take in TACH and PWM signals as well as output such signals. The microcontroller encompasses both the hardware and software to complete the desired simulation modes as well as leaves room for future improvement.     

Below describes the interfaces betwen the microcontroller subsystem and the other subsystems:
1. Display
   - The microcontroller will send graphical information for display on the systems LCD via serial communication.
3. Power/Circuitry
   - The microcontroller will receive input power from the Power/Circuitry subsystem
4. PCB
   - The power/circuitry will distribute the DC input voltage to power the microcontroller through the PCB subsystem. The microcontroller will be connected to the PCB via physical connection.

## Display Design

1. The display shall show the PWM signal.  
2. The display shall show the tachometer signal.  
3. The display shall show the different options for the user interface.  
4. The display shall show the correct operations based on the user input.  

The Display is responsible for showing the PWM and TACH signals to the user and the menus needed to operate the device. This also includes the code responsible for making this happen. Even though the microcontroller is techanically responsible for this on a component level, this subsystem will include this for the sake of dividing work up appropriately.  

Below describes the interfaces between the Display subsystem and the other subsystems:
1. Microcontroller
   - The Microcontroller subsystem will send graphical information to the Display subsytem through a serial connection.
2. Power/Circuitry
   - The Display subsystem will also recieve an input power signal from the Power/Circuitry subsystem.
3. PCB
    - The PCB subsystem will distribute the input power signal from the Power/Circuitry subsystem to the Display subsystem. The Display subsystem is connected to the PCB subsystem by a physical connection.

## Power / Ciruitry   

1. The power/circuitry shall encompass safe and proper connections between all subsections of the project.
2. The power/circuitry shall be able to take in various DC voltage loads and adjust values appropriately.
3. The device shall be powered by the fan DC power bus as well as by the USB connection in case no fan is connected. 
4. The power/circuitry shall be placed in a design such that all I/O ports are properly mapped and subsection connections are clear and efficient. 
5. The power/circuitry shall output DC power to the display and microcontroller.
6. The power/circuitry shall ensure stable power is output to all sensitive components such as the microcontroller.
7. The power/circuitry shall have safety measures in place to deal with noise and surges.
8. The power/circuitry shall use an LED to display the state of the power within the board.

The Power/Circuitry subsystem is responsible for delivering power to all components throughout the Fan Diagnostic Tool. It includes voltage regulation, power distribution and features to protect against overvoltage or overcurrent events. Additionally, this subsystem will be responsible for ensuring the sensitive components such as the microcontroller recieves stable power without noise or surges. The subsystem will recieve power through an external source. Either the boiler controller will act as that source and will power the device through a molex connection, or the power will come from an USB connection. Additionally this subsystem will have LEDs to indicate the power status of other subsystems.


Below describes the interfaces between the Power/Circuitry subsystem and the other subsystems:
1. Microcontroller
   - The Microcontroller subsystem will recieve an input power signal from the Power/Circuitry subsystem. Therefore the Power/Circuitry subsystem will be outputting a DC power signal.
2. Display
   - The Display subsystem will also recieve an input power signal from the Power/Circuitry subsystem. Therefore the Power/Circuitry subsystem will be outputting a DC power signal.
3. PCB
    - The PCB subsystem will be the physical integration of the Power/Circuitry subsystem. The Power/Circuotry subsystem will output DC power to the PCB and the PCB will distribute the power throughout to all necessary components.
4. Case
   - The Case and Power/Circuitry subsystems are not connected.

## PCB Design

1. The PCB shall have the connectors for the USB, power, fan interface, and controller interface near the edges to ensure easy access.
2. The PCB shall clearly label designators for easy assembly and debugging (e.g, R1, C2, etc.).
3. The PCB shall incorporate thermal managment techniques where applicable to reduce overheating and increase longivity of the board.
4. The PCB shall incorporate testing points to allow for easy probing during debugging.  

The PCB is responsible for linking together the various components and allows them to recieve the power and signals necessary. To adhere with the IPC-2221 standard, once the PCB is designed, the board will be produced by a company that creates boards in accordance with all the regulations covered in the standard. To adhere to IPC-J-STD-001 group members must be informed on the acceptable practices and materials used for soldering. All members of the team have completed the HSI soldering safety certification. The team must also ensure that suppliers of components and materials meet these requirements. Finally, preventing contamination of materials, tools, and surfaces is also required to meet this standard. The components will need to be properly soldered to the board to attach them physically and to ensure a good electrical connection

Below describes the interfaces between the PCB subsystem and the other subsystems:
1. Microcontroller
   - The Microcontroller subsystem is connected to the rest of the components through the traces provided by the PCB.
2. Display
   - The Display subsystem will recieve its signals from the microcontroller through the traces provided by the PCB.
3. Power/Circuitry
    - The PCB subsystem will be the physical model of the interconnections of the Power/Circuitry subsystem. The Power/Circuitry subsystem will output DC power to the PCB and the PCB will distribute the power throughout to all necessary components. The PCB will be the pathway for delivering the necessary power and signals to the corresponding component.
4. Case
   - The Case will encapsulate the board and provide openings for the display, ports, and buttons.

## Case  

1. The case shall encase and protect the board.
2. The case shall have openings for the display, buttons, and ports.
3. The case shall have mounting points to secure the board.
4. The case shall include a raised bezel for the display for protection.  

The case is responsible for completely enclosing the PCB and protecting it. It will have various openings for the display, buttons, and ports. The only true connection the case has with any of the other subsections is the PCB. Via screws or some other form of physical connection.
   
## Resources 
   
*Subsection:*
1. Microcontroller
   - Customer: Matthew Vick
   - Solution: Tucker Basham
2. Display
   - Customer: Jacob Brewer
   - Solution: Matthew Vick
3. Power/Circuitry
   - Customer: Tucker Basham
   - Solution: Layne Bowman
4. PCB
   - Customer: Layne Bowman
   - Solution: Ethan Haynes
5. Case
   - Customer: Ethan Haynes
   - Solution: Jacob Brewer
   
*Skill Sets Required:*  
To ensure the proper functionality of the device skills in circuity design, programming, CAD design, and embedded systems are required. While every team member has foundation of basic circuit and coding skills, the project requires on building these skills.

- PCB design
- Circuit design
- CAD
- C++
- Embedded system design

Softwares will need to be learned by various members to design subsystems of the project. Possible softwares that could be used include KiCad, for PCB and circuitry design, and Inventor, for the case design. The board will also require the use of soldering skills to attach the components.

**Add in customer assignments**

*Costs:*  
Below is a rough estimation of some of the items needed for the project. The estimates for the microcontoller and display come from looking at components that have similar capabilities. The PCB estimation is based upon what a board of our specifications could cost and accounting for having to get multiple. The case estimation is based on the general price of what a roll of filament is.  

| Component | Estimated cost |
| -------- | ------- |
| Microcontroller  | $125    |
| PCB | $200     |
| Display    | $200    | 
| Case | $50 |  
| Power/Circuitry | $50 |  

*Gantt Chart:*  
![1727126681866-7f68bf22-5c86-4794-9fba-536b8495a20f_1](https://github.com/user-attachments/assets/2698b1b4-6c89-48b4-93c2-1518eb13501d)
![1727126681866-7f68bf22-5c86-4794-9fba-536b8495a20f_2](https://github.com/user-attachments/assets/883387a8-fd66-4de8-9697-a30ab7e1cdbb)
![1727126681866-7f68bf22-5c86-4794-9fba-536b8495a20f_3](https://github.com/user-attachments/assets/1f2b35fe-ba07-4e7e-940f-8a4e3984b9d7)
![1727126681866-7f68bf22-5c86-4794-9fba-536b8495a20f_4](https://github.com/user-attachments/assets/0c140eaf-4c1f-4bbd-9885-bfbd6470584b)



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
[7] “Linear Voltage Regulator: How It Works, Application & Advantages,” Electricity Magnetism, https://www.electricity-magnetism.org/linear-voltage-regulator/ (accessed Oct. 11, 2024).  
[8] B. Schweber, “Understanding the advantages and disadvantages of linear regulators,” DigiKey, https://www.digikey.com/en/articles/understanding-the-advantages-and-disadvantages-of-linear-regulators?msockid=29ca711416706eb91ae8630a175c6f61 (accessed Oct. 11, 2024).  
[9] “Switching voltage regulator: How it works, application & advantages,” Electricity Magnetism, https://www.electricity-magnetism.org/switching-voltage-regulator/ (accessed Oct. 11, 2024).  
[10] “What is pla? (everything you need to know),” TWI, https://www.twi-global.com/technical-knowledge/faqs/what-is-pla#WhatisitUsedFor (accessed Oct. 11, 2024).  
[11] Z. Warner, “Advantages and disadvantages of PLA material in 3D printing,” Overture 3D, https://overture3d.com/blogs/beginners-guide/advantages-and-disadvantages-of-pla-material-in-3d-printing#:~:text=In%20conclusion%2C%20PLA%20material%20offers%20several%20advantages%20in,and%20durability%2C%20poor%20heat%20resistance%2C%20and%20limited%20flexibility. (accessed Oct. 11, 2024).  
[12] “Pla vs pla+: Is pla plus filament better for 3D printing?,” 3DSourced, https://www.3dsourced.com/3d-printer-materials/pla-vs-pla-plus-filament/#:~:text=PLA%2B%20is%20an%20enhanced%20version%20of%20regular%20PLA,conventional%20PLA%2C%20but%20it%20will%20also%20costs%20more. (accessed Oct. 11, 2024).  
[13] “Fan Diagnostic Tool.” Lochinvar, Cookeville, Sep. 11, 2024  
[14] A. Ward, “Questions for Initial Lochinvar Meeting (1) - Answered.” Lochinvar, Cookeville, Sep. 11, 2024  
[15] “Generic Standard on Printed Board Design,” Lawrence Berkley National Laboratory , https://www-eng.lbl.gov/~shuman/NEXT/CURRENT_DESIGN/TP/MATERIALS/IPC_2221.pdf (accessed Sep. 13, 2024).  
[16] Flex PCB, “Joint Industry Standard (J-std-001): All you Need To Know,” Flex PCB, https://flexpcb.org/joint-industry-standard-j-std-001-all-you-need-to-know/#:~:text=What%20is%20the%20J-STD-001%20Standard%3F%20The%20J-STD-001%2C%20also,that%20provides%20guidelines%20for%20producing%20high-quality%20soldered%20interconnections. (accessed Sep. 21, 2024).  
[17] “IEC 61010-2-081 - safety requirements for electrical equipment for measurement, control, and laboratory use – part 2-081: Particular requirements for automatic and semi-automatic laboratory equipment for analysis and other purposes | Engineering360,” GlobalSpec, https://standards.globalspec.com/std/13207536/IEC%2061010-2-081 (accessed Sep. 21, 2024).  

### Statement of Contribution:  
Layne Bowman  
Ethan Haynes - Resources, speficications for case, and PCB solution.  
Tucker Basham - Introduction and customer specifications for power/circuitry section.  
Matthew Vick- Display solution, PCB specifications, High-level solution, and re-introduce the problem.  
Jacob Brewer - Specifications for the display also Ethical, Professional, and Standards Considerations section.
