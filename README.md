# BIIL_MTB-102_GPIO-PDL_LED_Blink_Template
## Lab Objective:
The purpose of this lab is to offer students a hands-on understanding of GPIO (General Purpose Input Output) implementation using the PSoC 6 microcontroller from Cypress (CY8CKIT-062S2-43012 Infineon Board). Upon completing this lab, students will be proficient in initializing GPIOs, controlling GPIO states, and developing basic delay functions.

## Lab Description:
This lab instructs students to program a PSoC 6 microcontroller to manage an LED through a GPIO, employing the GPIO-PDL (Peripheral Driver Library). The task will demonstrate the core functionality of GPIO output.

## The code will:
- Initialize the device and necessary board peripherals.
- Set up a GPIO pin (connected to the LED) as an output utilizing GPIO-PDL functions.
- Establish an endless loop that will:
  - Drive the pin low
  - Wait 250 ms
  - Drive the pin high
  - Wait 250 ms
This sequence will lead to the LED blinking on and off every half-second (250ms on, 250ms off), showcasing an elementary control of GPIO output through GPIO-PDL.
    - *Note: [See the PDL API documentation for the GPIO functions to drive the pin high and low.](https://infineon.github.io/mtb-hal-cat1/html/group__group__hal__gpio.html#nested-classes)*
    - *Note: Use the `Cy_SysLib_Delay` function for the delay.*

## 🔥 Requirements
| Resources                                  | Links                                                                                                  |
|--------------------------------------------|--------------------------------------------------------------------------------------------------------|
| Computer                                   | 💻                                                                                                    |
| ModusToolbox™ software v3.0 or later       | [Link](https://www.infineon.com/modustoolbox)                                                         |
| CY8CKIT-062S2-43012 Infineon Board         | [Link](https://github.com/Advance-Innovation-Centre-AIC/BIIL_MTB-100_Hello_World_and_LED_Blinking_Programming_Template/assets/88732241/0215501d-b774-4045-8e64-ef49e28d8404) |
| Technical Report | [dropbox](https://www.dropbox.com/scl/fi/amaxc94pte0ut2i1r5ewx/Technical-Report-Lab00.paper?rlkey=b3xm3vrerz9xgv1glb30cvy9z&dl=0)

## 🚩 Let start
- 👉  Open Eclipse IDE ModusToolbox               
![image](https://github.com/Advance-Innovation-Centre-AIC/BIIL_MTB-100_Hello_World_and_LED_Blinking_Programming_Template/assets/88732241/276b5ee3-7752-488c-baa7-3b55f6615b27)                 

- 👉  Select board  
  
![image](https://github.com/Advance-Innovation-Centre-AIC/BIIL_MTB-100_Hello_World_and_LED_Blinking_Programming_Template/assets/88732241/df637b74-1bee-4c0c-9bdc-4b70d7f0cee8)

- 👉  Select Application      
![image](https://github.com/Advance-Innovation-Centre-AIC/BIIL_MTB-102_GPIO-PDL_LED_Blink_Template/assets/88732241/662a9e38-6f1b-4558-b8b7-49ed8cc1d42b)

- 👉  Device Configuration
  ![image](https://github.com/Advance-Innovation-Centre-AIC/BIIL_MTB-102_GPIO-PDL_LED_Blink_Template/assets/88732241/778447ee-6e93-4b91-a038-be23573b82f4)
  - Find Pin and search for `led` then select the `P1[5]`      
    ![image](https://github.com/Advance-Innovation-Centre-AIC/BIIL_MTB-102_GPIO-PDL_LED_Blink_Template/assets/88732241/5f516394-f05e-43e3-b0f7-2eb7daf2d8a6)
  -  Set the pin's `Drive Mode` parameter to `Strong Drive Input buffer off`.      
![image](https://github.com/Advance-Innovation-Centre-AIC/BIIL_MTB-102_GPIO-PDL_LED_Blink_Template/assets/88732241/a3fe848a-4396-4788-8ead-0afce0b0ddbd)
  - Coding: Open the main.c file and add the following code to the main() function.
  ```
  for (;;)
    {
        /* Drive the USER LED pin low (LED on) */
      	Cy_GPIO_Set(CYBSP_USER_LED_PORT, CYBSP_USER_LED_NUM);
      
        /* Wait 250 ms */
    	Cy_SysLib_Delay(250U);
    
        /* Drive the USER LED pin high (LED off) */
    	Cy_GPIO_Clr(CYBSP_USER_LED_PORT, CYBSP_USER_LED_NUM);
    
        /* Wait 250 ms */
	Cy_SysLib_Delay(250U);
    }
  ```
    - `for (;;`) This line starts an infinite loop. The code contained within the curly braces {} will repeat indefinitely.
    - `Cy_GPIO_Set(CYBSP_USER_LED_PORT, CYBSP_USER_LED_NUM);` sets the GPIO pin specified by CYBSP_USER_LED_PORT and CYBSP_USER_LED_NUM to a high state, turning on the LED connected to that pin.
    - `Cy_SysLib_Delay(250U);` introduces a delay of 250 milliseconds, causing a pause in the execution of the program. This delay is implemented using a system library function.
    - `Cy_GPIO_Clr(CYBSP_USER_LED_PORT, CYBSP_USER_LED_NUM);` clears (sets to a low state) the GPIO pin specified by CYBSP_USER_LED_PORT and CYBSP_USER_LED_NUM, turning off the LED connected to that pin.
    - Another `Cy_SysLib_Delay(250U);` introduces another delay of 250 milliseconds.
=> This sequence of code turns on the LED, waits for 250 milliseconds, turns off the LED, and then waits for another 250 milliseconds. The cycle then repeats, creating a blinking effect for the LED.
- 👉  Build the Application
- 👉  Launching the Application
    - Before launching the program to the board, make sure that you have already connected the board to the computer through USB cable.        
![image](https://github.com/Advance-Innovation-Centre-AIC/BIIL_MTB-100_Hello_World_and_LED_Blinking_Programming_Template/assets/88732241/7a6bb6ef-cb63-4613-98a1-42f9617ad724)
  - Launching Program    
    ![image](https://github.com/Advance-Innovation-Centre-AIC/BIIL_MTB-102_GPIO-PDL_LED_Blink_Template/assets/88732241/efee18cb-0e32-4d4e-93d1-6dd0ee609140)

- 👉  Check the Result
  ![106650](https://github.com/Advance-Innovation-Centre-AIC/BIIL_MTB-102_GPIO-PDL_LED_Blink_Template/assets/88732241/7d1bbd14-4157-4f9c-823d-e8f147dfea2e)


### 🎉  Congratulations! You can now complete Lab102

## Supported toolchains (make variable 'TOOLCHAIN')

- GNU Arm&reg; embedded compiler v10.3.1 (`GCC_ARM`) - Default value of `TOOLCHAIN`
- Arm&reg; compiler v6.16 (`ARM`)
- IAR C/C++ compiler v9.30.1 (`IAR`)

## Supported kits (make variable 'TARGET')

- [PSoC&trade; 62S2 Wi-Fi Bluetooth&reg; pioneer kit](https://www.infineon.com/CY8CKIT-062S2-43012) (`CY8CKIT-062S2-43012`)
- [PSoC&trade; 62S1 Wi-Fi Bluetooth&reg; pioneer kit](https://www.infineon.com/CYW9P62S1-43438EVB-01) (`CYW9P62S1-43438EVB-01`)
- [PSoC&trade; 62S1 Wi-Fi Bluetooth&reg; pioneer kit](https://www.infineon.com/CYW9P62S1-43012EVB-01) (`CYW9P62S1-43012EVB-01`)
- [PSoC&trade; 62S3 Wi-Fi Bluetooth&reg; prototyping kit](https://www.infineon.com/CY8CPROTO-062S3-4343W) (`CY8CPROTO-062S3-4343W`)


## Related resources
Resources  | Links
-----------|----------------------------------
ModusToolbox™ Software Training | [link](https://www.dropbox.com/sh/waj898o4o8eccx0/AAB3hBBaIQo2OvJ5-fubGJIha/training-modustoolbox-level1-getting-started-master/Manual/Ch2-Tools.pdf?dl=0)



## Other resources

Infineon provides a wealth of data at www.infineon.com to help you select the right device, and quickly and effectively integrate it into your design.


## Document history

Document title: *BILL_MTB-101* – *GPIO LED Blink Template*

 Version | Description of change
 ------- | ---------------------
 1.0.0   | Lab101: Introduction to GPIO control with PSoC 6, featuring an LED blinking .


## Authors:
- *Assoc. Prof. Wiroon Sriborrirux*
- *Mr. Sriengchhun Chheang*
- *Mr. Sabol Socare*
<br>

<br>

---------------------------------------------------------

© BDH Corporation, 2022-2023
