# Intermediate tutorial   
Learn common programming syntax based on "UNO board + expansion board + peripheral module", and learn the most comprehensive arduino syntax and application with the lowest cost.     

## Previous preparation   
1. Install the [**Arduino IDE**](../../../arduino/arduino_ide/arduino_ide.md).     
2. Basic operation of the [**Arduino UNO R3**](../../../arduino/A1D0000_uno_r3/A1D0000_uno_r3.md) motherboard.    
3. Learn about [**3in1 basic learning shield**](../../../arduino/A1E0000_basic_learning_shield/A1E0000_basic_learning_shield.md).  
4. Install the [**Mosiwi basic learning kit**](../../../arduino/A1E0000_basic_learning_shield/A1E0000_basic_learning_shield.md#integration-library) library.    

## Chapter1 RGB LED    

**Curriculum question:** 
1. What is resistance?     
2. How to control R, G, B LED?    
3. What is a preprocessing directive: #define     

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/1img.png)    

**Open the example code: "2.0.0_RGB_led"**   
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/2img.png)    
Upload the code to the UNO board.     
<span style="color: rgb(255, 76, 65);">Note: All the sample code in the following sections is opened in the same way as in the figure above.</span>     

**Example code phenomena:**   
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/3img.png)    
RGB LED lights flash red, green, blue, yellow, cyan, mauve and white.   

**FAQ:** 
(1) What is resistance?   
The resistance of a conductor to the current is called its resistance. The greater the resistance of the conductor, the greater the obstruction effect of the conductor on the current. The resistance of a conductor is usually represented by the R symbol, the unit of resistance is ohms, and the symbol is Ω.     

Resistance is defined by the ratio of the voltage U at the two ends of the conductor to the current I passing through the conductor:      
$$R=U/I$$     

Color ring resistor uses different colors to show the resistance and accuracy, as shown below:    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/4img.png)    

(2) How to control R, G, B LED?    
When the expansion board is directly inserted into the UNO board, the R, G, and B leds on the expansion board are controlled by the 5, 6, and 9 pins of the UNO board. These three pins can be set to digital output mode, by output high or low level to control the LED on and off.             
Set pin mode:    
```
Syntax:
pinMode(pin, OUTPUT);

Parameters:
pin: LED pin number, 5, 6, 9
```
Set the leds on or off:    
```
Syntax:
digitalWrite(pin, state);

Parameters:
pin: LED pin number, 5, 6, 9
state: HIGH or LOW, corresponding to the LED on and off state
```

(3) What is a preprocessing directive: #define  
**\#define** allows the programmer to assign a name to a constant before compiling the program, and the compiler will replace references to these constants with defined values at compile time.    
```
Syntax:
#define name val

Parameters:
name: Constant name.
val: Constant value.

In the sample code:
#define T 500
```
More information: <https://www.arduino.cc/reference/en/language/structure/further-syntax/define/>    

## Chapter2 waterfall light   

**Curriculum question:** 
1. How to control the LED strip of the expansion board?      

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/5img.png)    

**Open the example code: "2.1.0_Waterfall_light"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
The LED strip on the expansion board turns on and off in cycles.   
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/6img.png)    

**FAQ:** 
(1) How to control the LED strip of the expansion board?     
There is one LED strip on the expansion board, which is controlled by the 74HC595 chip on the expansion board. 74HC595 is a widely used serial input and parallel output chip.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/7img.png)    

Because the 74HC595 chip is controlled by pin 8, A0, and A1 of the UNO, the LED strip on the expansion board is ultimately controlled by the UNO board. For ease of use, the control methods have been written as functions and integrated into the library file, which must include the relevant headers:   
```
#include <MswLed.h>
```

Initialize the control pins:   
```
Init_LED_IO(8, A1, A0);
```

Control LED strip function:   
```
Syntax:
SetLed(num, state);

Parameters:
num: LED, allowed range: 0-7
state: LED state, on or off; For example: 0, 1, On, Off

In the sample code: 
int i;
for(i=0; i<=7; i++){
SetLed(i, On);
delay(500);
}
```

## Chapter3 LED strip   

**Curriculum question:** 
1. How is the map() function used?   
2. How is the break statement used?   
3. How is the switch statement used?  
4. What are binary numbers, decimal numbers, and hexadecimal numbers?     
5. How to control all leds of the LED strip at the same time?   

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/8img.png)    

**Open the example code: "2.1.1_Led_bar"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
The more you push the slide resistor up, the more LEDs are turned on; the more you push the slide resistor down, the more LEDs are turned off.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/9img.png)    

**FAQ:**
(1) How is the map() function used?   
map() is a mapping function that remaps numbers from one range to another, as follows:    
```
Syntax:
map(value, fromLow, fromHigh, toLow, toHigh)

parameter:
value: The value to map.
fromLow: The lower limit value of the current range.
fromHigh: The upper limit value of the current range.
toLow: The lower limit value of the target range.
toHigh: The upper limit value of the target range.

In the sample code:
int analogValue = 0;
byte ledNum = 0;
ledNum = map(analogValue, 0, 1010, 0, 8);
```


