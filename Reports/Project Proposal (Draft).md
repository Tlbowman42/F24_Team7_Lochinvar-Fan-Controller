# Introduction
**Conner Vick**

# Specifications and Constraints
**Layne Bowman**  
*1) Case Specifications:*  
The customer does not have any specific guidelines for the materials used nor the size of the diagnogstic tool. However, the tool shall be smaller than 12 inches in length and width. [1]  

*2) Power Specifications:*  
Lochinvar requested the tool be able to run from both the DC power bus from the boiler's fan, which is from 10 to 40 volts, and by a USB connection if a fan is not present. [2] Therefore the tool with need a USB port somewhere on the tool, along with circuitry to step down the DC voltage to a usable level. Specific location and type of circuitry used will be based on the cumalalitive power needs of all system components for the diagnostic tool. (Look into wide range DC-DC Buck covertors) 

*3) Diagnostic Tool Modes Specifications:*  
The diagnostic tool shall be able to simulate the boiler's fan. In this mode the diagnostic tool will "Control allows an approximate simulation of a fan operation, which can be used for testing boiler controls. In this case, the diagnostic tool might only be connecyed to a boiler control and have no actual fan connected." [2] In this mode the diagnostic tool shall be able to simulate both a PWM signal and Tach signal.  

The following shall be possible in this mode:  

- Adjusting the minumum and maximum fan speed
- Adjusting the minumum PWM duty cycle needed for the fan to turn on
- Adjusting the minumum PWM duty cycle for the fan to continue running
- The fan speed increasing and decreasing the transient timing factor
  
*4) Budget Specifications:*  
The diagonostic tool's design and build phase will not exceed the given $2,000 budget.  

*Constraints*  
The following section outlines the constraint statements that the team will adhere to.  

  The diagnostic tool shall adhere to the following standards:  
  1. IPC-2221: This standard outlines how PCB's should be designed to ensure the reliability, quality, and safety. [3]
  2. **Maybe ASME Boiler and Pressure Standards mainly section VI in terms of Operational Safety Testing for the cutoff systems, this may be a different type of boiler**
  3. IEC 61010: The standard for the safety requirements for electrical equipment for measurement, control and laboratory use  [Find a source as everything I find you have to pay for]
  4. 

# Relevant information
**Tucker Basham**  
Some of the most important documents and specifications our team will need to work by include governmental and engineering specifications and regulations. Throughout the entire creation from design to hands on constrcution the team will need to adhere by and follow all rules and regulations corresponding to the project. For instance, standards such as the IEEE 1118.1-1990 speak on the proper use of microcontroller serial bus connections for interdevice connections. Regulations such as this one will both aid and hinder us in our creation of the diagnostic tool. We will need to ensure safe and compliant use in both our microchip connections and communications. Another largly important regulation comes from IEC 61010-1 Which speaks on the proper safety requirements for electrical equipment and measurement devices within a lab. This will be one of the most important regulations we follow as our entire project is based from creation and work inside of a testing lab. Furthermore, this regulation will also place some constraints on our devices eventual field testing applications. Another constraint placed on our design is done so by IEC 62680-1, these regulations work directly with the safe and proper use of USB's for powering and charging devices. As specified by the customer our design will need to have a USB-FTDI cable which can connect to a computer in order to recieve power. Thus, this regulation will need to be followed precisely by our team as to not break regulation requirements. Alongside these requirements we will also need to adhere to proper PCB design and specifications. Most of these specifications and regulations are laid out by the IPC-2221. However, our specific PCB design falls under more that just IPC-2221 and actualy falls under most IPC regulations listed from 2221-2226. With that being said the team will need to ensure we adhere to these standards as they are in place to keep consumers and engineers safe. Substantial thought will need to be put into the design of our PCB as alongside the IPC regulations there are also a multitude of classes for PCB's(Each class adhereing to their respective PCB uses). The team will need to ensure all listed regulations will be followed and that all products produced in this project will be of engineering, industrial, and governmental standards.  **(need more patent oriented/research paper info)**

# Goals and how they are measured
**Everyone**  

1. The diagnostic tool will be able to be powered by two different sources, a 10 to 40 volt DC bus and through a USB. For this to be successful the tool will need to be powered through both the mediums seperately ten out of ten times.
2. When powered the diagnostic tool's LCD screen will turn on, and will display data.
3. The diagnostic tool will be small enough to fit in a toolbox/bag for field use. A successful measure will be placing the tool in a toolbox/bag.
4. The diagonostic tool will be able to preform at least the fan simulation mode **(PLACE IN OTHER MODE AND DEFINE SUCCESS)**
5. The design and construction of the diagnostic tool will not exceed the price of $1,500.
6. Over 50% of the software will be programmed in C. For this to be successful GitHub will be used as a version control platform and it will be periodically used to determine the distribution of code.
7. **Place more in as needed**


# Resources and Timeline
**Ethan Haynes & Everyone for timeline**

*Skill Sets Required:*    
To ensure the proper functionality of the device skills in circuity design, programming, CAD design, and embedded systems are required. While every team member has foundation of basic circuit and coding skills, the success of our project depends on the building of these skills possessed by each team member.  

+ PCB design
+ Circuit design
+ CAD
+ C++
+ Embedded system design

*Costs and Timeline:*  
The budget for the project compensates for unknown future expenses of the project. It is estimated that the PCB, microcontrollers, and display will be no more than $1500. A list of the proposed budget will be provided in the appendix.

# Consider Broader Impacts
**Jacob Brewer**  
Our diagnostic tool will streamline workplace operations by cutting down the time needed to test and assess boiler controls and/or fans. In doing so it will reduce overall cost of the products that the tool is used on. In turn potentially reducing the cost for the customers of Lochinvar. It also allows Lochinvar to start with a baseline product that can be enhanced. By incorporating additional modes for various applications. As EE majors we are responsible for upholding IEEE code of ethics primarily focusing on the safety and wellness of all members of Lochinvar and fellow students. The team also will need to ensure that all work and ideas presented is our own and not duplicated from another tool.


# Citations
Please use IEEE format for citations and cite anything that is not common knowledge for an ECE student. (If your not sure if it should be cited, cite it and we can decide together)  
[1] “Fan Diagnostic Tool.” Lochinvar, Cookeville, Sep. 11, 2024  
[2] A. Ward, “Questions for Initial Lochinvar Meeting (1) - Answered.” Lochinvar, Cookeville, Sep. 11, 2024  
[3] “Generic Standard on Printed Board Design,” Lawrence Berkley National Laboratory , https://www-eng.lbl.gov/~shuman/NEXT/CURRENT_DESIGN/TP/MATERIALS/IPC_2221.pdf (accessed Sep. 13, 2024).  





