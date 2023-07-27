# C-language for Raspberry pi4    
This tutorial is based on the [C1K0001 4in1 basic learning kit](../../C1K0000_4in1_basic_learning_kit/C1K0000_4in1_basic_learning_kit.md).     

## Prepared knowledge     
**Learn about** [**Basic learning shield**](../../../arduino/A1E0000_basic_learning_shield/A1E0000_basic_learning_shield.md).  

**Learn about** [**3in1 basic learning shield**](../../../common_product/C1E0000_3in1_basic_learning_shield/C1E0000_3in1_basic_learning_shield.md).  

**Raspberry pi4 basics**     
If you don't have Raspberry pi4 basics, you can follow the link to learn the basics: [Click Me](../../../raspberry/R1D0000_raspberry_pi4/R1D0000_raspberry_pi4.md)      

**Install the GPIO library**
1. Install the [Wiringpi](../../../raspberry/wiringpi/wiringpi.md)   
2. Install the [BCM2835](../../../raspberry/bcm2835/bcm2835.md)      

**Download sample code**   
[Login to Raspberry pi4 using PUTTY](../../../raspberry/R1D0000_raspberry_pi4/R1D0000_raspberry_pi4.md#remote-access), then use the following command to download the sample code:      
```   
git clone https://github.com/Mosiwi/Mosiwi-basic-learning-kit     
```    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/pi4_tutorial/1img.png)    

The file in the "**Mosiwi-basic-learning-kit-for-arduino -> pi4 -> c**" folder is the sample code：           
```
cd Mosiwi-basic-learning-kit/pi4/c

ls
```
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/pi4_tutorial/3img.png)    

Document architecture:   
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/pi4_tutorial/2img.png)      
1. If you are a newbie, the files in the "**src**" folder are not recommended to modify them, which may cause the code in the "**examples**" folder to compile incorrectly.    
2. Each example folder contains a "Makefile", "xxx.o", and "xxx.c" files, as well as an execution file.     
3. The "xxx.o" and execution files are generated from the "Makefile" file.    
4. If you are a newbie, it is not recommended to modify the contents of the "Makefile" and the name of the "xxx.c" file, which may cause compilation errors.    
5. If the content of the xxx.c file is modified, you need to compile it again to generate an executable file.    
```
sudo make
```
6. Run the execution file with the following command:   
```
sudo ./xxx
```

Resource: [GNU Make](https://www.gnu.org/software/make/)(Makefile) 

## Basic Example: Terminal    
**Objective:**       
1. Run the sample code.   
2. Recompile the sample code. 
3. Modify and recompile the sample code.      

**Objective_1:**       
Terminal into the **"1.0.0_Terminal"** folder:    
```
cd ~/Mosiwi-basic-learning-kit/pi4/c/examples/1.0.0_Terminal/    
```
Permission to view execution files:   
```
ls -al   
```
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/pi4_tutorial/4img.png)      
r: Read permission. &ensp;&ensp; w: Write permission. &ensp;&ensp; x: Execute permission.     

If the file does not have execution permissions as shown in the figure above, you need to add execution permissions:    
```
chmod 777 terminal   
ls -al   
```
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/pi4_tutorial/5img.png)     

Run the compiled sample code:     
```
sudo ./terminal     
```
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/pi4_tutorial/6img.png)      

**Objective_2:**       
Delete the latest executable file and then view the files in the folder:     
```
rm terminal   
ls   
```
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/pi4_tutorial/7img.png)     

The "terminal" executable is no longer visible from the image above, now re-run the "Makefile" file to generate the executable "terminal" file.    
```
sudo make  
ls   
```
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/pi4_tutorial/8img.png)      

**Objective_3:**    
Edit the sample code using the [nano tool](https://www.nano-editor.org/) that comes with the Raspberry PI system:  
```
sudo nano terminal.c   
```
When the editing is complete, save the file by typing the following command on the keyboard and exit the nano editor:  
```terminal
Ctrl+O
Ctrl+C
```
Recompile the "terminal.c" source file:   
```
sudo make  
ls
```
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/pi4_tutorial/8img.png)      


## Wiring diagram   
Turn off the Raspberry PI and connect the Raspberry PI to the expansion board with a 40P color cable:    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/pi4_tutorial/0img.png)      
Then restart Raspberry PI and TUTTY.     

## Example1: Arithmetic operator             
Run the following command on the terminal:       
```
cd ~/Mosiwi-basic-learning-kit/pi4/c/examples/1.0.1_Arithmetic_operation/     
chmod 777 arithmetic_operation     
sudo ./arithmetic_operation
```
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/pi4_tutorial/9img.png)     

