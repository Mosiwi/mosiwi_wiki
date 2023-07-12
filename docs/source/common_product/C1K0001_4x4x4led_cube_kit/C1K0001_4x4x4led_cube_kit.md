# C1K0001_4x4x4led_cube_kit

## Overview
![Img](../../_static/common_product/C1K0001_4x4x4led_cube_kit/4img.png)  
This is a very interesting light cube that can be used for learning programming or as an ambient light. When used for learning programming, we provide rich sample code such as Arduino, Raspberry pi 4B, and Raspberry pi pico. This light cube also has an excellent feature, which is that multiple light cubes can be connected together in series, and they can be controlled simultaneously or independently using the MCU.    
<span style="color: rgb(255, 76, 65);">(No welding, can be assembled in 10 minutes.)</span>   

## Specification  
1. Operating Voltage: 3.3 to 5V  
2. Operating Current: Max 220mA/1pcs  
3. Interface: 3-Wire or SPI  
4. Lighting frequency: ≥ 50Hz  
5. Weight: about ?g  
6. Dimensions: ?*?*?mm  

## List
|      |      |      |      |
| :--: | :--: | :--: | :--: |
|      |      |      |      |



## Assemble  
**Arduino IDE 2.0.x**  


## Series method  
If you have multiple cubes, you can string them together as follows.    
![Img](../../_static/common_product/C1K0001_4x4x4led_cube_kit/3img.png)    
![Img](../../_static/common_product/C1K0001_4x4x4led_cube_kit/6img.png)

## Download library file
This library package is available for Arduino: UNO and NANO, Raspberry pi 4B, and Raspberry pi pico.  
Download resource: https://github.com/mosiwi/Mosiwi-4x4x4cube  
![Img](../../_static/common_product/C1K0001_4x4x4led_cube_kit/5img.png)  
For Arduino UNO and NANO: C  
For Raspberry pi4: C  
For Raspberry pi pico: Python  

## For Arduino    
**Arduino basics:**  
If you don't have Arduino basics, you can follow the link to learn the basics: [Click Me](../../arduino/A1D0000_uno_r3/A1D0000_uno_r3.md)  

**Wiring diagram:**  
|  UNO or nano  |   Cube   |  
|      :--:     |   :--:   |  
|   5V or 3V3   |   VCC    |  
|      GND      |   GND    |  
|      13       |   SH_C   |  
|      10       |   ST_C   |  
|      11       |   DIN    |  

**Install the Arduino library file:**  
Extract the "Mosiwi-4x4x4cube.zip" file downloaded above into the arduino IDE in the following two ways:    
1. Importing a .zip Library  
2. Manual Installation    

Please refer to the link: <https://www.arduino.cc/en/Guide/Libraries>      

**Use the example code in the library file:**    
If you have successfully loaded the library file, you can open the sample code in the library file in the arduino IDE as follows.   
![Img](../../_static/common_product/C1K0001_4x4x4led_cube_kit/7img.png)   

After opening the sample, select the "Arduino UNO" or "Arduino nano" development board, then select the COMx port, and then upload the code to the development board.  

## For Raspberry pi pico    
**Pico basics:**     
If you don't have Pico basics, you can follow the link to learn the basics: [Click Me](../../raspberry/R1D0001_raspberry_pico/R1D0001_raspberry_pico.md)  
 
**Wiring diagram:**   
|      pico     |   Cube   |  
|      :--:     |   :--:   |   
|  VBUS or 3V3  |   VCC    |  
|      GND      |   GND    |  
|      18       |   SH_C   |  
|      17       |   ST_C   |  
|      19       |   DIN    |   

**Use the pico example code in the library file:**    
Open one of the sample code as follows.  
| 1 | 2 |
|:---:|:---:|
| ![Img](../../_static/common_product/C1K0001_4x4x4led_cube_kit/8img.png) | ![Img](../../_static/common_product/C1K0001_4x4x4led_cube_kit/9img.png) |

