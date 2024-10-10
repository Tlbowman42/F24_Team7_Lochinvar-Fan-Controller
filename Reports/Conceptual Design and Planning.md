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

![Hardware Block Diagram](https://github.com/user-attachments/assets/a5f96d97-f1a4-4459-9a31-c11c07cb50e2)


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

## Power / Ciruitry   

1. The circuitry shall encompass safe and proper connections between all subsections of the project.
2. The circuitry shall ensure proper connections and data transfer between different sections of our project. **Is this the same specification as #1**
3. The circuitry shall be able to take in various DC voltage loads and adjust values appropriately.
4. The circuitry shall be able to take in TACH and PWM signal as well as output either.
5. The circuitry shall be presented via a block diagram.
6. The circuitry shall be placed in a design such that all I/O ports are properly mapped and subsection connections are clear and efficient.
7. The device shall be powered by the fan DC power bus as well as by the USB connection in case no fan is connected. Ideally the device doesn’t need a separate power source and uses the fan DC power bus.

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

*Costs and Timeline:*  
  
*Gantt Chart:*  



# Ethical, Professional, and Standards Considerations

**Jacob Brewer**

# Appendix
### Citations:   


### Statement of Contribution:  
Layne Bowman  
Ethan Haynes  
Tucker Basham  
Matthew Vick- Back-end specifications, (I can do intro as well and restate the problem)  
Jacob Brewer  







