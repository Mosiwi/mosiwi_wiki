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
More info: <https://www.arduino.cc/reference/en/language/functions/math/map/>    

(2) How is the break statement used?   
The "break" statement is used to exit the "for", "while" and "do...while" loop. It is also used to exit the "switch case" statement.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/10img.png)    
More info: <https://www.arduino.cc/reference/en/language/structure/control-structure/break/>    

(3) How is the switch statement used?  
Like the "if" statement, the "switch case" statement allows the programmer to control the flow of the program by executing different pieces of code under specified conditions.    
```
Description:
The "switch" statement compares the value of the variable "var" to the value specified in the case statement as "label". When the value of a case statement "label" is found to match the value of the variable "var", the block after the "case" statement is run until the "break" statement is executed, and the switch statement comes out.

Syntax:
switch (var) {
    case label1:
    // statements
    break;
    case label2:
    // statements
    break;
    efault:
    // statements
    break;
}

Parameters:
var: A variable used for comparison. Allowed data types: int, char.
label1, label2: Constants. The data types are int and char.

In the sample code:
byte ledNum = 0;
switch (ledNum){
    case 0: SetLedBar(0b00000000); break;
    case 1: SetLedBar(0b00000001); break;
    case 2: SetLedBar(0b00000011); break;
    case 3: SetLedBar(0b00000111); break;
    case 4: SetLedBar(0b00001111); break;
    case 5: SetLedBar(0b00011111); break;
    case 6: SetLedBar(0b00111111); break;
    case 7: SetLedBar(0b01111111); break;
    case 8: SetLedBar(0b11111111); break;
    default: break;
}
```

(4) What are binary numbers, decimal numbers, and hexadecimal numbers?    
**Binary numbers and decimal numbers:**   
In the computer hard disk, every 1 location can only store 0 or 1 (high or low level), then the data stored in the hard disk is actually a string of 0 and 1, in other words, if we have a way to record 0 and 1 can record data. 1 position can only store 0 and 1, need many positions to store a lot of 0 and 1, we call each 1 position "bit", that is, binary numbers, binary numbers is generally "0b" or "0B" as the prefix.        

The 1 "char" variable is 8 bits, 8 consecutive locations in memory, as shown below:    
| Bit | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| Binary numbers | 0 or 1 | 0 or 1 | 0 or 1 | 0 or 1| 0 or 1 | 0 or 1 | 0 or 1 | 0 or 1 |
| Decimal numbers | 2\*2\*2\*2\*2\*2\*2\*（0 or 1） | 2\*2\*2\*2\*2\*2\*（0 or 1） | 2\*2\*2\*2\*2\*（0 or 1） | 2\*2\*2\*2\*（0 or 1） | 2\*2\*2\*（0 or 1） | 2\*2\*（0 or 1） | 2\*（0 or 1） | 0 or 1 |

From the figure above, we can see that the value range of "char" variable is: 0-255, please see the following calculation:       
```
Binary number ：0b00000001
Decimal number：0+0+0+0+0+0+0+1=1
```
...
```
Binary number ：0b10000001
Decimal number：2*2*2*2*2*2*2*1+0+0+0+0+0+0+1=129
```
...
```
Binary number ：0b11111111
Decimal number：2*2*2*2*2*2*2*1+64+32+16+8+4+2+1=255
```
<span style="color: rgb(255, 76, 65);">Note: You do not need to write prefixes in Decimal numbers.</span>       

**Decimal numbers and hexadecimal numbers:**   
Each digit of A hexadecimal number ranges from 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, and F, corresponding to the following decimal values:    
| Hexadecimal numbers | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | A | B | C | D | E | F |    
| :--: | :--: | :--:| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |   
| Decimal numbers | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 |   

The relationship between hexadecimal numbers and decimal numbers is as follows:    
| Bit | 3 | 2 | 1 | 0 |   
| :--: | :--: | :--: | :--: | :--: | :--: | :--: |   
| Hexadecimal numbers | 0 ot F | 0 ot F | 0 ot F | 0 ot F |       
| Decimal numbers | 16\*16\*16（0 to 15） | 16\*16（0 to 15） | 16（0 to 15） | 0 to 15 |  

