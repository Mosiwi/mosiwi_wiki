# R1K0000_space_station_kit_MicroPython   

## What is MicroPython?
MicroPython is a full implementation of the Python 3 programming language that runs directly on embedded hardware like Raspberry Pi Pico. You get an interactive prompt (the REPL) to execute commands immediately via USB Serial, and a built-in filesystem. The Pico port of MicroPython includes modules for accessing low-level chip-specific hardware.      

Resources (Option):     
1. The [MicroPython Wiki](https://github.com/micropython/micropython/wiki)
2. The [MicroPython Forums](https://forum.micropython.org/)   
3. Basic tutorial kit for MicroPython: [Link](../../../common_product/C1K0000_4in1_basic_learning_kit/Pico_tutorial/microPython_tutorial.md)

## Prepared knowledge    
**Pico and Thonny basics (Important):**     
If you don't have Pico and Thonny basics, you can follow the link to learn the basics: [Click Me](../../../raspberry/R1D0001_raspberry_pico/R1D0001_raspberry_pico.md)    

**Learn about (Option):**      
[**MicroPython for Pico**](https://docs.micropython.org/en/latest/rp2/quickref.html).    

## Upload the space station code to Pico         
**Tools:**     
1. PC(Win10 or uper)     
2. Micro USB cable 

**Download code:**    
Please download the code on Github: <https://github.com/Mosiwi/Mosiwi-space-station-kit-for-pico>     
![Img](../../../_static/raspberry/R1K0000_space_station_kit/2img.png)       
Unzip the file downloaded above, and the file in the "**MicroPython**" folder is the code.       
![Img](../../../_static/raspberry/R1K0000_space_station_kit/micropython/1img.png)   

**Upload module and main code:**    
Make sure your Raspberry PI Pico's USB is plugged into your computer's USB via a usb cable, then click on **"Python"** and the version number in the bottom right corner of the Thonny window, then select "**MicroPython(Raspberry PI Pico)". COMx** ".     
![Img](../../../_static/raspberry/R1K0000_space_station_kit/micropython/5img.png)   

Make sure Thonny checked **"View -> Files"**:  
![Img](../../../_static/raspberry/R1K0000_space_station_kit/micropython/2img.png)    

Select **"Mosiwi_lib_examples"**, then right-click and select the **"Upload to/"** menu to upload the code to Pico:    
![Img](../../../_static/raspberry/R1K0000_space_station_kit/micropython/3img.png)   

Follow the same method to upload the **"main\.py"** file to Pico:    
![Img](../../../_static/raspberry/R1K0000_space_station_kit/micropython/4img.png)   

Run the code offline:         
<span style="color: rgb(255, 76, 65);">If you save a file to the Pico and give it the special name **main\.py**, then MicroPython starts running that script as soon as power is supplied to Raspberry Pi Pico in the future.</span>     

## Assembly steps        
Please refer to: [Link](../assembly/assembly.md)    

## Control space station       
The [previous steps](./microPython_tutorial.md#upload-the-space-station-program-to-pico) have uploaded the code of the space station to Pico. After the space station is installed, the space station can be controlled by the infrared remote control, as follows:       

Function of the key:    
| 1 | 2 | 3 |    
| :--: | :--: | :--: |    
| LED switch | Buzzer switch | Laser switch |      
| 5 | 8 | 0 |     
|door switch | Displays battery power | Display light value |   
| ▲ | ▼ | ◀ |     
| Solar panels turn backwards | Solar panels turn forward | Space station turns left |    
| ▶ | OK |  |    
| Space station turns right | Mode switch |  |    

**Remote mode:** The space station is controlled by infrared remote control.       
![Img](../../../_static/raspberry/R1K0000_space_station_kit/micropython/6img.png)      

**Auto mode:** The space station automatically tracks the direction of the light and uses the brightness of the light to control the LED.     
![Img](../../../_static/raspberry/R1K0000_space_station_kit/micropython/7img.png)       

**End!**    