## Example2 Blink     
**Pins to be used:**   
1. Red RGB LED: 23(Wiringpi) or 13(BCM)  

**Demonstration:**       
Run the following command on the terminal:       
```
cd ~/Mosiwi-basic-learning-kit/pi4/c/examples/1.1.0_Blink/     
chmod 777 blink     
sudo ./blink
```
The red LED lights on the expansion board are lit at one-second intervals.    
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/pi4_tutorial/10img.png)     

## Example3 Button   
**Pins to be used:**   
1. Red RGB LED: 23(Wiringpi) or 13(BCM) 
2. Button: 22(Wiringpi) or 6(BCM)  

**Demonstration:**       
Run the following command on the terminal:       
```
cd ~/Mosiwi-basic-learning-kit/pi4/c/examples/1.2.0_Button/     
chmod 777 button     
sudo ./button
```
After uploads the code, the green RGB led on the expansion board is always off, and if the "Button" on the extension board is pressed, the LED is turned on.     
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/pi4_tutorial/11img.png)     


## Example4 Buzzer   
**Pins to be used:**   
1. Buzzer: 1(Wiringpi) or 18(BCM) 

**Demonstration:**       
Run the following command on the terminal:       
```
cd ~/Mosiwi-basic-learning-kit/pi4/c/examples/2.2.0_Buzzer/     
chmod 777 buzzer     
sudo ./buzzer
```
After uploading the code, the buzzer on the expansion board will keep beeping with a fixed frequency and different volumes.       
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/pi4_tutorial/12img.png)     


## Example5 RGB LED   
**Pins to be used:**   
1. Red RGB LED: 23(Wiringpi) or 13(BCM)  
2. Green RGB LED: 24(Wiringpi) or 19(BCM)  
3. Blue RGB LED: 26(Wiringpi) or 12(BCM)  

**Demonstration:**       
Run the following command on the terminal:       
```
cd ~/Mosiwi-basic-learning-kit/pi4/c/examples/2.2.0_Buzzer/     
chmod 777 buzzer     
sudo ./buzzer
```
After uploading the code, the buzzer on the expansion board will keep beeping with a fixed frequency and different volumes.       
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/pi4_tutorial/12img.png)     


## Example6 Fan   
**Pins to be used:**   
1. S1(INB): 23(Wiringpi) or 13(BCM)  
2. S2(INA): 24(Wiringpi) or 19(BCM)  

**Wiring diagram:**   
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/pi4_tutorial/13img.png)     

**Demonstration:**       
Run the following command on the terminal:       
```
cd ~/Mosiwi-basic-learning-kit/pi4/c/examples/2.8.0_Fan_PWM/     
chmod 777 fan_pwm     
sudo ./fan_pwm
```
The fan rotates clockwise and counterclockwise, and the speed changes from small to large, and then from large to small.       
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/pi4_tutorial/14img.png)     


## Example7 Potentiometer      
**Pins to be used:**   
1. SDA: 8(Wiringpi) or 2(BCM)  
2. SCL: 9(Wiringpi) or 3(BCM)   

**Demonstration:**       
Run the following command on the terminal:       
```
cd ~/Mosiwi-basic-learning-kit/pi4/c/examples/1.3.0_Analog_sr/     
chmod 777 analog_sr     
sudo ./analog_sr
```
Push the potentiometer up and down, and the terminal prints the corresponding analog value and voltage value.          
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/pi4_tutorial/15img.png)     
Note: Raspberry Pi4 reads the analog value of the potentiometer through the I2C expansion chip on the "3in1_basic_learning_shield".     

## Example8 Microphone      
**Pins to be used:**   
1. SDA: 8(Wiringpi) or 2(BCM)  
2. SCL: 9(Wiringpi) or 3(BCM)   

**Demonstration:**       
Run the following command on the terminal:       
```
cd ~/Mosiwi-basic-learning-kit/pi4/c/examples/2.3.0_Microphone/     
chmod 777 microphone     
sudo ./microphone
```
After running the code, the terminal prints the analog value of the amplified sound and the voltage value.        
![Img](../../../_static/common_product/C1K0000_4in1_basic_learning_kit/pi4_tutorial/16img.png)     
Note: Raspberry Pi4 reads the analog value of the microphone through the I2C expansion chip on the "3in1_basic_learning_shield".     



**End!**    
  