Hexadecimal number is usually prefixed with "0x" or "0X" as follows:   
```
Hexadecimal number：0x000F
Decimal number：0+0+0+15=15
```
```
Hexadecimal number：0x00FF
Decimal number：0+0+16*15+15=255
```
```
Hexadecimal number：0xFFFD
Decimal number：16*16*16*15+16*16*15+16*15+13=65533
```
You can open the PC calculator to verify the above calculation, first switch to the binary mode input "11111111"; You will get the decimal number "255" and the hexadecimal number "FF".    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/11img.png)    

(5) How to control all leds of the LED strip at the same time?   
In the previous chapter, we learned how to control a single LED, so we'll use another function that allows us to control the state of eight leds from bits of data.      
```
Syntax:
SetLedBar(num);

Parameters:
num: LED control value, allowed value: 0b00000000--0b11111111 (0--255).
```
Relationship between the LED state and the value of "**num**":      
| Bit | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| 0b | 0 or 1 | 0 or 1 | 0 or 1 | 0 or 1 | 0 or 1 | 0 or 1 | 0 or 1 | 0 or 1 |

## Chapter4 bit operation  
**Curriculum question:** 
1. How to use the bit operations: &, |, ~, ^, < <, > >        

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/12img.png)    

**Open the example code: "2.1.2_Bitwise_operation"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
Every time you press "Button" on the expansion board, the LED strip on the expansion board will be lit in the order shown below.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/13img.png)    

**FAQ:**
(1) How to use the bit operations: &, |, ~, ^, < <, > >     
The bit AND operation: &      
```
Description:
Two data bits AND operations: 1&1 =1, 1&0=0, 0&1=0, 0&0=0    

Examples:

  0b11110000  --> operand1
& 0b10000001  --> operand2
--------------
  0b10000000  --> result
```
The bit OR operation: &    
```
Description:
Two data bits OR operations: 1|1=1，1|0=1，0|1=1，0|0=0

Examples:   

  0b11110000  --> operand1
| 0b10000001  --> operand2    
--------------
  0b10000000  --> result
```
The bit NOT operation: ~    
```
Description:
Two data bits NOT operations: ~0=1，~1=0  

Examples: 

~  0b10000001  --> operand
--------------
   0b01111110  --> result
```
The bit XOR(Exclusive OR) operation: ^   
```
Description:
Two data bits XOR operations: 1|1=0，1|0=1，0|1=1，0|0=0

Examples: 

  0b11110000  --> operand1
^ 0b10000001  --> operand2    
--------------
  0b01110001  --> result
```
Bit left shift operation: <<
```
Syntax:
variable << number_of_bits;

Parameters:
variable: A variable or number
number_of_bits: The number of bits shifted

Examples:
0b00000001 << 7 = 0b10000000
```
Bit right shift operation: >>
```
Syntax:
variable >> number_of_bits;

Parameters:
variable: A variable or number
number_of_bits: The number of bits shifted

Examples:
0b10000000 >> 7 = 0b00000001    
```


## Chapter5 Buzzer
**Curriculum question:** 
1. What is buzzer?    
2. What is MOS transistor?    
3. How do you use the tone() and notone() functions?       

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/14img.png)    

**Open the example code: "2.2.0_Buzzer"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
The buzzer cycle produced 440 Hz and 880 Hz sounds.     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/15img.png)    

**FAQ:**
(1) What is buzzer?    
The piezoelectric buzzer consists of internal piezoelectric elements and has two pins, one for the power positive and the other for the negative.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/16img.png)    
When the buzzer is energized, an electric charge is applied to the ceramic disk of its internal piezoelectric element, resulting in vibration. The ceramic disc is attached to a vibrating disc, which vibrates along with it, producing an audible sound.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/17img.png)    

Passive buzzer VS active buzzer:   
Active buzzers use DC power and buzzers emit sound at a fixed frequency.      
As for the passive buzzer, additional drive circuits are required. The frequency of the sound will vary with the frequency of the square wave signal. If the frequency signal is not added, the passive buzzer does not sound.     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/18img.png)    
The extension board integrates a patch passive buzzer that is controlled by the 9 pins of the UNO board when the extension board is directly inserted into the UNO board.    

(2) What is MOS transistor?    
MOS, is MOSFET (Metal-Oxide-Semiconductor Field-Effect Transistor) abbreviation.      
Mosfets are four-terminal devices with source (S), gate (G), drain (D), and body (B) terminals. Typically, the B terminal is connected to the S terminal, resulting in a three-terminal device. MOS transistors can be divided into enhanced MOS transistors and depletion MOS transistors, which can be subdivided into N-channel MOS transistors and p-channel MOS transistors. The enhanced MOS transistors are more widely used in the two types.     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/19img.png)    

