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




**End!**    
   












