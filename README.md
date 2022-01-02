# esphome-sgp40-dht22
  
Using ESPHOME with Home Assistant and a Sensirion SGP40 VOC Sensor with a ESP8266 (NodeMCU in this example)
A fast reactive VOC sensor that does not require a week to warm up and has good stability. Highly recommended.  
  
Link: https://learn.adafruit.com/adafruit-sgp40  
ESPHome: https://esphome.io/components/sensor/sgp40.html  
  
A big thank you to the amazing team working on Home Assistant and ESPHome. This has to be the best smart home solution in the world and exceeds all of the commercial systems out there.  
  
The YAML example code is simply a working version (edit your passwords in) of the code required to get your project started.  
  
This combo project required a bit of extra thinking...  
I was not sure if the humidity and temperature inputs needed to be compatible with the SGP40.  
The datasheet showed that you need a SHT40 (https://www.adafruit.com/product/4885) but it turns out you can use just about any humidity and temperature sensor you can get working.  
So in this example I used a DHT22 (also known as AMS2303 or RHT03) but you could use quite a few different options as the code reads the sensor and transfers the variable into the SGP40 code.  
If you look at the code, you will see how the multi sensor code works.  

ESP8266 (NodeMCU) PINOUT  
ESP PIN D1 to SGP40 SCL  
ESP PIN D2 to SGP40 SCA  
ESP PIN 3.3V to SGP40 VIN  
ESP PIN GND to SGP40 GND  
  
ESP PIN 3.3V to DHT22 PIN1 (VCC)  
ESP PIN GND to DHT22 PIN4 (GND)  
ESP PIN D5 to DHT22 PIN2 (DATA)  

TIP1: The DHT22/RHT03/AMS2303 has a built in resistor from VCC to DATA as a pull up resistor which works just fine but some people recommend either a 10k or 4.7k resistor in addition but I have not used any and it works just fine.  
  
TIP2: In the code there is a section under sensor called 'model' and I had to set this to RHT03 for my sensor to work. My sensor had RHT03 written on it not DHT22.  
Without the correct setting here, I was getting -10'C and 22% humidity which was completely incorrect.  
(Options are: AUTO_DETECT, DHT11, DHT22, DHT22_TYPE2, AM2302, RHT03, SI7021 but AUTO_DETECT didn't work for me)  
Ref: https://esphome.io/components/sensor/dht.html

  