MOS transistors are commonly used as switches. If the voltage between the drain and the source reaches the threshold voltage, the G and S poles are conducted, otherwise they are not conducted. Common circuits are as follows:   
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/20img.png)    

A 2N7002 MOS is used on the extension board to drive the buzzer. It is an enhanced N-channel MOS. When a voltage greater than 2.5V is applied to its gate, the MOS drain and source electrodes are on, and therefore, the buzzer is on. Otherwise the buzzer is open.   
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/21img.png)    

(3) How do you use the tone() and notone() functions?   
The tone() and notone() functions are built-in libraries in the Arduino IDE that you can call directly.    

The tone() function:     
```
Description:
Produces a square wave at the specified frequency (50% duty cycle) on the UNO pin. You can specify a duration, otherwise a square wave will be generated until noTone() is called.

Syntax:
tone(pin, frequency);
tone(pin, frequency, duration);

Parameters:
pin: The pin of UNO.
frequency: The frequency of the tone, in Hertz. Allowed data type: unsigned int
duration: The duration in milliseconds (optional) Allowed data type: unsigned long.

Note:
The set frequency must be greater than 31Hz.
Using the tone() function affects the PWM output of pins 3 and 11 and affects the use of timer 2.
Only one pin can use tone() at a time.If you want to use another pin, you need to close the active pin with the notone() function.

In the sample code:
byte BuzzerPin = 9;
tone(BuzzerPin, 440, 1000);
```
More info: <https://www.arduino.cc/reference/en/language/functions/advanced-io/tone/>   

The notone() function:    
```
Description:
Stops the square wave generated by the tone() trigger.

Syntax:
noTone(pin)

Parameters:
pin: The UNO pin that needs to stop generating the tone.
```
More info: <https://www.arduino.cc/reference/en/language/functions/advanced-io/notone/>    


## Chapter6 Frequency-Tone  
**Curriculum question:** 
1. What is the relationship between the frequency and the tone of the buzzer?        

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/22img.png)    

**Open the example code: "2.2.1_Frequency_Tone"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
When the slider resistor is pushed, the buzzer produces the sound of "DO", "RE", "MI", "FA", "SO", "LA", "SI", and the frequency of the sound is displayed by the 4-bit digital tube.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/23img.png)    

**FAQ:**
(1) What is the relationship between the frequency and the tone of the buzzer?      
Various tones are produced by sounds of different frequencies. Because buzzers can produce sounds of different frequencies, buzzers can also produce a variety of tones.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/24img.png)    


## Chapter7 Music   
**Curriculum question:** 
1. What is music?    
2. How do you use sizeof()?    
3. How to use the store statements: PROGMEM, pgm_read_word_near(), pgm_read_float_near()       

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/25img.png)    

**Open the example code: "2.2.2_Jingle_bells"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**    
The buzzer keeps playing the song "Jingle bells" on a loop.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/15img.png)    
  
**FAQ:**
(1) What is music?    
Music is the art of arranging sound in time through elements such as melody, harmony, rhythm, and timbre.   
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/26img.png)    

Analysis of musical notation:     
Note rhythm is divided into one beat, half beat, 1/4 beat and 1/8 beat. We stipulate that the time of a beat note is 1, so half beat is 0.5, and 1/4 beat is 0.25. 1/8 is 0.125... For each note to be given such a time to play out, the whole tone of the music comes out.    

In the bottom left corner of the title of the song in the notation, there is a 1 = F 4/4 icon. F means that the song is in the key of F, and 4/4 means that the song is in four or four beats.    

