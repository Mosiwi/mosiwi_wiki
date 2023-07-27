# Advanced tutorial   
Learn communication protocol, driver programming and Arduino library development based on "UNO board + expansion board", and crack Arduino programming deeply with the lowest cost.      

## Previous preparation   
1. Install the [**Arduino IDE**](../../../arduino/arduino_ide/arduino_ide.md).  
2. Install the [**Mosiwi basic learning kit**](../../../arduino/A1E0000_basic_learning_shield/A1E0000_basic_learning_shield.md#Integration-library) library.    
3. Basic operation of the [**Arduino UNO R3**](../../../arduino/A1D0000_uno_r3/A1D0000_uno_r3.md) motherboard.    

## Chapter1 Arduino    
The essence of the Arduino programming language is a combination of C and C++ programming languages, and there is only one main() function, and the initial program entry is also the main() function. In order to allow more people to use the Arduino platform to develop products, the Arduino team tried every means to lower the threshold of programming and hide the tedious details of program development. Open the "main.cpp" file under the Arduino IDE installation file as shown in the figure below, and you can intuitively analyze the above description.         
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/1img.png)       
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/2img.png)       
As can be seen from the figure above, the setup() and loop() functions in the Arduino IDE are only called in the main() function, and they are just ordinary function types.       

The definition of some other keywords and commonly used functions can also be found in the header file in the same folder as "main.cpp", and many other definitions can be found in the following path:     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/3img.png)       


## Chapter2 Library files for Arduino
A large part of the reason why Arduino is so popular with the public is that it has a huge open source library file. You only need to download the relevant library file according to the function, and then copy it to the relevant folder to program quickly. Because various functional functions have been integrated in the library file, the desired function can be realized by calling related functions as required.      

**1. Learn about Arduino project:**    
■ Catalog specification    
When creating an empty project, press **Ctrl+s** on the keyboard to save it.     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/4img.png)       

At this time, a dialog box pops up, name the project. Suppose it is named **"LED_blink"** and saved in my own Arduino working directory **"E:\\Arduino_workspace\\"**. So the IDE will automatically help us create a folder under Arduino_workspace, and put the main file in it, and the main file has the same name as the folder.    
```
 E:\Arduino_workspace\
    LED_blink\
      LED_blink.ino
```
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/5img.png)       

■ Rules for code in the main file
Every Arduino program has a main file with the suffix .ino, which is the file where the program's setup function and loop function are located.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/6img.png)       

Open the file, the framework is as follows:    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/7img.png)       

**2. Use multiple files in the project:**      
Sometimes the bigger the program gets, the messier it gets. Multiple file management can solve this problem. Arduino programs can have multiple source code files, but only one main file, which is the.ino file that stores the **"setup()"** and **"loop()"** functions.       

In order to make the code clearer, we let the main file is used to control the main logical part of the program, and the specific details are packaged into a single module, stored in other files, so that it is easy to manage.    

■ Use files with no suffix (in fact, the suffix is also .ino, but the suffix will not be displayed in the IDE, but .ino will be displayed in the resource manager of the computer, hereinafter referred to as no suffix)     

Click the button marked in the figure below, select the first option **\[New Tab\]**, and enter the file name.     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/8img.png)       
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/9img.png)       

So our project has 2 files, a **"LED_blink"** main file and a file named **"LED"**. Then write the program in the file, which is the simplest multi-file method. as follows:    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/10img.png)       
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/11img.png)       

I do not recommend using this method. This is for noobs who have no C/C++ programming experience. They don't understand that functions must be declared before they can be used after they are defined, and they don't understand the inclusion of header files. These are all done for them by the Arduino IDE. The specific processing of the IDE is in the early stage of compilation. Arduino IDE will merge the file without suffix and the main file into one file, the effect is like writing in the main file. And add **#include "Arduino.h"** in the first line of the main file (**Arduino.h** is the core header file of the Arduino program), then, the IDE scans the function definitions of the merged file and adds function declarations to the defined functions. (This is why the function we defined can be compiled even if it is not declared in the main file)      

But the official made it clear that this mechanism for automatically inserting function declarations is not perfect! So I also suggest that you develop the habit of manually declaring functions.     
```
Also, this generation isn't perfect: it won't create prototypes for functions that have default argument values, or which are declared within a namespace or class.  
```

■ Use traditional C/C++ separate files     
In this way, for a code module, we need a pair of files: source file and header file, ie: **x.c** and **x.h** or **x.cpp** and **x.h** . The former is C language style, and the latter is C++ style. The official seems to recommend that we use C++ to write Arduino code. Whether it is the Arduino standard library or the tutorial, there is a strong C++ atmosphere. So I will use C++ style as an example below.    

