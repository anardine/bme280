# BME280 Sensor Library for AVR Microcontrollers
This Library allows you to communicate with a BME/BMP280 to sense temperature, pressure and humidity (only with BME280) with AVR microcontroller like Atmega328.
Communications use my own I2C library (settings for I2C in i2c.h).

Default settings for sensors are:
standby-time: 250 ms
iir-filter: 8x
temperature oversampling: 16x
pressure oversampling: 16x
humidity oversampling: 16x
mode: normal

If you want to change this settings edit bme280.h (look at /* TODO:...).

Please first confirm if the clock `F_CPU` parameter is correctly set at bme280.h and the makefile.


example source-code:
```
/*************BME280 examble*************/
#include <stdlib.h>
#include "bme280.h"

int main(void){
  // variables for sensor values
  float temperature = 0.0;
  float pressure = 0.0;
  float humidity = 0.0;

  // init i2c
  i2c_init();

  // init sensor
  bme280_init(0);
  // read values
  temperature = bme280_readTemperature(0); // in °C
  pressure = bme280_readPressure(0)/100.0; // in mbar
  humidity = bme280_readHumidity(0); // in %
  
  for(;;){
    // main-loop
  }
  return 0; // never reached
}
```


