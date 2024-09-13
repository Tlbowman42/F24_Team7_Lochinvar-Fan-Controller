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

**Write in Constraints for the tool**

# Relevant information
**Tucker Basham**

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


# Consider Broader Impacts
**Jacob Brewer**  
Our diagnostic tool will streamline workplace operations by cutting down the time needed to test and assess boiler controls and/or fans. In doing so it will reduce overall cost of the products that the tool is used on. In turn potentially reducing the cost for the customers of Lochinvar. It also allows Lochinvar to start with a baseline product that can be enhanced. By incorporating additional modes for various applications. As EE majors we are responsible for upholding IEEE code of ethics primarily focusing on the safety and wellness of all members of Lochinvar and fellow students. The team also will need to ensure that all work and ideas presented is our own and not duplicated from another tool.


# Citations
Please use IEEE format for citations and cite anything that is not common knowledge for an ECE student. (If your not sure if it should be cited, cite it and we can decide together)  
[1] “Fan Diagnostic Tool.” Lochinvar, Cookeville, Sep. 11, 2024  
[2] A. Ward, “Questions for Initial Lochinvar Meeting (1) - Answered.” Lochinvar, Cookeville, Sep. 11, 2024  