For example, we want to package the LED control into a module. We need to create 2 files: LED.h, LED.cpp   
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/12img.png)       
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/13img.png)       
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/14img.png)       

First we think about how to control the LED, then we first write the content of the header file, then write the function implementation in the source file, and finally use this module in the main file. Include the header file using the **#include "LED.h"** preprocessing directive in the main file.       
```
/*******************
LED.h
*******************/
#ifndef _LED_H__                              // Prevents header files from being repeatedly included when used.
#define _LED_H__

#include"Arduino.h"                           // Import Arduino core headers 
class LED {
    private:
        byte pin;                             // Store the pin that control the led
     
    public:
        LED(byte p , bool state=LOW );        // Constructor function
        ~LED();                               // Destructor function

        void on();                            // Turn on the LED
        void off();                           // Turn off the LED
        bool getState();                      // Getting the LED statu
        void disattach();                     // Release pin
};

#endif
```
```
/*****************
LED.cpp
******************/
#include"LED.h"
#include"Arduino.h"

LED::LED(byte p,bool state):pin(p){
   pinMode(pin,OUTPUT);
   digitalWrite(pin,state);
}
LED::~LED(){
    disattach();
} 
void LED::on(){
    digitalWrite(pin,HIGH);
}
void LED::off(){
   digitalWrite(pin,LOW);
}
bool LED::getState(){
    return digitalRead(pin);
}
void LED::disattach() {     
    digitalWrite(pin,LOW);
    pinMode(pin,INPUT);
}
```
```
/**********************
LED_blink：
Instantiate an LED object, control it with pin 10, let it flash 10 times, 
and print its status in the serial port, release and recover the pin after 10 times.
**********************/
#include"LED.h"

LED led(10);
byte count =0;
void setup() {
   Serial.begin(9600);
}

void loop() {
   if(count<10){
     led.on();
     delay(300);
     Serial.print("LED state:");
     Serial.println(led.getState(),DEC);
     
     led.off();
     delay(300);
     Serial.print("LED state:");
     Serial.println(led.getState(),DEC);
     
     ++count;
     if(count==10)
        led.disattach();
   }
}
```
Note: If the header file and the main file are in the same folder, use double quotation marks **"xx.h"** to include the library file into the main file, as follows:
```
#include"LED.h"
```

**3. Make it a standard library!**
If the above library works well for you and you use it often, you can set it up as a standard Arduino library file, and then you can include it in the Arduino IDE and use it.     

Arduino's extension libraries can be placed under the libraries directory:     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/15img.png)       
The usual default path: **C:\\Users\\Administrator\\Documents\\Arduino**    

We need to create a folder in this directory. For example, the above example is LED control, so I created a folder named "LED", and then created 2 empty folders ( examples and src ) and 2 Empty files ( keywords.txt and library.properties ):    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/16img.png)       

Then copy the written ".cpp" and ".h" files into the src file. Create a new folder named "LED_blink" in the examples folder, and copy the "LED_blink.ino" file into it, as follows:     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/18img.png)       

In this way, our main file becomes a sample program in the library file. In the sample, we need to use angle brackets **< >** to include standard files, as follows:       
```
#include<LED.h>    
LED led(10);
byte count =0;

void setup() {
   Serial.begin(9600);
}

void loop() {
    if(count<10){
        led.on();
        delay(300);
        Serial.println(led.getState(),DEC);
     
        led.off();
        delay(300);
        Serial.println(led.getState(),DEC);
     
        ++count;
        if(count==10)
            led.disattach();
    }
}
```

Note: Since the LED control module is already a standard library, use angle brackets **< >** to include library files, as follows:    
```
#include<LED.h>
```
There is a "keywords.txt" file in the LED folder, which is used to configure syntax highlighting for custom libraries. If not configured, the Arduino IDE cannot render highlighted colors.      
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/19img.png)       