(2) How is the break statement used?   

(3) How is the switch statement used?  

(4) What are binary numbers, decimal numbers, and hexadecimal numbers?    

(5) How to control all leds of the LED strip at the same time?   

## Chapterxx xxxx   

**Curriculum question:** 
1. How to control the 8 blue leds on the expansion board?    

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/img.png)    


**Open the example code: "2.1.0_Waterfall_light"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
   
**FAQ:**

## Chapterxx xxxx   

**Curriculum question:** 
1. How to control the 8 blue leds on the expansion board?    

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/img.png)    


**Open the example code: "2.1.0_Waterfall_light"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
   
**FAQ:**

## Chapterxx xxxx   

**Curriculum question:** 
1. How to control the 8 blue leds on the expansion board?    

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/img.png)    


**Open the example code: "2.1.0_Waterfall_light"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
   
**FAQ:**

## Chapterxx xxxx   

**Curriculum question:** 
1. How to control the 8 blue leds on the expansion board?    

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/img.png)    


**Open the example code: "2.1.0_Waterfall_light"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
   
**FAQ:**


## Chapterxx xxxx   

**Curriculum question:** 
1. How to control the 8 blue leds on the expansion board?    

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/img.png)    

**Open the example code: "2.1.0_Waterfall_light"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
   
**FAQ:**

## Chapterxx xxxx   

**Curriculum question:** 
1. How to control the 8 blue leds on the expansion board?    

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/img.png)    


**Open the example code: "2.1.0_Waterfall_light"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
   
**FAQ:**


## Chapterxx xxxx   

**Curriculum question:** 
1. How to control the 8 blue leds on the expansion board?    

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/img.png)    


**Open the example code: "2.1.0_Waterfall_light"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
   
**FAQ:**


## Chapterxx xxxx   

**Curriculum question:** 
1. How to control the 8 blue leds on the expansion board?    

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/img.png)    


**Open the example code: "2.1.0_Waterfall_light"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
   
**FAQ:**


## Chapterxx xxxx   

**Curriculum question:** 
1. How to control the 8 blue leds on the expansion board?    

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/img.png)    


**Open the example code: "2.1.0_Waterfall_light"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
   
**FAQ:**


## Chapterxx xxxx   

**Curriculum question:** 
1. How to control the 8 blue leds on the expansion board?    

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/img.png)    


**Open the example code: "2.1.0_Waterfall_light"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
   
**FAQ:**


## Chapterxx xxxx   

**Curriculum question:** 
1. How to control the 8 blue leds on the expansion board?    

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/img.png)    


**Open the example code: "2.1.0_Waterfall_light"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
   
**FAQ:**


## Chapterxx xxxx   

**Curriculum question:** 
1. How to control the 8 blue leds on the expansion board?    

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/img.png)    


**Open the example code: "2.1.0_Waterfall_light"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
   
**FAQ:**


## Chapterxx xxxx   

**Curriculum question:** 
1. How to control the 8 blue leds on the expansion board?    

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/img.png)    


**Open the example code: "2.1.0_Waterfall_light"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
   
**FAQ:**


## Chapterxx xxxx   

**Curriculum question:** 
1. How to control the 8 blue leds on the expansion board?    

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/img.png)    


**Open the example code: "2.1.0_Waterfall_light"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
   
**FAQ:**

## Chapterxx xxxx   

**Curriculum question:** 
1. How to control the 8 blue leds on the expansion board?    

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/img.png)    


**Open the example code: "2.1.0_Waterfall_light"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
   
**FAQ:**

## Chapterxx xxxx   

**Curriculum question:** 
1. How to control the 8 blue leds on the expansion board?    

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/img.png)    


**Open the example code: "2.1.0_Waterfall_light"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
   
**FAQ:**

## Chapterxx xxxx   

**Curriculum question:** 
1. How to control the 8 blue leds on the expansion board?    

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/img.png)    


**Open the example code: "2.1.0_Waterfall_light"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
   
**FAQ:**

## Chapterxx xxxx   

**Curriculum question:** 
1. How to control the 8 blue leds on the expansion board?    

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/img.png)    


**Open the example code: "2.1.0_Waterfall_light"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
   
**FAQ:**

## Chapterxx xxxx   

**Curriculum question:** 
1. How to control the 8 blue leds on the expansion board?    

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/img.png)    


**Open the example code: "2.1.0_Waterfall_light"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
   
**FAQ:**

## Chapterxx xxxx   

**Curriculum question:** 
1. How to control the 8 blue leds on the expansion board?    

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/img.png)    


**Open the example code: "2.1.0_Waterfall_light"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
   
**FAQ:**


**End!**    
For more exciting tutorials, check out the [advance tutorial](./Advanced_tutorial.md)!    












