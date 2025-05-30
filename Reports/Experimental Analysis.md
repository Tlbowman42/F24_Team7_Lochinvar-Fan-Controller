# Experiment List

Below is a list of the experiments conducted for Experimental Analysis.

1. Power Source Stability and Redundancy Test
2. User Parameter Storage Test
3. Fan Simulation Testing


# Power Source Stability and Redundancy Test

## Purpose and Justification

1. To verify that the Fan Diagnostic Tool operates stably when powered by:
   - The Fan Control Board (~24 Vdc)
   - USB Connection (5 Vdc)
   - Both power sources simultaneously
2. To ensure that power switching does not disrupt tool operation.

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
6. 2 Female to Male Wire Connectors
7. USB to USB Micro cable (5 Vdc source)

**Step 1: Setting up the Power Source**  
1. Lochinvar Control Board Power (24 Vdc)
   - Connect the female end of the MOLEX wire harness to the male end of the wire harness coming from the Lochinvar Control Board.
   - Connect the male end of the MOLEX wire harness to the Fan Diagnostic Tool's first MOLEX connector. (Side closest to the SD-Card)


2. USB Power (5 Vdc)
   - Connect the Fan Diagnostic tool to a USB power supply or a laptop.

![image](https://github.com/user-attachments/assets/879e7e65-9841-4369-b25e-331a32be9c48)  

![image](https://github.com/user-attachments/assets/4d7895df-d5ae-4ad9-b52e-4187c88b428c)


**Step 2: Setting up the Load on the Breadboard** 
1. Connect one of the female to male wire connectors to Pin 34 of the microcontroller (It is located on the bottom Morpho connector, the bottom row, three spaces from the right-hand side)  
![image](https://github.com/user-attachments/assets/84d45f88-e8e3-4bd0-8c14-e212e9e2e53d)
2. Connect the male end of the wire connector to the breadboard.
3. Connect the other female to male wire connector to Pin 20 of the microcontroller (It is located on the bottom Morpho connector, the bottom row, ten spaces from the left-hand side)  
![image](https://github.com/user-attachments/assets/64daddf7-a7d7-4181-91dc-b8813e26a552)
4. Connect the male end of the wire connector to the ground rail on the breadboard.
5. Connect the Multimeter across the resistor to measure the voltage across the load.
6. Connect the Multimeter in series with the resistor to measure the current through the load.

![image](https://github.com/user-attachments/assets/631592ae-0ab6-4a85-9a25-c4efdd974490)



**Step 3: Testing Load Conditions**
1. Test the following resistor values to simulate varying loads
   - 1 kΩ (Minimal Load)
   - 500 Ω
   - 100 Ω
   - 10 Ω
   - 4.7 Ω (Highest Load)  


## Expected Results
The expectation is that the Power Source Configuration will not affect the voltage stability across the board. As the resistance decreases (indicating a higher load), the current is expected to increase, resulting in greater power dissipation. Finally, it is believed that the voltage consistency should remain relatively constant, with the voltage drops across the resistor staying close to 3.3 Vdc.  

## Actual Results

| Power Source Configuration   | Resistor Value (Ω) | Measured Resistance (Ω) | Voltage (V)  | Current (mA) | Power Dissipated (mW)   |
| :--------------------------- | :----------------: | :---------------------: | :----------: | :----------: | :---------------------: |
| Lochinvar Control Board Only | 1k                 | 987.1                   | 3.309        | 3.353        | 11.1                    |
| Lochinvar Control Board Only | 470                | 467.1                   | 3.304        | 7.083        | 23.4                    |
| Lochinvar Control Board Only | 100                | 97.63                   | 3.264        | 33.576       | 109.6                   |
| Lochinvar Control Board Only | 10                 | 9.98                    | 3.189        | 331.79       | 1064.5                  |
| Lochinvar Control Board Only | 4.7                | 4.75                    | 3.0394       | 685.73       | 2084.2                  |
| USB Only                     | 1k                 | 987.1                   | 3.309        | 3.356        | 11.1                    |
| USB Only                     | 470                | 467.1                   | 3.304        | 7.083        | 23.4                    |
| USB Only                     | 100                | 97.63                   | 3.266        | 33.589       | 109.7                   |
| USB Only                     | 10                 | 9.98                    | 3.197        | 333.23       | 1065.3                  |
| USB Only                     | 4.7                | 4.75                    | 3.036        | 693.72       | 2106.1                  |
| Dual Power                   | 1k                 | 987.1                   | 3.309        | 3.356        | 11.1                    |
| Dual Power                   | 470                | 467.1                   | 3.304        | 7.083        | 23.4                    |
| Dual Power                   | 100                | 97.63                   | 3.265        | 33.590       | 109.7                   |
| Dual Power                   | 10                 | 9.98                    | 3.194        | 333.21       | 1064.3                  |
| Dual Power                   | 4.7                | 4.75                    | 3.065        | 695.77       | 2132.5                  |


## Interpretation and Conclusions

The purpose of this experiment was to evaluate the voltage stability and redundancy of the Fan Diagnostic Tool when powered from different sources, including the Lochinvar Control Board, USB, and both. By applying different resistive loads and measuring the voltage, current, and power dissipation, we were able to assess the power delivery system under different levels of stress. Doing this, we were able to identify signs of power stability or instability.  

Across all three power source configurations, the voltage readings remained consistently within a small range, even when going from low load (High resistance) to high load (Low resistance). For example, when using USB power along the voltage drops from 3.309 V (1 kΩ) to 3.036 V (4.7 Ω). This is about an 8.2 % decrease despite a large rise in current. We can see the same concept for only being powered by the Lochinvar Control Board and when being powered by both sources.  

When using the Dual Power configuration (Both USB and Lochinvar Control Board), we can see it had nearly identical results to either power source being used independently. This shows that the redundant power sources work effectively with no evidence of voltage instability when both sources are connected.  

In conclusion, the results show that the Fan Diagnostic Tool maintains stable voltage levels across a range of load conditions and power source configurations. The Dual Power configuration shows that the tool can draw from redundant sources without introducing instability.  

# User Parameter Storage Test

## Purpose and Justification

1. To verify that the user-defined settings can be saved to the onboard SD card.

2. To verify that we can retrieve and load the settings accurately from memory after a power cycle or restart.

3. To maintain data integrity across multiple read/write cycles and to ensure the system resumes operations using the most recently saved data configuration.


## Detailed Procedure

### Setup
***Equipment Needed***
1. SD-Card reader
2. USB to USB Micro cable
3. USB Power (5 Vdc)

**Step 1: Setting up the Power Source** 
1. Connect the USB to USB micro cable between a laptop and the Fan Diagnostic Tool.

**Step 2: Entering Values to Save**
1. Power the Fan Diagnostic Tool with your USB to power the tool.
2. Hit the "Ok" button while "Fan Sim" is selected on the menu.
3. Change the following parameters to the values the user wishes: Max FS, Min FS, PWM Run, PWM Cont, TTF In, TTF De, and PPR.
4. After you have entered your values, scroll down and hit "Ok" while "Save" is selected.

**Step 3: Loading Values**
1. Power the Fan Diagnostic Tool with your USB to power the tool.
2. Hit the "Ok" button while "Fan Sim" is selected on the menu.
3. Scroll down and hit the "Ok" button while "Load" is selected.

**Step 4: Checking Values**
***Saving***  
1. Remove the SD card and place it in an SD card reader.
2. Plug the SD-Card reader with the SD-Card inserted into the reader into your computer.
3. Verify the values are correctly saved.

***Loading***
1. Verify that the values match what was last saved to the SD-Card on the LCD.


## Expected Results

The SD card is expected to accurately save the inputted user parameters, and then correctly read in the most recently saved data. 

## Actual Results

| Saved Parameter                   | Test 1 Values |  Test 2 Values |  Test 3 Values | Test 4 Values |  Test 5 Values |
| :-------------------------------: | :-----------: | :------------: | :------------: | :-----------: | :------------: |
| Max Fan Speed (RPM)               | 3000          | 5000           | 10000          | 1000          | 5000           |
| Min Fan Speed (RPM)               | 1000          | 500            | 2000           | 100           | 250            |
| Min Duty Cycle (%)                | 10            | 20             | 25             | 5             | 30             |
| Continuous Duty Cycle (%)         | 40            | 60             | 60             | 50            | 50             |
| Transient Timing Factor Increase  | 100           | 150            | 200            | 50            | 100            |
| Transient Timing Factor Decrease  | 100           | 50             | 200            | 100           | 175            |
| Pulses Per Revolution             | 2             | 3              | 5              | 2             | 2              |
| **Success / Failed**              | Success       | Success        | Success        | Success       | Success        |

## Interpretation and Conclusions

The purpose of this experiment was to verify that the system can accurately save and read data from the SD Card. The results confirm that the tool can successfully store user data and retrieve the latest saved values. In conclusion, the Fan Diagnostic Tool is capable of saving user-inputted parameters and reading back the most recent configuration after a restart or power cycle.  

# Fan Simulation Test

## Purpose and Justification
1. To verify that the Fan Diagnostic Tool takes in a PWM signal.
2. To verify that the Fan Diagnostic Tool outputs a tachometer signal based on user parameters and the incoming PWM signal.

## Detailed Procedure

### Setup
***Equipment Needed***
1. Function generator
2. Fan Diagnostic Tool
3. Oscilloscope
4. Variable Power supply (24 Vdc, 0.3 A)

**Step 1: Making Connections** 
1. Connect the positive probe of the 24 Vdc power supply to pin one of the first MOLEX connector (MOLEX closest to the SD Card) of the Diagnostic Tool.
2. Connect the negative probe of the 24 Vdc power supply to pin five of the first MOLEX connector (MOLEX closest to the SD Card) of the Diagnostic Tool.
3. Connect the positive of the function generator to the PWM pin and the negative to the ground pin.
4. Connect an oscilloscope probe to the tachometer pin to read the output.
5. Set the function generator to a 20 V square wave with a 3.2 kHz frequency and the corresponding duty cycle.
6. Enter the user parameters in the Diagnostic Tool and hit "RUN" to output a tachometer signal.

## Expected Results
When testing with the 5 sets of parameters in the first table, the corresponding tachometer signal is expected in the second table based on the duty cycle of the PWM signal.

| Parameter                         | Test 1 Values |  Test 2 Values |  Test 3 Values | Test 4 Values |  Test 5 Values |
| :-------------------------------: | :-----------: | :------------: | :------------: | :-----------: | :------------: |
| Max Fan Speed (RPM)               | 3000          | 5000           | 10000          | 1000          | 5000           |
| Min Fan Speed (RPM)               | 1000          | 500            | 2000           | 100           | 250            |
| Min Duty Cycle (%)                | 10            | 20             | 25             | 5             | 30             |
| Continuous Duty Cycle (%)         | 40            | 60             | 60             | 50            | 50             |
| Transient Timing Factor Increase  | 100           | 150            | 200            | 50            | 100            |
| Transient Timing Factor Decrease  | 100           | 50             | 200            | 100           | 175            |
| Pulses Per Revolution             | 2             | 3              | 5              | 2             | 2              |


|             Tachometer                            | Test 1      | Test 2       | Test 3       | Test 4      | Test 5       |
| :------------------------------------------------: | :---------: | :----------: | :----------: | :---------: | :----------: |
| Expected RPM at 15% Duty / Expected Tach Frequency | 0 / 0       | 0 / 0        | 0 / 0        | 100 / 3.3   | 0 / 0        |
| Expected RPM at 30% Duty / Expected Tach Frequency | 1000 / 33.3 | 500 / 25.0   | 2000 / 166.7 | 100 / 3.3   | 250 / 8.3    |
| Expected RPM at 45% Duty / Expected Tach Frequency | 1167 / 38.9 | 500 / 25.0   | 2000 / 166.7 | 100 / 3.3   | 250 / 8.3    |
| Expected RPM at 60% Duty / Expected Tach Frequency | 1667 / 55.6 | 500 / 25.0   | 2000 / 166.7 | 280 / 9.3   | 1200 / 40.0  |
| Expected RPM at 75% Duty / Expected Tach Frequency | 2167 / 72.2 | 2187 / 109.4 | 5000 / 416.7 | 550 / 18.3  | 2625 / 87.5  |
| Expected RPM at 90% Duty / Expected Tach Frequency | 2667 / 88.9 | 3875 / 193.8 | 8000 / 666.7 | 820 / 27.3  | 4050 / 135.0 |
| Expected RPM at 98% Duty / Expected Tach Frequency | 2933 / 97.8 | 4775 / 238.8 | 9600 / 800.0 | 964 / 32.1  | 4810 / 160.3 |

## Actual Results

|                                                    | Test 1 *    | Test 2 *     | Test 3 *     | Test 4 *    | Test 5 *     |
| :------------------------------------------------: | :---------: | :----------: | :----------: | :---------: | :----------: |
| Expected RPM at 15% Duty / Expected Tach Frequency | 0 / 0       | 0 / 0        | 0 / 0        | 100 / 3.3   | 0 / 0        |
| Actual RPM at 15% Duty / Actual Tach Frequency     | 0 / 0       | 0 / 0        | 0 / 0        | 100 / 15.0  | 0 / 0        |
| Expected RPM at 30% Duty / Expected Tach Frequency | 1000 / 33.3 | 500 / 25.0   | 2000 / 166.7 | 100 / 3.3   | 250 / 8.3    |
| Actual RPM at 30% Duty / Actual Tach Frequency     | 1000 / 33.3 | 500 / 25.1   | 2000 / 167.7 | 100 / 15.0  | 250 / 15.0   |
| Expected RPM at 45% Duty / Expected Tach Frequency | 1167 / 38.9 | 500 / 25.0   | 2000 / 166.7 | 100 / 3.3   | 250 / 8.3    |
| Actual RPM at 45% Duty / Actual Tach Frequency     | 1151 / 38.5 | 500 / 25.1   | 2000 / 167.7 | 100 / 15.0  | 250 / 15.0   |
| Expected RPM at 60% Duty / Expected Tach Frequency | 1667 / 55.6 | 500 / 25.0   | 2000 / 166.7 | 280 / 9.3   | 1200 / 40.0  |
| Actual RPM at 60% Duty / Actual Tach Frequency     | 1655 / 55.2 | 500 / 25.1   | 2000 / 167.7 | 274 / 15.0  | 1170 / 39.1  |
| Expected RPM at 75% Duty / Expected Tach Frequency | 2167 / 72.2 | 2187 / 109.4 | 5000 / 416.7 | 550 / 18.3  | 2625 / 87.5  |
| Actual RPM at 75% Duty / Actual Tach Frequency     | 2166 / 72.5 | 2185 / 109.0 | 4995 / 417.3 | 550 / 18.3  | 2625 / 87.7  |
| Expected RPM at 90% Duty / Expected Tach Frequency | 2667 / 88.9 | 3875 / 193.8 | 8000 / 666.7 | 820 / 27.3  | 4050 / 135.0 |
| Actual RPM at 90% Duty / Actual Tach Frequency     | 2709 / 91.1 | 4011 / 201.2 | 8250 / 689.8 | 840 / 28.5  | 4170 / 138.7 |
| Expected RPM at 98% Duty / Expected Tach Frequency | 2933 / 97.8 | 4775 / 238.8 | 9600 / 800.0 | 964 / 32.1  | 4810 / 160.3 |
| Actual RPM at 98% Duty / Actual Tach Frequency     | 2928 / 97.2 | 4750 / 237.8 | 9558 / 798.1 | 962 / 31.8  | 4796 / 159.8 |

***Footnotes***  
*At 90% duty cycle for all tests, we are reading 91.2 % duty cycle due to opto-coupler rounding. (When given a 90% duty cycle signal)*   
*At 98% duty cycle, due to the opto-coupler rounding, we cannot properly measure the signal due to the voltage range on the microcontroller's pins not being a clear high or low level. (Test 3)*   
*For test 4, the minimum hertz that the oscilloscope can read is 15 Hz; therefore, the frequency measurements for duty cycles 15-60% will not be read properly.*


![image](https://github.com/user-attachments/assets/10247939-4d04-448b-82ca-75f33d0d7b7d)


![image](https://github.com/user-attachments/assets/7e067242-1b91-453a-8daa-cffc765fafdf)




## Interpretation and Conclusions
The purpose of this experiment was to ensure that the Fan Diagnostic Tool could perform its minimum required duty of fan simulation. By allowing the user to adjust fan parameters and subsequently input a fan-driving PWM signal, the upper and lower limits of the diagnostic tool can be assessed. In doing so, the tool’s weak points have been identified, and methods to mitigate these issues have been proposed.  

Across almost all the tests, proper results based on the specified user parameters and an input signal of 3.2 kHz with varying duty cycle percentages were achieved. As observed in the tables and graphs above, there was little to no error between the expected signal and the actual response. However, small errors began to appear at higher PWM duty cycles due to the optocouplers not being fast enough. This is because the optocouplers were unable to provide the microcontroller with a suitable voltage range for high and low inputs. According to the microcontroller specifications, high inputs are recognized from 2.7–3.3 V, whereas low inputs are recognized from 0.0–1.0 V. When the PWM duty cycle increased, to around 95%, the microcontroller began receiving a voltage range of 3.3–1.0 V with additional noise. Thus, there is a need for faster optocouplers with larger bandwidth and lower capacitance. Furthermore, observable signals below 15 Hz were unattainable due to limitations of the oscilloscope. Regardless, the tool is expected to output tachometer signals with allowable frequencies as low as 1 Hz.  



# Experimental Analysis Conclusion
The experiments shown above have demonstrated that the Fan Diagnostic Tool can be powered by two different sources (Lochinvar Control Board and USB). Additionally, the tool successfully saves user parameters and accurately reads back the latest saved data. The tool accepts a PWM input and simulates fan behavior based on user-defined parameters, including: max fan speed, minimum fan speed, minimum duty cycle, continuous duty cycle to run, transient timing factor increase, transient timing factor decrease, and pulses per revolution. Therefore, the tool has successfully met the criteria established in the original conceptual design.  


# Statement of Contributions
Layne Bowman helped with all three experiments, along with formatting the Experimental Analysis document.  
Tucker Basham helped with the SD card and fan simulation testing, alongside writing the interpretations and conclusions section for the fan sim.  
Conner Vick was present for some experiments to help troubleshoot if needed.  
Ethan Haynes helped with the fan simulation testing and writing the fan simulation test setup, steps, and expected results.  
Jacob Brewer was present for some experiments to help troubleshoot if needed. Also reviewed this document.