The following is the analysis of keywords.txt:     
```
Format: word Tab Description

Word: It is the keyword you want to highlight.
Tab: the tab key on the keyboard.

Possible values for DESCRIPTION:
KEYWORD1 --> highlight class name
KEYWORD2 --> Highlight method name
KEYWORD3 --> highlight library file name
LITERAL1 --> highlight constant name
```
The beginning of "#" is a comment and can be omitted.     
```
# Library (KEYWORD3)
LED  KEYWORD3

# Methods and Functions (KEYWORD2)
on  KEYWORD2
off  KEYWORD2
getState  KEYWORD2
disattach  KEYWORD2
```
There is also a library.properties file in the "LED" folder, which is a configuration library that can display the library name in the Arduino IDE. The contents are as follows:     
```
name=LED
version=*
author=*
maintainer=*
sentence=*
paragraph=*
category=*
url=*
architectures=*
depends=*
```
You can change the * symbol to the required content according to your personal needs, please refer to the following link settings:     
<https://arduino.github.io/arduino-cli/0.24/library-specification/#library-metadata>   

After configuration, you can find the standard library named "LED" and the sample code of the library in the Arduino IDE menu "File" --> "examples".     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/20img.png)       
More info: <https://docs.arduino.cc/learn/contributions/arduino-creating-library-guide>      


## Chapter3 Serial port
**1. Puzzled**
There are many serial port products on the market, such as RS232, RS485, TTL, which can be divided into simplex, half-duplex and full-duplex communication, but they cannot be used together, which can easily confuse everyone. This is because people don't know the difference between them. Now let's study them in detail and divide them into protocol layer, physical layer and communication to explain.       

**2. Protocol layer**
The serial port communication protocol mentioned here is based on UART (Universal Asynchronous Receiver-Transmitter), which specifies the format of sending and receiving data between two devices. The device has two hardware units, one is the transmitter (TX) and the other is the receiver (RX). The connection between the two devices is as follows:     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/21img.png)       

The main purpose of each device's transmitter and receiver is to send and receive data on the serial data line.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/22img.png)       
The transmitting UART is connected to the control data bus that transmits data in parallel, and the parallel data is serially transferred bit by bit on the transmission line to the receiving UART. The receiver converts the serial data to parallel data and transmits it to the parallel device.     

For UART and most serial communications, the same baud rate needs to be set on the sending and receiving devices. In serial port communications, the baud rate determines the maximum number of bits transferred per second.    

UART summary:    
1. Number of wires: 2   
2. Baud rate: 9600, 19200, 38400, 57600, 115200, 230400, 460800, 921600, 1000000, 1500000    
3. Transmission method: asynchronous     
4. Maximum number of hosts: 1     
5. Maximum number of slaves: 1      

A UART device does not use a clock signal to synchronize the transmitter and receiver devices, it transmits data asynchronously. While the receiver uses its internal clock signal to sample the incoming data, the transmitter also generates the bit stream based on its internal clock signal, and no clock signal is required between the receiver and transmitter to synchronize the data. Use the same baud rate on both devices to manage the synchronization point, failure to do so may affect the time to send and receive data, resulting in discrepancies in data processing. Under the premise that the timing of the bits does not deviate too much, the maximum allowable difference in the baud rate is 10%.       

In UART devices, data is transferred in packets. The transmitter and receiver need to create serial data packets and control these physical hardware lines for data transfer. A data packet consists of start bits, data frames, parity bits, and stop bits.     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/23img.png)       

Start bit:   
The data line of a UART device is normally held high when not transmitting data. To start a data transfer, the transmitting UART pulls the transmission line from high to low for 1 clock cycle. When the receiving UART detects a high-to-low transition, it starts reading the bits in the data frame at the set baud rate.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/24img.png)       

Data frame:    
The data frame contains the actual data being transmitted. If parity bits are used, it can be 5 and up to 8 bits. If parity bits are not used, the data frame can be 9 bits. In most cases, the lowest bit of the data is sent first.     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/25img.png)       

Parity bits:   
The parity bit describes whether a number is even or odd. The parity bit is a way for the receiving UART to determine whether the data has changed during transmission. Bits can be altered by electromagnetic radiation or mismatched baud rates.     
After the receiving UART reads the data frame, it calculates the sum of the values of the bits in the data frame that are 1 and checks whether the sum is even or odd.  If the parity bit is 0, the sum of bits that are 1 in the data frame should be even. If the parity bit is 1, the sum of bits that are 1 in the data frame should be odd.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/26img.png)       

To signal the end of a data packet, the transmitting UART drives the data transmission line from low voltage to high voltage for a duration of 1 to 2 bits.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/27img.png)       


**UART transmission steps:**
1\. The sending UART receives data from the data bus in parallel.   
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/28img.png)       

2\. The sending UART adds the start, parity and stop bits to the data frame.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/29img.png)       

3\. The entire data packet is sent serially to the receiving UART, which samples the data line at a preconfigured internal baud rate.   
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/30img.png)       

