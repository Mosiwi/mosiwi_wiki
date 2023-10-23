# O1M0001_fan_module   
--------------------
![Img](../../_static/outsourcing/O1M0001/img/1img.png)    

The electric fan is a device that electrically drives the motor to generate air flow. After the internal motor is energized, it drives the blade to rotate and converts the electric energy into wind energy.     

## Specification          
----------------
1. Operating Voltage: 3 to 5V  
2. Operating Current: less than 100mA      
3. Rotate speed: Max 8300  
9. Dimensions: 35\*27.1mm  

## Dimensional drawing            
----------------------
![Img](../../_static/outsourcing/O1M0001/img/2img.png)  

## Schematic diagram          
--------------------
![Img](../../_static/outsourcing/O1M0001/img/3img.png)  

## Logical table         
----------------
|Input Pin|Input Pin|Output Pin|Output Pin| Motor |
|  :--:   |  :--:   |   :--:   |   :--:   |  :--: |
|   INA   |   INB   |    OA    |    OB    | State |
|    L    |    L    |    L     |    L     | Brake |
|    L    |    H    |    L     |    H     | Positive/reverse turn |
|    H    |    L    |    H     |    L     | Reverse/positive turn |
|    H    |    H    |    H     |    H     | Brake |         

Control fan speed:    
| INA | INB | Direction |
| :--: | :--: | :--: |
| 0 | PWM | Positive/reverse turn |
| PWM | 0 | Reverse/positive turn |

## Example Code           
---------------
**Arduino IDE:**  
Please refer to the link to use Arduino IDE: [Link](../../arduino/arduino_ide/arduino_ide.md)  

**wiring diagram**  
![Img](../../_static/outsourcing/O1M0001/img/4img.png)  

**Digital pin code:**  
```c++
const int ina = 9;            
const int inb = 10;             

void setup() {
   pinMode(ina, OUTPUT);
   pinMode(inb, INPUT);
}

void loop() {
   digitalWrite(ina, HIGH);    
   digitalWrite(inb, LOW);
   delay(2000);
   digitalWrite(ina, LOW);    
   digitalWrite(inb, HIGH);
   delay(2000);
}
```

**PWM pin code:**
```c++
const char ina = 9;            
const char inb = 10;             

void setup() {
   pinMode(ina, OUTPUT);
   pinMode(inb, INPUT);
}

void loop() {
   char i=0;
   for(i=0; i<256; i++>){
      analogWrite(ina, i);    
      analogWrite(inb, 0);
      delay(10);
   }

   for(i=0; i<256; i++>){
      analogWrite(ina, 0);    
      analogWrite(inb, i);
      delay(10);
   }
}
```

--------
**End!**     