# Introduction
**Conner Vick**  
Throughout many industry applications testing is one of the upmost priorities, this can be for many reasons such as reliability, safety, and quality. This is especially true for devices that operate countinously because any defects in such a device will show themselves much more quickly than a device that is used intermittently. In this project, the goal is to design a fan diagnostic tool for Lochinvar to test the communication between fan and controller in their boilers. This is important, because a fault in the communication between these two devices can lead to serious compications with the boiler. Without this tool, the troubleshooting proccess would take longer. Therefore, the project will increase the efficiency of the troubleshooting proccess; saving them time and money. 
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
As of now there are two documents found that contain relevant literture to the fan diagnostic tool being created in our project. The first comes from the Queensland University of Technology in Brisbane Australia. In this document the author mentions a system that uses front and back end software in order to help boiler technicians acquire better data and information. The author also mentions how the simulator should be able to predict changes or trends in the boilers in response to change in variables such as fan speed or other factors. Alongside this system, the author also mentions having sub-modeling systems for each part of the boiler itself. This information which may not hold the most weight for us, could also offer more solutions to our project via other boiler components.    

The second source comes from the GyeongSang National University ERI in Korea. In this document the author speaks on their development of a thermal power boiler system simulator. This system was implemented using a nueral network where the modeling techniques and software used could adapt and change in response to changes in the boiler itself. This document, while helpful I believe solely speaks on larger power plant uses and not smaller household boiler uses. Regardless this document could prove helpful when developing our software and approaching the problems proposed by our customers.  

Attached below are links to the two documents I found. Keep in mind the Korean document must be translated.  

Thermal Power System Simulator(Korea):  
https://koreascience.kr/article/JAKO202029462558941.page

Boiler Simulation Tool Development(Queensland):  
https://eprints.qut.edu.au/118512/


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
The budget for the project will compensate for components for the device and unknown future expenses of the project. Below is a table of the estimated costs of some of the components needed.  
| Component | Estimated cost |
| -------- | ------- |
| Microcontrollers  | $125    |
| PCB | $100     |
| Screen    | $100    |  

The timeline will consider the time needed for various designing, learning, ordering, implementation, and trouble shooting. Schedules and time for learning skills must be accounted for to meet deadlines.   

# Consider Broader Impacts
**Jacob Brewer**  
Our diagnostic tool will streamline workplace operations by cutting down the time needed to test and assess boiler controls and/or fans. In doing so it will reduce overall cost of the products that the tool is used on. In turn potentially reducing the cost for the customers of Lochinvar. It also allows Lochinvar to start with a baseline product that can be enhanced. By incorporating additional modes for various applications. As EE majors we are responsible for upholding IEEE code of ethics primarily focusing on the safety and wellness of all members of Lochinvar and fellow students. The team also will need to ensure that all work and ideas presented is our own and not duplicated from another tool.


# Citations
Please use IEEE format for citations and cite anything that is not common knowledge for an ECE student. (If your not sure if it should be cited, cite it and we can decide together)  
[1] “Fan Diagnostic Tool.” Lochinvar, Cookeville, Sep. 11, 2024  
[2] A. Ward, “Questions for Initial Lochinvar Meeting (1) - Answered.” Lochinvar, Cookeville, Sep. 11, 2024  
[3] “Generic Standard on Printed Board Design,” Lawrence Berkley National Laboratory , https://www-eng.lbl.gov/~shuman/NEXT/CURRENT_DESIGN/TP/MATERIALS/IPC_2221.pdf (accessed Sep. 13, 2024).  