4\. After verifying the received data successfully, the receiving UART discards the start bit, parity bit and stop bit of the data frame.     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/31img.png)       

5\. The receiving UART converts the serial data back to parallel data and transmits it to the parallel data bus on the receiving end.     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/32img.png)       

**3. physical layer**
The physical layer is to optimize the interface shape or communication data level voltage, so that the transmission distance is longer, and the data transmission is faster and more accurate.       

1\. RS232    
The RS-232 interface conforms to the serial data communication interface standard formulated by the Electronic Industry Alliance (EIA) of the United States, and its full name is EIA-RS-232. It defines the interface between DTE (data terminal devices such as computers) and DCE (data communication devices such as modems) devices using serial binary data exchange.     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/33img.png)       

The line voltage range of RS232 is -25V to +25V. They are divided into signal voltage and control voltage.      
The signal voltage between +3V and +25V represents logic "1", and the signal voltage between -3V and -25V represents logic "0". However, the control voltage signal uses negative logic, that is, logic "1" represents -3 to -25 volts and logic "0" represents +3V to +25V. The voltage from -3V to +3V is considered as an uncertain state.     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/34img.png)       

DB9 interface:     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/35img.png)       

2\. RS485
The RS-485 standard name is TIA/EIA-485-A, RS-485 makes up for the shortcomings of RS-232 short communication distance and low rate. RS-485 is differential transmission and uses A pair of twisted pair wires where one wire is defined as A and the other as B with R receiver and D transmitter inside. It is recommended to add pull-up and pull-down resistors to the terminals of the bus to eliminate interference signals generated externally when the bus is idle.      
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/36img.png)       

Pin Description:     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/37img.png)       

Calculate the resistance formula (assuming that the terminal resistance Rt = 120 Ω, 200mV is the minimum threshold voltage of R receiver) :     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/38img.png)       

Truth table:   
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/39img.png)       

Wiring:    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/40img.png)       
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/41img.png)       

3\. TTL Serial
TTL (Transistor-Transistor Logic) is composed of three wires, which are the data transmitting line (TXD), the data receiving line (RXD), and the common ground (GND).     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/42img.png)       

TTL level:     
| Output low (0) | Output high (1) | Input low (0) | Input high (1) |  
| :--: | :--: | :--: | :--: |  
| <0.8V | >2.4V	| <1.2V	| >2.0V |   

**4. Communication direction**    
With only one data line, data can only be transmitted in one direction.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/43img.png)        
With only one data line, two devices can send data to each other, but data can only be sent from one device to the other at the same time.       
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/44img.png)     
There are two data lines, two devices can send data to each other, and the data of two devices can be sent to each other at the same time.           
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/45img.png)       

**5. Overview**
The serial port we are talking about is an overview. The interface that can send data or receive data serially in a piece of data can be called a serial port.      
1. RS232, RS485, TTL serial ports, etc. can also send data or receive data serially in one piece of data, so they can all be called serial ports. It's just that they specify the electrical properties on the data line, and they don't specify how the data is transmitted.     
2. We can run different data transmission protocols on RS232, RS485, and TTL serial ports, such as the Universal Asynchronous Receiver-Transmitter (UART) protocol explained in the protocol layer above, and you can also run your own defined protocols.     
3. Simplex, half-duplex, and full-duplex communication only stipulate the direction of data transmission at the same time, and do not involve any data transmission protocol and electrical properties.      

Now returning to the serial port on the UNO board, it is a TTL serial port, running the Universal Asynchronous Receiver-Transmitter (UART) protocol, the communication format is XXX-8-N-1 (xxx special rate, 8 bit data, no parity bit, 1 stop bit), and it is a full-duplex serial port.     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/46img.png)       

USB port of PC can not communicate with TTL serial port of Mega328 chip directly, because their communication protocol is different, so USB to TTL serial port chip needs to be used to convert USB signal to TTL signal.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/47img.png)       

**6. Examples of software simulation serial port**
In this example, we use the way of software simulation to realize a TTL serial port function, the data format of the serial port is XXx-8-N-1 (xxx: variable rate, 8-bit data, no parity check bit, 1 stop bit), the advantage of this way is that any two pins on the UNO board can be defined as a serial port.    

■ Open the "3.0.0_Soft_serial" example in the "[Mosiwi_Basic_Learning_Kit](../../../arduino/A1E0000_basic_learning_shield/A1E0000_basic_learning_shield.md#integration-library)" library file, then select the board type and port, and then upload the code.    

