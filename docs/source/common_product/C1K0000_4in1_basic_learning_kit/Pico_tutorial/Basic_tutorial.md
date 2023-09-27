# Basic_tutorial  
This tutorial is based on the [C1K0001 4in1 basic learning kit](../../C1K0000_4in1_basic_learning_kit/C1K0000_4in1_basic_learning_kit.md).     

Learn simple programming syntax based on the Pico board, and learn the most comprehensive Python basics in the fastest way.     

## What is MicroPython?
MicroPython is a full implementation of the Python 3 programming language that runs directly on embedded hardware like Raspberry Pi Pico. You get an interactive prompt (the REPL) to execute commands immediately via USB Serial, and a built-in filesystem. The Pico port of MicroPython includes modules for accessing low-level chip-specific hardware.      
1. The [MicroPython](https://micropython.org/)
2. The [MicroPython Forums](https://forum.micropython.org/)  
3. MicroPython is a language derived from Python, so it is recommended to learn [Python](https://docs.python.org/3/reference/index.html) first.   

## Prepared knowledge    
**Learn about:** [**Basic learning shield**](../../../arduino/A1E0000_basic_learning_shield/A1E0000_basic_learning_shield.md).  

**Learn about:** [**3in1 basic learning shield**](../../../common_product/C1E0000_3in1_basic_learning_shield/C1E0000_3in1_basic_learning_shield.md).  

**Pico and Thonny basics:**     
If you don't have Pico and Thonny basics, you can follow the link to learn the basics: [Click Me](../../../raspberry/R1D0001_raspberry_pico/R1D0001_raspberry_pico.md)    

**Learn about:** [**MicroPython for Pico**](https://docs.micropython.org/en/latest/rp2/quickref.html).  

**Download sample code:**    
Please download the sample code on Github: <https://github.com/Mosiwi/Mosiwi-basic-learning-kit> 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/1img.png)    
Unzip the file downloaded above, and the file in the "**pico->microPython**" folder is the sample code.       

## Wiring diagram      
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/2img.png)    

## Basic_example Blink      
**Objective:**     
1. Open the example code.     
2. Upload and run code.   
3. Verify that the pico motherboard works.        
4. Digital output pin.       

**Demonstration:**       
Open the "**blink\.py**" file as follows:     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/3img.png)    

Run the code online: (The code is not saved in pico and is not executed after repowering.)       
Make sure your Raspberry PI Pico's USB is plugged into your computer's USB via a usb cable, then click on "Python" and the version number in the bottom right corner of the Thonny window, then select "**MicroPython(Raspberry PI Pico)". COMx** ".      
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/4img.png)    

After running the code, the LED on the pico board lights up every 1 second:      
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/5img.png)    

Run the code offline: (The code is stored in pico, and the code in pico is automatically executed after being powered on.)     
Enter the code in the main panel, then click on the "**Save**" or "**File->Save as ...**" menu. Thonny will present you with a popup, click on "**Raspberry Pi Pico**" and enter "**main\.py**" to save the code to the **Raspberry Pi Pico**.  
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/6img.png)    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/7img.png)    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/8img.png)    

| <span style="color: rgb(255, 76, 65);">Note</span>|  
|  :-- |
|If you "save a file to the device" and give it the special name **main\.py**, then MicroPython starts running that script as soon as power is supplied to Raspberry Pi Pico in the future. |    

**Code analysis:**                 
Pins and GPIO: [Click me](https://docs.micropython.org/en/latest/rp2/quickref.html#pins-and-gpio)      
Delay and timing: [Click me](https://docs.micropython.org/en/latest/rp2/quickref.html#delay-and-timing)           

Code comments:      
```
Syntax:    
code block      # Comment text

In the sample code:    
import time     # Importing the time class
```

import:     
```
Syntax:
import modulename   

In the sample code:    
import time     # Importing the time class
```

from xxx import xxx:    
```
Syntax:
from modelname import member     

In the sample code: 
from machine import Pin     # Import the Pin class from the machine module.    
```

while loop:        
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/22img.png)    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/27img.gif)    

```
Syntax:
while (condition):
    conditional code
    ...

or 

while condition:
    conditional code
    ... 

Parameters:
condition: Boolean expression whose result is true or false.   

In the sample code:   
while(1):                    # An infinite loop statement.
    button_value = Button.value()  # Read the key value
    if button_value == 1:          # Check whether the value of the key is 1, if so, turn off the LED.
        G_LED.off()                # Set pin to "off" (low) level
    else:                          # If the value of the key is not 1, the LED is turned on.
        G_LED.on()                 # Set pin to "on" (high) level  
```



## Example_1 Button      
**Objective:**     
1. What is button?     
2. What is resistance? 

