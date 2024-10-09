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

**Team** Maybe could use powerpoint or maybe autocad.  

## Operational Flow Chart

![Operational Flow Chart](https://github.com/user-attachments/assets/52b749fb-b345-4b3a-8c1d-126e047e38a1)


# Atomic Subsytem Specifications

**Please place your customer specifications in your specific subsection so the designer can start their work**

## Back-End Software Design
**(Comments)**

1) Needs to be able to take in PWM anolog and output TACH anolog(?? I do not know if anolog is the right word).  
2) Needs to be able to convert PWM into a dataset for signal proccessing(sampling).  
3) Needs to be able to take PWM dataset and output the appropriate signal with a given set of fan characteristics decided by the user(Will have to most likely look up how TACH is supposed to work in relation to PWM).  
4) Needs to be able to recive data from front-end to use for signal proccessing(User interface data).  

## Front-End Software Design

## Ciruitry   
1. The circuitry shall encompass safe and proper connections between all subsections of the project.
2. The circuitry shall ensure proper connections and data transfer between different sections of our project.
3. The circuitry shall be able to take in various DC voltage loads and adjust values appropriately.
4. The circuitry shall be able to take in TACH and PWM signal as well as output either.
5. The circuitry shall be presented via a block diagram.
6. The circuitry shall be placed in a design such that all I/O ports are properly mapped and subsection connections are clear and efficient.

## Physical Design

1. The PCB shall have the connectors for the USB, power, fan interface, and controller interface near the edges to ensure easy access.
2. The PCB shall clearly label designators for easy assembly and debugging (e.g, R1, C2, etc.).
3. The PCB shall consist of four layers.
   - Top layer: Components and signals
   - Inner layer 1: Ground plane
   - Inner layer 2: Power plane
   - Bottom layer: Components and signals
4. The PCB shall incorporate thermal managment techniques to reduce overheating and increase longivity of the board.
5. The PCB shall incorporate testing points to allow for easy probing during debugging.

   
## Power Management
The device shall be powered by the fan DC power bus (10-40Vdc) as well as by the USB connection in case no fan is connected. Ideally the device doesn’t need a separate power source and uses the fan DC power bus.

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







