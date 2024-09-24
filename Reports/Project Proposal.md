# Introduction 
Throughout many industry applications testing is one of the upmost priorities, this can be for many reasons such as reliability, safety, and quality. This is especially true for devices that operate countinously because any defects in such a device will show themselves much more quickly than a device that is used intermittently. In this project, the goal is to design a fan diagnostic tool for Lochinvar to test the communication between fan and controller in their boilers. This is important, because a fault in the communication between these two devices can lead to serious complications with the boiler. Without this tool, the troubleshooting proccess would take longer. Therefore, the project will increase the efficiency of the troubleshooting proccess; saving them time and money.  

# Specifications and Constraints
*1) Case Specifications:*  
The tool shall have a case that is no larger than 12 by 12 inches in length and width. [1]

*2) Power Specifications:*  
The tool shall be able to be powered by both the DC power bus from the boiler's fan, which is 10 to 40 volts, and by a USB connection if a fan is not present. [2]

*3) Diagnostic Tool Specifications:*  
The diagnostic tool shall have the hardware to implement all three modes given by Lochinvar; however, the tool will only be programmed to simulate the boiler's fan. [2]  

The following shall be possible in the Fan Simulation Mode:  

- Adjusting the minumum and maximum fan speed
- Adjusting the minumum PWM duty cycle needed for the fan to turn on
- Adjusting the minumum PWM duty cycle for the fan to continue running
- The fan speed increasing and decreasing the transient timing factor
  
*4) Budget Specifications:*  
The diagonostic tool's design and build phase shall not exceed the given $2,000 budget. [2]  

*Constraints*  
The following section outlines the constraint statements that the team will adhere to.  

  The diagnostic tool shall adhere to the following standards:  
  1. IPC-2221: This standard outlines how PCB's should be designed to ensure the reliability, quality, and safety. [3]
  2. IPC J-STD-001: This standard is known as the "Requirements for Soldered Electrical and Electronic Assemblies". It correlates to the following key elements [4]:
     
- Materials and Equipment used
- Solder Processes and Procedures (Such as hand soldering)
- Workmanship and Inspection Criteria
- Training and Certification 

 3. IEC 61010-2-081: The IEC 61010 standard is for the safety requirements for electrical equipment for measurement, control and laboratory use. The specific subsection that we will need to follow is subsection 2-081. This subsection applies to automatic and semi-automatic laboratory equipment for analysis and other purposes. In other words this section pertains to equipment for measuring or modifying one or more characteristics or parameters of samples. [5]

# Relevant information
As of now there are two documents found that contain relevant literture to the fan diagnostic tool being created in our project. The first comes from the Queensland University of Technology in Brisbane Australia. In this document the author mentions a system that uses front and back end software in order to help boiler technicians acquire better data and information. The author also mentions how the simulator should be able to predict changes or trends in the boilers in response to change in variables such as fan speed or other factors. Alongside this system, the author also mentions having sub-modeling systems for each part of the boiler itself. This information which may not hold the most weight for us, could also offer more solutions to our project via other boiler components. [6]  

The second source comes from the GyeongSang National University ERI in Korea. In this document the author speaks on their development of a thermal power boiler system simulator. This system was implemented using a neural network where the modeling techniques and software used could adapt and change in response to changes in the boiler itself. This document, while helpful I believe solely speaks on larger power plant uses and not smaller household boiler uses. Regardless this document could prove helpful when developing our software and approaching the problems proposed by our customers. [7]  

As of current standings there is only one fan diagnostic tool that shares similarities to our project. This product is a fan diagnostic tool coming from Lochinvar themselves and is called the Lochinvar RLY20119 blower/fan tester. Upon further inspection, this fan diagnostic tool seems to be a possible precursor to the product we're creating in this capstone project. Thus, even with the differences in the RLY20119 blower/fan tester and our project plans, theres a good possibility that we have much to learn from this product. However, on many websites this product is listed as discontinued, because of this we will need to find out why and possibly use the given reason as a chance to avoid an error in the product or possibly build upon it and find a solution to said error. Upon meeting with Lochinvar we will be sure to ask questions about this product and see if theres any chance we could obtain one or at least gain access to the schematics of one of these tools to further help us in the creation of our diagnostic tool.[8]

