# Function of the Subsystem
The role of the Preprocessing subsystem is to prepare the incoming PWM and Tach signals to be read by the microcontroller. This subsystem will be responsible for isolation from the Molex connection. It also will step down the signals to the necessary 3.3V DC.

# Specifications and Constraints
1. The Pre-processing shall step down the PWM signal to send to the Microcontroller subsystem.
2. The Pre-processing shall isolate the signal from any fluctuations in the signal from the Molex.

# Overview of Proposed Solution
The Molex connector will provide a PWM signal to the tool to take in as the fan speed. In order to process the signal an opto-coupler circuit will be implemented to adjust the signal so that it can be read by the microcontroller and will be used to protect the circuit from any power surge from the Molex connector. Afterwards, signal is then ready to be sent to the microcontroller.


# Interfacing with Other Subsystems
1. Microcontroller
   - The Microcontroller subsystem will receive a PWM signal that has went through the pre-processing circuit.
2. Display
   - The Display subsystem will display the interpreted version of the PWM signal from the microcontroller.
3. Case
   - The Case will account for the opening needed for the Molex connector.


# Buildable Schematic


# PCB Layout

# BOM

# Analysis

# References