Run the code online. (The code is not saved in pico and is not executed after repowering.)    
![Img](../../_static/common_product/C1K0001_4x4x4led_cube_kit/10img.png)

Run the code offline. (The code is stored in pico, and the code in pico is automatically executed after being powered on.)   
| 1 | 2 | 3 |
|:---:|:---:|:---:|
| ![Img](../../_static/common_product/C1K0001_4x4x4led_cube_kit/11img.png) | ![Img](../../_static/common_product/C1K0001_4x4x4led_cube_kit/12img.png) | ![Img](../../_static/common_product/C1K0001_4x4x4led_cube_kit/13img.png) |


## For Raspberry pi4    
**Pi4 basics:**   
If you don't have Pi4 basics, you can follow the link to learn the basics: [Click Me](../../raspberry/R1D0000_raspberry_pi4/R1D0000_raspberry_pi4.md)  
 
**Wiring diagram:**   
|      pi4      |   Cube   |  
|      :--:     |   :--:   |   
|   5V or 3V3   |   VCC    |  
|      GND      |   GND    |  
|      x       |   SH_C   |  
|      x       |   ST_C   |  
|      x       |   DIN    |  



## For Microbit   
**Microbit basics:**   
If you don't have microbit basics, you can follow the link to learn the basics: [Click Me](../../microbit/M1D0000_microbit_mainboard/M1D0000_microbit_mainboard.md)  

**Wiring diagram:**  
|      pi4      |   Cube   |  
|      :--:     |   :--:   |   
|      3V       |   VCC    |  
|      GND      |   GND    |  
|      13       |   SH_C   |  
|      16       |   ST_C   |  
|      15       |   DIN    | 

## Internal operating principle    
**schematic diagram**      
![Img](../../_static/common_product/C1K0001_4x4x4led_cube_kit/1img.png)     
The light cube has 4 layers (F1, F2, F3, F4), each layer has 16 leds with common cathode wiring, which are controlled by 3 74HC595 serial to parallel data chips. Use the MCU's timing interrupt function to turn on and off the leds in each layer (frequency ≥50Hz) to achieve control of all the leds in the cube.    

**Communication data format**    
A data stream:   
| LEDs | LEDs | Layers |  
| :--: | :--: |  :--:  | 
| 16-15-14-13-12-11-10-9 | 8-7-6-5-4-3-2-1 | F1-F2-F3-F4-1-1-1-1 |   
| D0-D1-D2-D3-D4-D5-D6-D7 | D0-D1-D2-D3-D4-D5-D6-D7 | D0-D1-D2-D3-1-1-1-1 |  

"Dx": 0 or 1.  

A data stream entry protocol:  
![Img](../../_static/common_product/C1K0001_4x4x4led_cube_kit/2img.png)  
DIN  = Data_in  
ST_C = ST_clock  
SH_C = Shift_clock, the recommended frequency is less than 25MHz.  

**Timing display format**  
A cube:  
|      t        |      t        |      t        |      t        |      t        |      ....     |      t        |      ....     |  
|     :--:      |     :--:      |     :--:      |     :--:      |     :--:      |      :--:     |     :--:      |      :--:     |  
|    Laye 4     |    Laye 3     |    Laye 2     |    Laye 1     |    Laye 4     |      ....     |    Laye 1     |      ....     |  
| A data stream | A data stream | A data stream | A data stream | A data stream |      ....     | A data stream |      ....     |  

t: MCU timer interrupt time.  
Cube display frequency: It must be ≥ 50Hz, f = 1s/(t \* 4)  

Series multiple cubes:   
|      T        |      T        |     ....      |      T        |      T        |       T       |      ....     |  
|     :--:      |     :--:      |     :--:      |     :--:      |     :--:      |      :--:     |      :--:     |  
|    Cube N     |   Cube N-1    |     ....      |    Cube 2     |    Cube 1     |     Cube N    |      ....     |  

T: The MCU timer displays the time of a cube, T = (t\*4).  
Cube display frequency: It must be ≥ 50Hz, f = 1s/(T \* N)   

End!  



