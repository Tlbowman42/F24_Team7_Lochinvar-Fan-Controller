# Experiment List

Below is a list of the experiments conducted for Experimental Analysis.

1. Power Source Stability and Redundancy Test
2. User Parameter Storage Test
3. Insert Here
4. Insert Here
5. Insert Here

# Power Source Stability and Redundancy Test

## Purpose and Justification

1. To verify the the Fan Diagnostic Tool operates stably when powered by:
   - The Fan Control Board (~24 Vdc)
   - USB Connection (5 Vdc)
   - Both power sources simultaneously
2. To ensure power switching does not disrupt tool operation.

## Detailed Procedure

### Setup
***Equipment Needed***
1. Lochinvar Control Board (24 Vdc)
2. Fan Diagnostic Tool
3. One Female to Male MOLEX wire harness
4. Resistors of varying amounts
   - 500 Ω
   - 1 kΩ
   - 5 kΩ
   - 10 kΩ
   - 100 kΩ
5. Digital Multimeter (for voltage and current measurements)
6. 2 Female to Male Wire connectors
7. USB Power Supply (5 Vdc source)

***Simulating Fan Control Board Power Supply***  
**Step 1: Setting up the Power Source**  
1. Lochinvar Control Board Power (24 Vdc)
   - Connect the female end of the MOLEX wire harness to the male end of the wire harness coming from the Lochinvar Control Board.
   - Connect the male end of the MOLEX wire harness to the Fan Diagnostic Tool's first MOLEX connector. (Side closest to the SD-Card)


2. USB Power (5 Vdc)
   - Connect the Fan Diagnostic tool to a USB power supply or to a laptop.


**Step 2: Setting up the Load on the Breadboard** 
1. Connect one of the female to male wire connectors to Pin 34 of the microcontroller (It is located on the bottom Morpho connector, the bottom row, three spaces from the right hand side)
![image](https://github.com/user-attachments/assets/84d45f88-e8e3-4bd0-8c14-e212e9e2e53d)
2. Connect the male end of the wire connector to the bread board.
3. Connect the other female to male wire connector to Pin 20 of the microcontroller (It is located on the bottom Morpho connector, the bottom row, ten spaces from the left hand side)
![image](https://github.com/user-attachments/assets/64daddf7-a7d7-4181-91dc-b8813e26a552)
4. Connect the male end of the wire connector to the ground rail to the bread board.
5. Connect the Multimeter across the resistor to measure the voltage across the load.
6. Connect the Multimeter in series with the resistor to measure the current through the load.


**Step 3: Testing Load Conditions**
1. Test the following resistor values to simulate varying loads
   - 1 kΩ (Minimal Load)
   - 500 Ω
   - 100 Ω
   - 10 Ω
   - 4.7 Ω (Highest Load)  


## Expected Results


## Actual Results

| Power Source Configuration | Resistor Value (Ω) | Voltage (V) | Current (mA) | Power (mW) | Voltage Drop (%) |
| :------------ | :-----------: | :-----------: | :-----------: | :-----------: | :-----------: |
| Lochinvar Control Board Only | 1k | Content Cell | Content Cell | Content Cell | Content Cell |
| Lochinvar Control Board Only | 500 | Content Cell | Content Cell | Content Cell | Content Cell |
| Lochinvar Control Board Only | 100 | Content Cell | Content Cell | Content Cell | Content Cell |
| Lochinvar Control Board Only | 10 | Content Cell | Content Cell | Content Cell | Content Cell |
| Lochinvar Control Board Only | 4.7 | Content Cell | Content Cell | Content Cell | Content Cell |
| USB Only | 1k | Content Cell | Content Cell | Content Cell | Content Cell |
| USB Only | 500 | Content Cell | Content Cell | Content Cell | Content Cell |
| USB Only | 100 | Content Cell | Content Cell | Content Cell | Content Cell |
| USB Only | 10 | Content Cell | Content Cell | Content Cell | Content Cell |
| USB Only | 4.7 | Content Cell | Content Cell | Content Cell | Content Cell |
| Dual Power | 1k | Content Cell | Content Cell | Content Cell | Content Cell |
| Dual Power | 500 | Content Cell | Content Cell | Content Cell | Content Cell |
| Dual Power | 100 | Content Cell | Content Cell | Content Cell | Content Cell |
| Dual Power | 10 | Content Cell | Content Cell | Content Cell | Content Cell |
| Dual Power | 4.7 | Content Cell | Content Cell | Content Cell | Content Cell |


## Interpretation and Conclusions