**Pins to be used:**     
1. Button: GP21 
2. LED: GP25

**Schematic diagram:**       
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/9img.png)    

**Open the example code: "button\.py"**     
1. Open the sample code using the methods in **"[Basic_example](./python_tutorial.md#basic-example-blink)"**.     
2. Run the example code online.      

**Example code phenomena:**         
After uploads the code, the led on the Pico is always off, and if the "Button" on the extension board is pressed, the LED is turned on.     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/10img.png)    

**FQA:**    
(1) What is a button?   
The key is A press switch, as shown in the following figure, A and B, C and D are directly connected inside, when no press, AB and CD are not connected, when the key is pressed, AB and CD are connected.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/11img.png)    

(2) What is resistance?
The resistance of a conductor to the current is called its resistance. The greater the resistance of the conductor, the greater the obstruction effect of the conductor on the current. The resistance of a conductor is usually represented by the R symbol, the unit of resistance is ohms, and the symbol is Ω.     

Resistance is defined by the ratio of the voltage U at the two ends of the conductor to the current I passing through the conductor:      
$$R=U/I$$     

Color ring resistor uses different colors to show the resistance and accuracy, as shown below:    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/23img.png)    

**Code analysis:**            
Variable：          
Variables come from mathematics and are abstract concepts in computer language that can store calculation results or represent values. Variables can be accessed by variable name.         
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/25img.png)    

Variable naming rules:      
1. Variable names can contain only alphanumeric characters and underscores (A-z, 0-9, and _).          
2. Variable names must start with a letter or underscore character Variable names cannot start with numbers.         
3. Variable names are case-sensitive ("age", "Age", and "AGE" are three different variables).            

```
Syntax:    
VariableName = data 

int variable:  
var = 10    

long variable:  
var = 51924361L   

float variable:    
var = 10.1  

complex variable:   
var = 3.14j   

string variable:    
var = "mosiwi"  

list variable:   
var = [ 'mosiwi', 786 , 2.23, 'john', 70.2 ]   

tuple variable:    
var = ( 'mosiwi', 786 , 2.23, 'john', 70.2 )  

dictionary variable:    
var = {'name': 'mosiwi','code':6734, 'dept': 'sales'}       


In the sample code:
button_value = Button.value()  # Read the key value

```


Judgment statement: 
if ... else ...         
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/24img.png)    

```
Syntax:
if condition: 
    conditional code
    ...  
else: 
    conditional code
    ...   

In the sample code: 
if button_value == 1:          # Check whether the value of the key is 1, if so, turn off the LED.
    G_LED.off()                # Set pin to "off" (low) level
else:                          # If the value of the key is not 1, the LED is turned on.
    G_LED.on()                 # Set pin to "on" (high) level
```

Additional knowledge: if    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/28img.jpg)    

```
Syntax:
if condition: 
    conditional code   

example:   
if a > 2:   
    b = 10
```


## Example_2 Buzzer   
**Objective:**     
1. What is PWM output?      
2. What is buzzer?    

**Pins to be used:**   
1. Buzzer: GP6  

**Schematic diagram:**       
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/12img.png)    

**Open the example code: "buzzer\.py"**     
1. Open the sample code using the methods in **"[Basic_example](./python_tutorial.md#basic-example-blink)"**.     
2. Run the example code online. 

**Example code phenomena:**         
After uploading the code, the buzzer on the expansion board will keep beeping with a fixed frequency and different volumes.       
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/13img.png)    
<span style="color: rgb(255, 76, 65);">Note: A passive buzzer is used on the extension board.</span>        

**FQA:**   
(1) What is PWM output?      
PWM, called pulse width modulation signal, is a square wave signal with fixed frequency and variable duty cycle time. In the figure below, T is the cycle time, which is fixed; A is high level (Pico high level is 3.3V); B is low level (Pico high level is 0V); The level width of A and B in the period T time is changeable, the longer the pulse time of the high level, the larger the average voltage value, and the smaller the vice versa.          
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/14img.png)    
Note: T = A + B     

