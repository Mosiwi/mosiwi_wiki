# Based tutorial   
Learn simple programming syntax based on the UNO board, and learn the most comprehensive Arduino basics in the fastest way.     

## Previous preparation   
1. Install the [**Arduino IDE**](../../../arduino/arduino_ide/arduino_ide.md).     
2. Basic operation of the [**Arduino UNO R3**](../../../arduino/A1D0000_uno_r3/A1D0000_uno_r3.md) motherboard.    
3. Learn about [**3in1 basic learning shield**](../../../arduino/A1E0000_basic_learning_shield/A1E0000_basic_learning_shield.md).  

## Chapter_1 Blink    

**Curriculum question:**     
1. What is LED light ?     
2. setup() and loop() functions in Arduino program.    
3. How to set up and use digital outlet?   
4. How to use the delay() delay function?  
5. How to use the comment symbols in the code: //, /* ... */    

**Program flow diagram:**   
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Basic_tutorial/2img.png)     

**Open the example code: "1.0.0_Blink"**     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Basic_tutorial/1img.png)    
<span style="color: rgb(255, 76, 65);">Note: All the sample code in the following sections is opened in the same way as in the figure above.</span>     

**Example code phenomena:**    
The RGB LED on the expansion board emits a red light every 1 second.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Basic_tutorial/4img.png)    

**FAQ:**
(1) What is LED light?    
Leds are also known as light-emitting diodes. It has positive and negative poles, generally the shorter pin or the pin near the gap is the negative pole, and the other end is the positive pole. Only when the forward current is connected, the LED light will be lit. Its current is generally required to be about 5-15ma, so resistors are often used in series with leds to achieve current limiting.     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Basic_tutorial/3img.png)     

(2) "setup()" and "loop()" functions in Arduino program.
"setup()" and "loop()" are two functions defined by Arduino. All Arduino programs have and only have one "setup()" and "loop()" functions. When the arduino program is running, the code inside "setup()" is executed first, and then the code inside "loop()" is looped.     

(3) How to set the I/O port to digital output mode?     
Pins 2-13 on the UNO board can be set to digital output mode to output logic "0" (low level, 0V) and logic "1" (high level, 5V) on the pin.     
```
Syntax:    
pinMode(pin, mode);   

Parameters:  
pin: The pin number of the arduino motherboard (2-13 for UNO).   
mode: INPUT, OUTPUT, or INPUT_PULLUP.   

INPUT: Digital input mode.    
OUTPUT: Digital output mode.     
INPUT_PULLUP: Digital input mode with pull resistance.        
```

When mode is set to OUTPUT mode, use the following statement to make the IO port output high or low:    
```
Syntax:
digitalWrite(pin, value);

Parameters:
pin: The pin number of the arduino motherboard (2-13 for UNO).
value: HIGH or LOW.

"HIGH" : High level, digital value is 1, voltage value is 5V.
LOW: Low level, digital value is 0, voltage value is 0V.   
```
(4) How to use the delay() function?    
The delay() function is used to pause the program for a period of time, which can be customized.    
```
Syntax:
delay(ms);

Parameters:
ms: The value ranges from 0 to 4294967295, in milliseconds.
```

(5) How to use the comment symbols in the code: //, /\*...\*/
When we want to parse the function and function of the code with text, we need to use the single-line comment (//) and block comment symbols(/\*...\*/). The text after the comment does not participate in the code running, but is only used to parse the code.     
```
Syntax:
// Text content that needs to be commented

/* Text content to be commented */

/ *
Text content to be commented
Text content to be commented
* /
```

## Chapter_2 Button    

**Curriculum question:**     
(1) What is a button?    
(2) What are variables, byte variables and global variables?    
(3) How to use the assignment operator: =       
(4) How to set up and use the digital input port?    
(5) How to use relational operators: ==,! =   
(6) How to use the judgment statement: if        

**Program flow diagram:**   
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Basic_tutorial/5img.png)     

**Open the example code: "1.1.0_Button"**     
Open the sample code using the methods in **"Chapter_1"**.   

**Example code phenomena:**   
When the "OK" key is pressed, the red RGB LED lights up, otherwise the RGB LED does not light up.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Basic_tutorial/6img.png)     

**FAQ:**
(1) What is a button?   
The key is A press switch, as shown in the following figure, A and B, C and D are directly connected inside, when no press, AB and CD are not connected, when the key is pressed, AB and CD are connected.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Basic_tutorial/7img.png)     

(2) What are variables, byte variables and global variables?   
Variables come from mathematics and are abstract concepts in computer language that can store calculation results or represent values. Variables can be accessed by variable name.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Basic_tutorial/8img.png)     

**byte** variable is a variable defined by the arduino programming language, and its value ranges from 0 to 255.   
```  
Syntax:
byte var = val;

Parameters:
var: Parameter name.
val: The value assigned to the var.
```

**Global variable** applies to the entire program and is defined outside the stup() and loop() functions, and not inside other functions. The "buttonPin", "ledPin", and "buttonState" variables defined in the sample code can be used in stup() and loop() functions, or in other functions.    
```
Syntax: 
byte buttonPin;          
byte ledPin;          
byte buttonState; 
```

(3) How to use the assignment operator?
The assignment symbol is "=", note that this symbol is not an equal sign, as in the example:    
```
Syntax: 
buttonPin   = 2;    
ledPin      = 5;       
buttonState = 0; 
```

(4) How to set up and use the digital input port?    
Pins 2-13 on the UNO board can be set to digital input mode to read the logic "0" (low level, 0V) and "1" (high level, 5V) of the pins.     

Set the pin to digital input mode.      
```
Syntax:    
pinMode(pin, INPUT);   

Parameters:  
pin: The pin number of the arduino motherboard (2-13 for UNO).           
```
Read the value on the pin:   
```
Syntax:
digitalRead(pin);

Parameters:
pin: The pin number of the arduino board (2-13 for UNO).

Return value:
HIGH or LOW.

HIGH: High level. The digital value is 1, and the voltage value is greater than 3V.
LOW: Low level. The digital value is 0 and the voltage is less than 1.5V.
```

(5) How to use relational operators: ==,! = 
The equal and unequal relation operators are "==" and "!= ". Commonly used with judging conditions true and false. If variable A is assigned 10 and variable B is assigned 20, then:    
| symbol | annotation | example |    
| :--: | :--: | :--: |    
| == | Check whether the values of the two variables are equal. If equal, the condition is true, otherwise the condition is false. | (A == B) is false |   
| != | Check whether the values of the two variables are equal. If equal, the condition is true, otherwise the condition is false. | (A != B) is true |     

In the sample code:   
```
buttonState == LOW
buttonState != LOW
```

(6) How to use the judgment statement: if     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Basic_tutorial/9img.png)    
```
Syntax:
if (condition) {
//statement(s)
}

Parameters:
condition: A boolean expression (true or false).

Example:
if (buttonState == LOW) {
digitalWrite(ledPin, HIGH);
}

if (buttonState ! = LOW){
digitalWrite(ledPin, LOW);
}
```



**End!**    
For more exciting tutorials, check out the [intermediate tutorial](./Intermediate_tutorial.md)!    












