# Function of the Subsystem  
The role of the post-processing subsystem is to prepare the incoming PWM and Tach signals to be read by the microcontroller. This subsystem will be responsible for isolation from the Molex connection. It also will step up the signals to the necessary 3.3V DC. Then for the case the function is the protect and enclose the PCB.

# Specifications and Constraints  
The Post-processing shall step up the tachometer signal, coming from the microcontroller, to send to the boiler controller.  
The Post-processing shall isolate the signal from backfeed.  
The case shall encase and protect the board.
The case shall have openings for the display, buttons, and ports.
The case shall have mounting points to secure the board.
The case shall include a raised bezel for the display for protection.  

# Overview of Proposed Solution  
The post-processing system starts off with a tachometer signal (3.3V) that it steps up from the microcontroller to send to the boiler controller (24V). In addition to this, the signal must be isolated to protect the system from power surges. To accomplish this, an opto-coupler circuit will be implemented to meet both of these requirements. This circuit will consist of an opto-coupler, a current limiting resistor, and a pull up resistor. The case will be designed in solidworks then 3D printed.  

# Interfacing with Other Subsystems
Microcontroller   
-The microcontroller subsystem will send a tachometer signal that has gone through the post-processing circuit.
Display  
-The Display subsystem will display the interpreted version of the tachometer signal from the microcontroller.
Case  
-The Case will account for the openings needed for the Molex connector and buttons.  