■ Open the serial port, adjust the baud rate of the serial port monitor to 9600, fill in "hello mosiwi" in the transmission frame, and then click send, UNO board will receive the data from the new back to the serial port monitor.     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/48img.png)       

code analysis:    
1\. Define a soft serial port class.    
```
class SoftwareSerial { ... }
```

2\. The constructor of the SoftwareSerial class initializes the receive pin as input mode and the transmit pin as output mode, and initializes the private variables of the class (after the colon and before the curly braces).    
```
SoftwareSerial::SoftwareSerial(uint8_t receivePin, uint8_t transmitPin) : ...{
  ...
}
```

3\. Set the baud rate of the serial port.   
```
void SoftwareSerial::begin(long speed){ ... }
```
The baud rate is used to calculate the time it takes to transfer a data bit:   
$$bit_time = (1/speed)/(1/F_CPU )$$

Then the bit time is divided into four parts, which is convenient for subsequent calculation of various bit delays:    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/49img.png)        
$$bit_delay = (F_CPU / speed) / 4$$

In order to obtain the accurate delay of various transmitting bits and receiving bits, it is necessary to consider the influence of different versions of GCC compiler on the running speed of the program. See the source code for the calculation.    

4\. Set the receiving pin level change to generate an interrupt (PCINT --> PCMSK register).   
Using the PCINT function of MEGA328p, the interrupt can be generated when the level of each pin changes. The user needs to read the relevant register to determine which PCINT port has changed, and then jump into a specified program.    

5\. Then the object of soft serial port class enters the listening state.     
```
bool SoftwareSerial::listen(){ ... }  
```

6\. Enable the receiving pin of the serial port to interrupt when the level changes.    
```
void SoftwareSerial::setRxIntMsk(bool enable){ ... }
```

7\. Set interrupt vectors and functions: Interrupts generated by PCINT0--PCINT3 all call the recv() function.     
```
inline void SoftwareSerial::handle_interrupt(){
  if (active_object){
    active_object->recv();
  }
}

#if defined(PCINT0_vect)
ISR(PCINT0_vect){
  SoftwareSerial::handle_interrupt();
}
#endif

#if defined(PCINT1_vect)
ISR(PCINT1_vect, ISR_ALIASOF(PCINT0_vect));
#endif

#if defined(PCINT2_vect)
ISR(PCINT2_vect, ISR_ALIASOF(PCINT0_vect));
#endif

#if defined(PCINT3_vect)
ISR(PCINT3_vect, ISR_ALIASOF(PCINT0_vect));
#endif
```
More info: <http://www.nongnu.org/avr-libc/user-manual/group__avr__interrupts.html>    

8\. The receive function of the soft serial port that is executed if the level of the receive pin is changed.    
```
void SoftwareSerial::recv(){ ... } 
```
A 64-byte receive cache number is set and two Pointers, the receive cache header and the receive cache tail, are created. The two Pointers can point to any address in the array, and the cache tail pointer is incremented by 1 for each byte received.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/50img.png)        

9\. Count the number of received data in the receive cache array and return the value.     
```
int SoftwareSerial::available(){ ... }
```
Algorithm:   
$$Num = (tail + 64 - head) \% 64$$
The above algorithm can count the number of received data in the receive cache array in both cases tail > head and tail < head.     

10\. Reads all data in the receive buffer array byte by byte.     
```
int SoftwareSerial::read(){ ... }
```
The cache header pointer is incremented by 1 for each byte read, and the following is used to determine whether the cache is fully read:   
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/Arduino_tutorial/Advanced_tutorial/51img.png)        

11\. Data is sent byte-by-byte from the send pin, with all interrupts turned off.   
```
size_t SoftwareSerial::write(uint8_t b){ ... }
```

<span style="color: rgb(255, 76, 65);">Note: Since the serial port is simulated for software, the Baud range is 1200 -- 19200 bps.</span>     

**7. Examples of hardware serial ports**      
Above, we used the IO port to simulate the serial port communication protocol for communication. In the process of communication, the processor is occupied for a long time (because the main program stream is delayed or cyclic waiting for signals), and the transmission time is relatively slow (affected by the delay, cycle and IO port output speed).    
Now most single-chip microcomputers have realized the serial communication function in the chip internal hardware, and there are special hardware receiving and transmitting units inside the hardware to process data. It is more convenient for the user to use, and the transmission speed is faster, and does not occupy the processor for a long time.    

For the use of hardware serial port based on arduino, please refer to:      
<https://www.arduino.cc/reference/en/language/functions/communication/serial/>     


## Chapter4 I2C communication protocol




**End!**    
   