Note type description: Take note 5 3 2 1 5 0 5 5 in the first short section of Jingle Bells notation as an example.   
1. Notes 5, 3, 2, 1, and 0 are all underlined to indicate that each note has 0.5 beat, so note 5 has 0.5 beat, note 3 has 0.5 beat, note 2, 1 has 0.5 beat, and note 0 has 0.5 beat. There are two underscores below 5, that is, 0.25 beat. Each note is 1 beat, and each underscore is the current number of beats divided by 2, so one underscore is 1/2=0.5 beats, and two underscore is 1/2/2=0.25 beats. Then, the beat of this short piece of notation (5,3,2,1,0,5,5) is 0.5 + 0.5 + 0.5 + 0.5 + 0.25 + 0.25 + 0.5 + 1 = 4, which is consistent with the 4-4 beat on the notation, indicating that the number of beats in this short piece of notation is not wrong. Remember, Jingle Bells has four beats per segment.   
2. You may also find that some notes have a dot, when the note does not have a dot, it means the middle note, for example, note 3 in the first paragraph, means the middle note 3; When a note has a dot underneath it, it's a low note, like note 5 in the first paragraph, it's a low note 5; Similarly, a note with a small dot above it indicates a high note. No high notes appear in the Jingle Bells score.     
3. Note followed by a decimal point, indicating that the note beat +0.5 beat (if the note is underlined, +0.5 beat on the basis of the underlined beat); Note is followed by -, indicating note +1 beat (+1 beat on top of the underlined beat).    
4. Two consecutive notes with an arc above, indicating the connection, you can slightly change the frequency of the following note, such as reducing or increasing the frequency, so that the sound will be smoother.    

![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/27img.png)    
In this case, the Jingle Bells are in the key of F, so the notes corresponding to the key of F are marked in red in the table. Please see the code in the example for the implementation of the music code!     

(2) How do you use sizeof()?    
```
Syntax:
sizeof(variable);

Parameters:
variable: Any variable type or array (e.g. int, float, byte).

Return value:
The number of bytes in a variable or in an array. Data type :size_t
```
More info <https://www.arduino.cc/reference/en/language/variables/utilities/sizeof/>    

(3) How to use the store statements: PROGMEM, pgm_read_word_near(), pgm_read_float_near()       
The PROGMEM keyword is a variable modifier that can only be used with data types defined in the "pgmspace.h" header file. It tells the compiler to "put this information in flash memory" instead of the usual SRAM.     
```
Syntax:
const dataType variableName[] PROGMEM = {data0, data1, data3… };

Parameters:
dataType: Data type; a variable of any data type.
variableName: The name of the data array
```
Flash memory data requires a specific syntax to read data, as follows:     
```
Syntax:
pgm_read_dataType_near(address_short);

Parameters:
dataType: The data type, e.g., byte, flaot, etc.
address_short: The address.

Return value:
The value in the address.
```
More info: <https://www.arduino.cc/reference/en/language/variables/utilities/progmem/>     


## Chapter8 Buzzer-Timer   

**Curriculum question:** 
1. How do you use a timer to make a buzzer sound?       

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/28img.png)    

**Open the example code: "2.2.3_Buzzer_Timer"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
The buzzer on the extension board emits 50Hz sound all the time.     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/15img.png)    

**FAQ:**
(1) How do you use a timer to make a buzzer sound?     
Instead of using the tone() function to set the buzzer to different frequencies, you can also use a timer interrupt to accomplish this. We have seen how to use timer1 and timer2 in the previous chapter, and now we can use them to generate square waves with different frequencies.      
Frequency calculation formula:      
$$f = 1/T$$
f: Frequency in Hertz   
T: Period in seconds

For example, if we want to generate a square wave with a frequency of 500Hz, the formula is: T=1/500=0.002 seconds =2 milliseconds      
In this case, we only need to execute the interrupt function once every 1 millisecond, and then change the level of the buzzer driver pin in the interrupt function, so that the following square wave can be generated:    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/29img.png)    
Example code:
```  
byte BuzzerPin   = 9; 
void tone(void) {  
  static boolean output = HIGH;
  digitalWrite(BuzzerPin, output);
  output = !output;
}
void setup() {
  pinMode(BuzzerPin, OUTPUT);
  MsTimer2::set(1, tone); 
  MsTimer2::start();
}
void loop() {
}
```


## Chapter9 Microphone   
**Curriculum question:** 
1. What is a microphone?   

**Program flow diagram:** 
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/30img.png)    

**Open the example code: "2.3.0_Microphone"**      
1. Open the sample code using the methods in **"[Chapter_1](./Basic_tutorial.md#chapter-1-blink)"**.   
2. Upload the code to the UNO board.

**Example code phenomena:**  
When powered on, the microphone will always obtain the sound data of the current environment. Open the serial port monitor and adjust the baud rate to 9600. The serial port monitor has been printing the analog value of the amplified sound and the voltage value calculated by the program.     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Intermediate_tutorial/31img.png)    


**FAQ:**
(1) What is a microphone?  

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












