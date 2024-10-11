# Introduction  

**Tucker Basham**  
The ability to properly test and or simulate a system once completed is a fundamental cornerstone of engineering. Proper testing of manufactured and engineered goods allow us to hone in on a device or machines functionality as well as simulate and assess the what if's and worst or best cases. Thus, for this project we have been tasked with the conceptual and physical design of a boiler fan simulation unit. This, appopriately deemed, fan diagnostic tool will simulate a boiler fan for our customer Lochinvar and will do so by taking in a PWM signal and returning a TACH signal. The reason a product such as this should exist is to save time and money, and allow for a full range of boiler diagnostic testing for lochinvar. This device will in turn allow for much faster testing procedures thus increasing productivity and saving the time and money of Lochinvar.

## Restate the Fully Forumlate Problem

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

## Comparative Analysis of Potential Solutions

**Layne Bowman**

# High Level Solution

**Conner Vick**  

## Hardware Block Diagram

![Hardware Block Diagram](https://github.com/user-attachments/assets/ca0c93cc-edce-4dcb-9229-e3a34758b63b)

## Operational Flow Chart

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
5. The power/circuitry shall be presented via a block diagram. 
6. The power/circuitry shall be placed in a design such that all I/O ports are properly mapped and subsection connections are clear and efficient.
7. The power/circuitry shall output DC power to the display and microcontroller.
8. The power/circuitry shall ensure stable power is output to all sensitive components such as the microcontroller.
9. The power/circuitry shall have safety measures in place to deal with noise and surges.
10. The power/circuitry shall use an LED to display the state of the power within the board.

The Power/Circuitry subsystem is responsible for delivering power to all components throughout the Fan Diagnostic Tool. It includes voltage regulation, power distribution and features to protect against overvoltage or overcurrent events. Additionally, this subsystem will be responsible for ensuring the sensitive components such as the microcontroller recieves stable power without noise or surges. Additionally this subsystem will have LEDs to indicate the power status of other subsystems.


Below describes the interfaces between the Power/Circuitry subsystem and the other subsystems:
1. Microcontroller
   - The Microcontroller subsystem will recieve an input power signal from the Power/Circuitry subsystem. Therefore the Power/Circuitry subsystem will be outputting a DC power signal.
2. Display
   - The Display subsystem will also recieve an input power signal from the Power/Circuitry subsystem. Therefore the Power/Circuitry subsystem will be outputting a DC power signal.

## PCB Design

1. The PCB shall have the connectors for the USB, power, fan interface, and controller interface near the edges to ensure easy access.
2. The PCB shall clearly label designators for easy assembly and debugging (e.g, R1, C2, etc.).
3. The PCB shall incorporate thermal managment techniques to reduce overheating and increase longivity of the board.
4. The PCB shall incorporate testing points to allow for easy probing during debugging.  

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


### Statement of Contribution:  
Layne Bowman  
Ethan Haynes  
Tucker Basham - Introduction and customer specifications for power/circuitry section.  
Matthew Vick- Back-end specifications, (I can do intro as well and restate the problem)  
Jacob Brewer - Specifications for the display also Ethical, Professional, and Standards Considerations section.







