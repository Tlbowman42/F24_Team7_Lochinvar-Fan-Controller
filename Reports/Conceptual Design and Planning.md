# Introduction  

**Tucker Basham**  
The ability to properly test and or simulate a system once completed is a fundamental cornerstone of engineering. Proper testing of manufactured and engineered goods allow us to hone in on a device or machines functionality as well as simulate and assess the what if's and worst or best cases. Thus, for this project we have been tasked with the conceptual and physical design of a boiler fan simulation unit. This, appopriately deemed, fan diagnostic tool will simulate a boiler fan for our customer Lochinvar and will do so by taking in a PWM signal and returning a TACH signal. The reason a product such as this should exist is to save time and money, and allow for a full range of boiler diagnostic testing for lochinvar. This device will in turn allow for much faster testing procedures thus increasing productivity and saving the time and money of Lochinvar.

## Restate the Fully Forumlate Problem

**Conner Vick**  

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

1. The microcontroller shall be able to take in and output both PWM and tachometer signals. (Needs to be able to take in PWM anolog and output TACH anolog(?? I do not know if anolog is the right word).)
2. The microcotroller shall be able to **Plug in here**. (Needs to be able to convert PWM into a dataset for signal proccessing(sampling).)
3. The microcotroller shall be able to communicate to the display to take and store user inputs. (Needs to be able to take PWM dataset and output the appropriate signal with a given set of fan characteristics decided by the user(Will have to most likely look up how TACH is supposed to work in relation to PWM).)
4. The microcontroller shall be shall to review user inputs to change selected parameters and/or change what is being displayed when necessary.
5. The microcontroller shall be able to clean and replicate the signals used in the software pass-through mode. (Hardawre Specifications and not software specifications.) (Needs to be able to recive data from front-end to use for signal proccessing(User interface data).)

## Display Design

1. The display shall show the PWM signal.  
2. The display shall show the tachometer signal.  
3. The display shall show the different options for the user interface.  
4. The display shall show the correct operations based on the user input.  
5. The display shall have working buttons for the user to operate the diagnostic tool.  

## Power / Ciruitry   

1. The power/circuitry shall encompass safe and proper connections between all subsections of the project.
2. The power/circuitry shall be able to take in various DC voltage loads and adjust values appropriately.
3. The power/circuitry shall be able to take in TACH and PWM signal as well as output either.
4. The power/circuitry shall be presented via a block diagram.
5. The power/circuitry shall be placed in a design such that all I/O ports are properly mapped and subsection connections are clear and efficient.
6. The device shall be powered by the fan DC power bus as well as by the USB connection in case no fan is connected. Ideally the device doesn’t need a separate power source and uses the fan DC power bus.
7. The power/circuitry shall output DC power to the display and microcontroller.
8. The power/circuitry shall ensure stable power is output to all sensitive components.
9. The power/circuitry shall have safety measures in place to deal with noise and surges.
10. The power/circuitry shall use an LED to display the state of the power within the board.

The Power/Circuitry subsystem is responsible for delivering power to all components throughout the Fan Diagnostic Tool. It includes voltage regulation, power distribution and **Maybe Add in safety features**. Additionally, this subsystem will be responsible for ensuring the sensitive components such as the microcontroller recieves stable power without noise or surges. **Maybe add in adding an LED to show the power status and if there are any issues present.**
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

PCB design
Circuit design
CAD
C++
Embedded system design

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







