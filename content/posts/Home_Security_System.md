---
title: "Home Security System"
date: 2019-08-14T12:46:50-05:00
draft: false
---

In my current CESI101 class we have been playing around with an Arduino mega2560. It is much bigger than the uno with more GPIO pins. The specs for the mega is much larger than the uno and it has RAM and a larger amount of flash memory. It is a nice board, but I’m not sure we couldn’t have done all that we have done using an uno. The actual number of bytes for each code wasn’t really big enough to need the mega’s larger capacity. But hey in the tech kit I got two of them and an ESP32 dev board too! I really can’t complain here. 

Now on to the set up of the security system. The basic plan was to add an RIF sensor and then add a buzzer and or LED that will go off when the RIF senses movement. The RIF sensor is light sensitive and doesn’t work as well in a well-lit room. I had to adjust the sensitivity pretty low so that it would actually go off. Here is the actually code I used for the project.  
int LEDPin =7 ;  
int SensorPin = 8;  
int pinState = LOW;  
int val=0;  

void setup()   
{  
pinMode(LEDPin, OUTPUT);  
pinMode(SensorPin, INPUT);  
}  
void loop() {  
 digitalWrite(SensorPin,LOW);  
  val= digitalRead(SensorPin);  
  if (val == HIGH)  
  {  
    digitalWrite(LEDPin, HIGH);  
    delay(1000);  
    digitalWrite(LEDPin, LOW);   
    delay(1000);  
    }else{  
      digitalWrite(LEDPin, LOW);  
      }  
   }    
  
I actually wrote the code myself since it wasn’t very long and I knew what was going on for the most part. The RIF sensor just uses GND 5V and data so that it can read or rather let the mega know that it senses movement.  
![LEDBuzzerProject](/images/LEDBuzzerProject3.jpg)

I  also added an LCD screen to the whole thing which uses an I2C connection. I actually learned this one a week or so earlier.  
![LEDBuzzerLCD](/images/LEDBuzzerLCD2.jpg)  

 I also added two LEDS one red and one blue so that they flashed like a police car! That was a fun twist too.
<video width="500" heigth="500" controls >
    <source src= "/images/RedBlueLEDSecurity.mp4" type="video/mp4">
    your browser does not support the video tag
</video>
