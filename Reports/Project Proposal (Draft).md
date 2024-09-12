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
  


# Relevant information
**Tucker Basham**

# Goals and how they are measured
**Everyone**

# Resources and Timeline
**Ethan Haynes & Everyone for timeline**

# Consider Broader Impacts
**Jacob Brewer**

# Citations
Please use IEEE format for citations and cite anything that is not common knowledge for an ECE student. (If your not sure if it should be cited, cite it and we can decide together)  
[1] “Fan Diagnostic Tool.” Lochinvar, Cookeville, Sep. 11, 2024  
[2] A. Ward, “Questions for Initial Lochinvar Meeting (1) - Answered.” Lochinvar, Cookeville, Sep. 11, 2024  