![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/15img.png)         
See more: [PWM for Pico](https://docs.micropython.org/en/latest/rp2/quickref.html#pwm-pulse-width-modulation)     

(2) What is buzzer?    
See: [Buzzer](../Arduino_tutorial/Intermediate_tutorial.md#chapter5-buzzer)    

**Code analysis:**          
range() function:   
```
Syntax:
range(stop)
range(start, stop[, step])  

Parameters:
start -> The value of the start parameter (or 0 if the parameter was not supplied)
stop  -> The value of the stop parameter
step  -> The value of the step parameter (or 1 if the parameter was not supplied)

Range examples:
>>> list(range(10))
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

>>> list(range(1, 11))
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

>>> list(range(0, 30, 5))
[0, 5, 10, 15, 20, 25]

>>> list(range(0, 10, 3))
[0, 3, 6, 9]

>>> list(range(0, -10, -1))
[0, -1, -2, -3, -4, -5, -6, -7, -8, -9]

>>> list(range(0))
[]

>>> list(range(1, 0))
[]

```

for loop:    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/26img.jpg)    

```
Syntax:   

for <variable> in <sequence>:
    <statements>
else:
    <statements>

In the sample code:  
for i in range(0, 65536):     # The loop executes the next two statements 65,536 times.
    time.sleep_us(50)         # Sleep for 50 microseconds
    buzzer.duty_u16(i)        # Set duty cycle of the PWM, 0 to 65535
```


## Example_3 Potentiometer   
**Objective:**     
1. What is potentiometer?         
2. What is ADC?   

**Pins to be used:**   
1. Potentiometer: GP28_A2    

**Schematic diagram:**       
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/16img.png)    

**Open the example code: "potentiometer\.py"**     
1. Open the sample code using the methods in **"[Basic_example](./python_tutorial.md#basic-example-blink)"**.     
2. Run the example code online. 

**Example code phenomena:**         
Push the potentiometer up and down, and the terminal prints the corresponding analog value and voltage value.          
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/17img.png)    

**FQA:**   
(1) What is potentiometer?    
Sliding potentiometer is a resistance element with adjustable resistance value and three leading ends. It usually consists of a resistive body and a removable brush. When the brush moves along the resistance body, the resistance value or voltage that is related to the displacement can be obtained at the output end.      
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/18img.png)    

(2) What is ADC (Analog to Digital Converter)? 
See: [ADC for Pico](https://docs.micropython.org/en/latest/rp2/quickref.html#adc-analog-to-digital-conversion)       

**Code analysis:**         
print function: [Click me](https://docs.python.org/3/library/functions.html#print)        


## Example_4 Timer   
**Objective:**     
1. What is timer?           

**Pins to be used:**   
1. Red RGB LED: GP8             

**Schematic diagram:**       
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/19img.png)    

**Open the example code: "timer\.py"**     
1. Open the sample code using the methods in **"[Basic_example](./python_tutorial.md#basic-example-blink)"**.     
2. Run the example code online. 

**Example code phenomena:**            
The red LED on the expansion board shines once every 1 seconds.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/20img.png)    

**FQA:**   
(1) What is timer?     
A timer is equivalent to an alarm clock, which can set a time, generate a signal (equivalent to an interrupt) at every set time, and perform another thing when the signal is generated.      

When the timer count reaches the set time, an interrupt signal is generated for the processor to execute a short program.      
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/Basic_tutorial/21img.png)    

See: [Timer for Pico](https://docs.micropython.org/en/latest/rp2/quickref.html#timers)       

**Code analysis:**    
To use a global variable in a function:       
```
Syntax:
global  VariableName  

In the sample code:
ledstate = 0;                # Define a global variable

def mycallback(t):           # Timed interrupt function
    global ledstate          # Use the "global" keyword to declare that the variable is global, otherwise it is local.
    ledstate = 1 - ledstate  # The global variable ledstate is either 0 or 1. 
    R_LED.value(ledstate)    # Turn on or off the LED.

```

pass:    
Do not do anything, generally used as placeholder statements.     
```
Syntax:   
loop statement:    
    pass

In the sample code:  
while True:                 # Always empty loop
    pass
```


## Example_5 Watchdog      
**Objective:**     
1. What is Watchdog?             

**Open the example code: "wdt\.py"**     
1. Open the sample code using the methods in **"[Basic_example](./python_tutorial.md#basic-example-blink)"**.     
2. Run the example code online. 

**Example code phenomena:**         
At the beginning of the program, let the LED on the Pico board blink once, and then set the dog feeding time of the watchdog to within 30 seconds, so that the program will always loop empty. Because the dog was not fed in time, the Pico reset every 30 seconds, and the LED on the Pico class flickered every time it was reset.             
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/5img.png)      
<span style="color: rgb(255, 76, 65);">Note: When practicing, don't set the dog feed time so short that the Pico keeps resetting and can't communicate with Thonny. At this point you have to [re-burn the UF2 file](../../../raspberry/R1D0001_raspberry_pico/R1D0001_raspberry_pico.md#using-uicropython-in-thonny).</span>    

**FQA:**   
(1) What is Watchdog?    
The watchdog is also a timer, and the set time must be refreshed within the set time, otherwise it will cause the chip to reset. Use this function to prevent the program from running incorrectly or out of control.      
See: [WDT for Pico](https://docs.micropython.org/en/latest/rp2/quickref.html#wdt-watchdog-timer)           


**End!**    