# Goals and how they are measured
1. The tool will have a case to encapsulate all of the circuitry. The measure of success will be if there is a case.
2. The diagnostic tool will be able to be powered by two different sources, a 10 to 40 volt DC bus and through a USB. For this to be successful the tool will need to be powered through both the mediums seperately ten out of ten times.
3. When powered the diagnostic tool's LCD screen will turn on, and will display data. To measure this as success the screen will need to power on and display experimental data five times.
4. The diagonostic tool will be able to preform the fan simulation mode. For this to be successful the tool will need to adjust the before mentioned parameters five out of five times.
5. Over 50% of the software will be programmed in C. For this to be successful GitHub will be used as a version control platform and it will be periodically used to determine the distribution of code.
6. The tool's design and implementation will not exceed $2000. For us to be successful we can not use more than $2000 for this project.
7. The tool's PCB will be designed accordingly to the guidelines set in IPC-2221. For this to be successful we will use a manufacturer that will follow the IPC-2221 guidelines.
8. The tool will follow the guidelines in IPC J-STD-001 for soldering the components. A measure of success will be for there to be no shorts in any of the hand soldered connections.
9. The tool will follow the guidelines set in IEC 61010-2-081. For this to be successful we will test the tool five times for shorts that could lead to the user being shocked.


# Resources and Timeline

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
  
*Gantt Chart:*  
![1727126681866-7f68bf22-5c86-4794-9fba-536b8495a20f_1](https://github.com/user-attachments/assets/2698b1b4-6c89-48b4-93c2-1518eb13501d)
![1727126681866-7f68bf22-5c86-4794-9fba-536b8495a20f_2](https://github.com/user-attachments/assets/883387a8-fd66-4de8-9697-a30ab7e1cdbb)
![1727126681866-7f68bf22-5c86-4794-9fba-536b8495a20f_3](https://github.com/user-attachments/assets/1f2b35fe-ba07-4e7e-940f-8a4e3984b9d7)
![1727126681866-7f68bf22-5c86-4794-9fba-536b8495a20f_4](https://github.com/user-attachments/assets/0c140eaf-4c1f-4bbd-9885-bfbd6470584b)


# Consider Broader Impacts
Our diagnostic tool will streamline workplace operations by cutting down the time needed to test and assess boiler controls and/or fans. In doing so it will reduce overall cost of the products that the tool is used on. In turn potentially reducing the cost for the customers of Lochinvar. It also allows Lochinvar to start with a baseline product that can be enhanced. By incorporating additional modes for various applications. As EE majors we are responsible for upholding IEEE code of ethics primarily focusing on the safety and wellness of all members of Lochinvar and fellow students. The team also will need to ensure that all work and ideas presented is our own and not duplicated from another tool.


# Appendix
### Citations:   
[1] “Fan Diagnostic Tool.” Lochinvar, Cookeville, Sep. 11, 2024  
[2] A. Ward, “Questions for Initial Lochinvar Meeting (1) - Answered.” Lochinvar, Cookeville, Sep. 11, 2024  
[3] “Generic Standard on Printed Board Design,” Lawrence Berkley National Laboratory , https://www-eng.lbl.gov/~shuman/NEXT/CURRENT_DESIGN/TP/MATERIALS/IPC_2221.pdf (accessed Sep. 13, 2024).  
[4] Flex PCB, “Joint Industry Standard (J-std-001): All you Need To Know,” Flex PCB, https://flexpcb.org/joint-industry-standard-j-std-001-all-you-need-to-know/#:~:text=What%20is%20the%20J-STD-001%20Standard%3F%20The%20J-STD-001%2C%20also,that%20provides%20guidelines%20for%20producing%20high-quality%20soldered%20interconnections. (accessed Sep. 21, 2024).  
[5] “IEC 61010-2-081 - safety requirements for electrical equipment for measurement, control, and laboratory use – part 2-081: Particular requirements for automatic and semi-automatic laboratory equipment for analysis and other purposes | Engineering360,” GlobalSpec, https://standards.globalspec.com/std/13207536/IEC%2061010-2-081 (accessed Sep. 21, 2024).  
[6] A. Mann, “BOILER SIMULATION TOOL DEVELOPMENT,” Queensland University of Technology, https://eprints.qut.edu.au/ (accessed Sep. 21, 2024).  
[7] J. H. Lee, “Development of Thermal Power Boiler System Simulator using neural network algorithm,” Journal of the Korea Society for Simulation, https://koreascience.kr/article/JAKO202029462558941.page (accessed Sep. 21, 2024).   
[8] “Lochinvar RLY20119 blower/fan tester,” parts4heating.com, https://www.parts4heating.com/Lochinvar-RLY20119-Blower-Fan-Tester-p/rly20119.htm (accessed Sep. 22, 2024). 

### Statement of Contribution:  
Layne Bowman worked on the Specifications and Constraints, and the Goals / Measures of Success.  
Ethan Haynes worked on the Skills, Budget, and Timeline / Gantt Chart.  
Tucker Basham worked on the Relevant Literature / Goals.  
Matthew Vick worked on the Introduction and the Goals  
Jacob Brewer worked on the Broader Impacts / Goals.







