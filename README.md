+
# EXPERIMENT--04-INTERFACING-AN16X2-LCD-DISPLAY-WITH-ARM AND DISPLAY STRING


 ## Aim: To Interface a 16X2 LCD display to ARM controller  , and simulate it in Proteus 
## Components required: STM32 CUBE IDE, Proteus 8 simulator .
## Theory 
The full form of an ARM is an advanced reduced instruction set computer (RISC) machine, and it is a 32-bit processor architecture expanded by ARM holdings. The applications of an ARM processor include several microcontrollers as well as processors. The architecture of an ARM processor was licensed by many corporations for designing ARM processor-based SoC products and CPUs. This allows the corporations to manufacture their products using ARM architecture. Likewise, all main semiconductor companies will make ARM-based SOCs such as Samsung, Atmel, TI etc.

What is an ARM7 Processor?
ARM7 processor is commonly used in embedded system applications. Also, it is a balance among classic as well as new-Cortex sequence. This processor is tremendous in finding the resources existing on the internet with excellence documentation offered by NXP Semiconductors. It suits completely for an apprentice to obtain in detail hardware & software design implementation.
 STM32F401xB STM32F401xC ARM® Cortex®-M4 32b MCU+FPU, 105 DMIPS, 256KB Flash/64KB RAM, 11 TIMs, 1 ADC, 11 comm.
interfaces Datasheet - production data Features
• Core: ARM® 32-bit Cortex®-M4 CPU with FPU, Adaptive real-time accelerator (ART Accelerator™) allowing 0-wait state execution from Flash memory, frequency up to 84 MHz, memory protection unit, 105 DMIPS/ 1.
25 DMIPS/MHz (Dhrystone 2.
1), and DSP instructions
• Memories – Up to 256 Kbytes of Flash memory – Up to 64 Kbytes of SRAM


   ## LCD 16X2 
   16×2 LCD is named so because; it has 16 Columns and 2 Rows. There are a lot of combinations available like,
   8×1, 8×2, 10×2, 16×1, etc. But the most used one is the 16*2 LCD, hence we are using it here.

All the above mentioned LCD display will have 16 Pins and the programming approach is also the same and hence the choice is left to you. 
Below is the Pinout and Pin Description of 16x2 LCD Module:
4-bit and 8-bit Mode of LCD:

The LCD can work in two different modes, namely the 4-bit mode and the 8-bit mode. In 4 bit mode we send the data nibble by nibble, first upper nibble and then lower nibble. For those of you who don’t know what a nibble is: a nibble is a group of four bits, so the lower four bits (D0-D3) of a byte form the lower nibble while the upper four bits (D4-D7) of a byte form the higher nibble. This enables us to send 8 bit data.

Whereas in 8 bit mode we can send the 8-bit data directly in one stroke since we use all the 8 data lines.

 8-bit mode is faster and flawless than 4-bit mode. But the major drawback is that it needs 8 data lines connected to the microcontroller. This will make us run out of I/O pins on our MCU, so 4-bit mode is widely used. No control pins are used to set these modes. 
 LCD Commands:

There are some preset commands instructions in LCD, which we need to send to LCD through some microcontroller. Some important command instructions are given below:

Hex Code

Command to LCD Instruction Register

0F

LCD ON, cursor ON

01

Clear display screen

02

Return home

04

Decrement cursor (shift cursor to left)

06

Increment cursor (shift cursor to right)

05

Shift display right

07

Shift display left

0E

Display ON, cursor blinking

80

Force cursor to beginning of first line

C0

Force cursor to beginning of second line

38

2 lines and 5×7 matrix

83

Cursor line 1 position 3

3C

Activate second line

08

Display OFF, cursor OFF

C1

Jump to second line, position 1

OC

Display ON, cursor OFF

C1

Jump to second line, position 1

C2

Jump to second line, position 2
 
## Procedure:
 1. click on STM 32 CUBE IDE, the following screen will appear 
  2. click on FILE, click on new stm 32 project 
3. select the target to be programmed  as shown below and click on next 
4.select the program name 
5. corresponding ioc file will be generated automatically 
6.select the appropriate pins as gipo, in or out, USART or required options and configure 
7.click on cntrl+S , automaticall C program will be generated 
8. edit the program and as per required 
9. Add necessary library files of LCD 16x2 , write the program and use project and build  
10. once the project is bulild 
11. click on debug option 
12.  Creating Proteus project and running the simulation
We are now at the last part of step by step guide on how to simulate STM32 project in Proteus.

13. Create a new Proteus project and place STM32F40xx i.e. the same MCU for which the project was created in STM32Cube IDE. 
14. After creation of the circuit as per requirement as shown below 
15. click on debug and simulate using simulation as shown below 

## CIRCUIT DIAGRAM 
![image](https://user-images.githubusercontent.com/36288975/233857974-bda6200e-4f88-4e7b-b189-4da80210fa23.png)


## STM 32 CUBE PROGRAM :
```
Developed By : Thirukaalathessvarar S
Reg.no: 212222230161
```
```
#include "main.h"
#include"lcd.h"

int main(void)
{
  
  HAL_Init();

  
  MX_GPIO_Init();
 
  Lcd_PortType ports[] = { GPIOA, GPIOA, GPIOA, GPIOA };
  Lcd_PinType pins[] = {GPIO_PIN_3, GPIO_PIN_2, GPIO_PIN_1, GPIO_PIN_0};
  Lcd_HandleTypeDef lcd;
  lcd = Lcd_create(ports, pins, GPIOB, GPIO_PIN_0, GPIOB, GPIO_PIN_1, LCD_4_BIT_MODE);
  Lcd_cursor(&lcd, 0,1);
  Lcd_string(&lcd, "DEPT- AI&DS");
 
  while (1)
  {
    
  }
 }
    

  if (HAL_RCC_ClockConfig(&RCC_ClkInitStruct, FLASH_LATENCY_0) != HAL_OK)
  {
    Error_Handler();
  }
}


}
void Error_Handler(void)
{
 
  __disable_irq();
  while (1)
  {
  }

}
```

## Output screen shots of proteus  :
![WhatsApp Image 2023-06-06 at 9 12 19 PM](https://github.com/Thirukaalathessvarar-S/EXPERIMENT--04-INTERFACING-AN16X2-LCD-DISPLAY-WITH-ARM-/assets/121166390/5acdb8e0-6b48-48af-a0d0-8fd1282a6254)
 
## Proteus Layout
![image](https://github.com/Thirukaalathessvarar-S/EXPERIMENT--04-INTERFACING-AN16X2-LCD-DISPLAY-WITH-ARM-/assets/121166390/374a2009-5d79-4c87-aec9-30f61e44af4b)

## Result :
Interfacing a digital output and digital input  with ARM microcontroller are simulated in proteus and the results are verified.

