# Function of the Subsystem
The goal of this subsystem is to display the options available to the user, display data relevant to the user, and to show the user's inputs do what they intended them to do.

# Specifications and Constraints
## Specifications
1. The display shall show the PWM signal.  
2. The display shall show the tachometer signal.  
3. The display shall show the different options for the user interface.  
4. The display shall show the correct operations based on the user input.  
  
## Constraints
1. The display's menu system will be able to be viewed with relative ease.  

This constraint is incredibly important when considering display choice. If the text on screen is hard to read, everything else is secondary.  
# Overview of Proposed Solution
The proposed solution for this subsystem is the use of a character LCD. This will be adequate to show the PWM and TACH signals. It will easily be able to show all the options available to the user and reflect the user's input appropriately.  

# Interfacing with Other Subsystems
The Display will interface directly with the microcontroller through a parallel serial connection (SPI). This will allow the microcontroller to send the required information to the display, so the display can show the information to the user. It will also require a connection to the power subsystem in order for the display to turn on and be used.  

# Buildable Schematic
![image](https://github.com/user-attachments/assets/514f43c3-295f-49f8-9994-b7b562f46038)
  

# PCB Layout
![image](https://github.com/user-attachments/assets/a5741e4c-52d9-4d9b-85f0-4c882c560005)  

![image](https://github.com/user-attachments/assets/5a6e39ef-8f56-4d20-a397-60724bc26a80)  
# BOM
| Manufacteror | Manufacteror Part Number | Distributor | Distributor Part Number | Quantity | Cost  | URL  | Component Name  |
| :---         | :---:                    | :---:       | :---:                   | :---:    | :---: | :--- | :--- |
| Newhaven Display Intl | NHD-0420H1Z-FL-GBW-33V3 | Digikey | NHD-0420H1Z-FL-GBW-33V3-ND | 1 | $20.30 | https://www.digikey.com/en/products/detail/newhaven-display-intl/NHD-0420H1Z-FL-GBW-33V3/2773594 | LCD1 |  
| YAGEO | RSF100JB-73-2R | Digikey | 13-RSF100JB-73-2R-ND | 1 | $0.29 | https://www.digikey.com/en/products/detail/yageo/RSF100JB-73-2R/18018 | R18 |  
| YAGEO | FMP100JR-52-100R | Digikey | 100WCT-ND | 1 | $0.20 | https://www.digikey.com/en/products/detail/yageo/FMP100JR-52-100R/2058569?s=N4IgTCBcDaIGIFkAKBGADGgUgJQLQFYxd01sQBdAXyA | R19 |  
TOTAL COST = $20.79

# Analysis
The development of the Display subsystem was a very simple matter. Firstly, the screen was chosen such that more than one row of text could be shown at the same time, but not too many rows either. This balanced approach insured that the user would not be annoyed by how little they could see at once, while also not too big as to be wasteful. Next, the screen needed to have a backlight and adjustable contrast. This would insure that text will be able to be viewed in the intended setting.  
  
The Display that fulfilled these design decisions was the HD-0420H1Z-FL-GBW-33V3. It is plenty large at 79mm by 36mm. It can display 4 lines 20 characters each [1].  
  
For the primary mode of operation, Fan Simulation, about 8 lines are needed for the menu. This means that the user would only have to go to one other screen to see all options. If this seems odd later on, other menu setups could be created such that no screen scroll would be necassary, but the current seems to be ideal. Through the microcontroller and connected buttons, user inputs will easily be reflected upon the display. Therefore, the selected screen will be able to show all desired information and user input, thus meeting all constraints and specfications.  
# References
[1] Newhaven Display International, Inc., “Character Liquid Crystal Display Module.” [Online]. Available: https://newhavendisplay.com/content/specs/NHD-0420H1Z-FL-GBW-33V3.pdf (accessed Nov. 24, 2024).
