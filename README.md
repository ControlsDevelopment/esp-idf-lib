# ESP-IDF Components library

[![Build Status](https://travis-ci.org/UncleRus/esp-idf-lib.svg?branch=master)](https://travis-ci.org/UncleRus/esp-idf-lib)
[![Docs Status](https://readthedocs.org/projects/esp-idf-lib/badge/?version=latest&style=flat)](https://esp-idf-lib.readthedocs.io/en/latest/)

Components for Espressif ESP32 [ESP-IDF framework](https://github.com/espressif/esp-idf) and [ESP8266 RTOS SDK](https://github.com/espressif/ESP8266_RTOS_SDK).

Most of them ported from [esp-open-rtos](https://github.com/SuperHouse/esp-open-rtos).

## Supported versions

### ESP-IDF

* master
* 4.x
* 3.2.2

### ESP8266 RTOS SDK

* master
* 3.3
* 3.2

Due to incompatibilities in ESP8266 RTOS SDK's SPI driver, the following
libraries are not supported on ESP8266.

* `max7219`
* `mcp23x17`

## How to use

### ESP32

Clone this repository somewhere, e.g.:

```Shell
cd ~/myprojects/esp
git clone https://github.com/UncleRus/esp-idf-lib.git 
```

Add path to components in your project makefile, e.g:

```Makefile
PROJECT_NAME := my-esp-project
EXTRA_COMPONENT_DIRS := /home/user/myprojects/esp/esp-idf-lib/components
include $(IDF_PATH)/make/project.mk
```

or in CMakeLists.txt:

```CMake
cmake_minimum_required(VERSION 3.5)
set(EXTRA_COMPONENT_DIRS /home/user/myprojects/esp/esp-idf-lib/components)
include($ENV{IDF_PATH}/tools/cmake/project.cmake)
project(my-esp-project)
```

### ESP8266 RTOS SDK

Clone this repository somewhere, e.g.:

```Shell
cd ~/myprojects/esp
git clone https://github.com/UncleRus/esp-idf-lib.git
```

Add path to components in your project makefile, e.g:

```Makefile
PROJECT_NAME := my-esp-project
EXTRA_COMPONENT_DIRS := /home/user/myprojects/esp/esp-idf-lib/components
EXCLUDE_COMPONENTS := max7219 mcp23x17
include $(IDF_PATH)/make/project.mk
```

See [GitHub examples](https://github.com/UncleRus/esp-idf-lib/tree/master/examples) or [GitLab examples](https://gitlab.com/UncleRus/esp-idf-lib/tree/master/examples).

## Documentation

If examples is not enough you can read autogenerated documentation: https://esp-idf-lib.readthedocs.io/en/latest/

## Components

### Common drivers

| Component      | Description                                                             | License | Thread safety
|----------------|-------------------------------------------------------------------------|---------|---------------
| **i2cdev**     | I2C utilites                                                            | MIT     | Yes
| **onewire**    | Bit-banging one wire driver                                             | MIT *   | No

### Real-time clocks

| Component      | Description                                                             | License | Thread safety
|----------------|-------------------------------------------------------------------------|---------|---------------
| **ds1302**     | Driver for DS1302 RTC module                                            | BSD     | No
| **ds1307**     | Driver for DS1307 RTC module                                            | BSD     | Yes
| **ds3231**     | Driver for DS1337 RTC and DS3231 high precision RTC module              | MIT     | Yes
| **pcf8563**    | Driver for PCF8563 real-time clock/calendar                             | BSD     | Yes

### Humidity & temperature sensors

| Component      | Description                                                             | License | Thread safety
|----------------|-------------------------------------------------------------------------|---------|---------------
| **dht**        | Driver for DHT11, AM2301 (DHT21, DHT22, AM2302, AM2321), Itead Si7021   | BSD     | No
| **sht31x**     | Driver for Sensirion SHT3x digital temperature and humidity sensor      | BSD     | Yes
| **si7021**     | Driver for Si7013/Si7020/Si7021/HTU21D/SHT2x and compatible             | BSD     | Yes
| **ds18x20**    | Driver for DS18B20/DS18S20 families of one-wire temperature sensor ICs  | BSD     | No
| **max31725**   | Driver for MAX31725/MAX31726 temperature sensors                        | BSD     | Yes
| **lm75**       | Driver for LM75, a digital temperature sensor and thermal watchdog      | ISC     | Yes
| **mcp9808**    | Driver for MCP9808, precision digital temperature sensor                | BSD     | Yes

### Pressure sensors

| Component      | Description                                                             | License | Thread safety
|----------------|-------------------------------------------------------------------------|---------|---------------
| **bmp180**     | Driver for BMP180 digital pressure sensor                               | MIT     | Yes
| **bmp280**     | Driver for BMP280/BME280 digital pressure sensor                        | MIT     | Yes
| **bme680**     | Driver for BME680 digital environmental sensor                          | BSD     | Yes
| **ms5611**     | Driver for barometic pressure sensor MS5611-01BA03                      | BSD     | Yes

### ADC/DAC

| Component      | Description                                                             | License | Thread safety
|----------------|-------------------------------------------------------------------------|---------|---------------
| **ads111x**    | Driver for ADS1113/ADS1114/ADS1115 I2C ADC                              | BSD     | Yes
| **hx711**      | Driver for HX711 24-bit ADC for weigh scales                            | BSD     | Yes
| **mcp4725**    | Driver for 12-bit DAC MCP4725                                           | BSD     | Yes
| **pcf8591**    | Driver for 8-bit ADC and an 8-bit DAC PCF8591                           | BSD     | Yes
| **mcp342x**    | Driver for 18-Bit, delta-sigma ADC MCP3426/MCP3427/MCP3428              | BSD     | Yes

### Power/Current monitors

| Component      | Description                                                             | License | Thread safety
|----------------|-------------------------------------------------------------------------|---------|---------------
| **ina3221**    | Driver for INA3221 shunt and bus voltage monitor                        | MIT     | Yes
| **ina219**     | Driver for INA219/INA220 bidirectional current/power monitor            | BSD     | Yes

### Magnetic sensors

| Component      | Description                                                             | License | Thread safety
|----------------|-------------------------------------------------------------------------|---------|---------------
| **hmc5883l**   | Driver for HMC5883L 3-axis digital compass                              | BSD     | Yes
| **qmc5883l**   | Driver for QMC5883L 3-axis magnetic sensor                              | BSD     | Yes

### Light sensors

| Component      | Description                                                             | License | Thread safety
|----------------|-------------------------------------------------------------------------|---------|---------------
| **bh1750**     | Driver for BH1750 light sensor                                          | BSD     | Yes
| **tsl2561**    | Driver for light-to-digital converter TSL2561                           | BSD     | Yes
| **tsl4531**    | Driver for digital ambient light sensor TSL4531                         | BSD     | Yes

### GPIO expanders

| Component      | Description                                                             | License | Thread safety
|----------------|-------------------------------------------------------------------------|---------|---------------
| **pcf8574**    | Driver for PCF8574 remote 8-bit I/O expander for I2C-bus                | MIT     | Yes
| **pcf8575**    | Driver for PCF8575 remote 16-bit I/O expander for I2C-bus               | MIT     | Yes
| **tca95x5**    | Driver for TCA9535/TCA9555 remote 16-bit I/O expanders for I2C-bus      | BSD     | Yes
| **mcp23008**   | Driver for 8-bit I2C GPIO expander MCP23008                             | BSD     | Yes
| **mcp23x17**   | Driver for I2C/SPI 16 bit GPIO expanders MCP23017/MCP23S17              | BSD     | Yes

### Other

| Component      | Description                                                             | License | Thread safety
|----------------|-------------------------------------------------------------------------|---------|---------------
| **ultrasonic** | Driver for ultrasonic range meters, e.g. HC-SR04, HY-SRF05              | BSD     | No
| **hd44780**    | Universal driver for HD44780 LCD display                                | BSD     | No
| **pca9685**    | Driver for 16-channel, 12-bit PWM PCA9685                               | BSD     | Yes
| **max7219**    | Driver for 8-Digit LED display drivers, MAX7219/MAX7221                 | BSD     | Yes
| **tda74xx**    | Driver for TDA7439/TDA7439DS/TDA7440D audioprocessors                   | MIT     | Yes
| **encoder**    | HW timer-based driver for incremental rotary encoders                   | BSD     | Yes
| **tca9548**    | Driver for TCA9548A/PCA9548A low-voltage 8-channel I2C switch           | BSD     | Yes

## FAQ

### How to debug I2C-based drivers

Common causes of I2C issues are:

* wrong wiring
* wrong pull-up resistors
* wrong I2C address
* broken I2C module
* the driver has a bug

When any of I2C-based drivers does not work, follow the steps below.

Build an _I2C scanner_ device. The device is not necessarily an ESP device.
There are many examples for various platforms. Search by keyword `i2c scanner`.

Connect the I2C module to the I2C scanner device. Make sure appropriate
pull-up registers are connected to `SCL` and `SDA` lines.

Scan devices on the I2C bus. If the scanner does not find the I2C device, then
your wiring might have issues. If the scanner finds the I2C device, make sure
the address found is what the driver expects. If you have more than one same
I2C modules, try them all.

If the scanner finds the I2C device and you are sure that the wiring is
correct, see the signals on the wire using an oscilloscope. Most oscilloscopes
can decode I2C signals and display I2C transactions in human-readable way.

If the driver does not work after these steps, please [let us
know](https://github.com/UncleRus/esp-idf-lib/issues).

### Why are semaphores (mutexes) used in ic2dev routines?

i2cdev uses two types of mutexes: port and transactional.

Port mutexes (there are only two of them, by the number of I2C ports) are
necessary to avoid problems in the situation mentioned in the documentation:

> The I2C APIs are not thread-safe, if you want to use one I2C port in
different tasks, you need to take care of the multi-thread issue.

They are taken before executing single I2C transactions and are released
immediately after them.

Mutexes of the second type are created one per device and are necessary if
the same device is used in several tasks:

```C
static i2c_dev_t some_dev;

void task1 (void * arg)
{
     // some_dev used here
}

void task2 (void * arg)
{
     // and here some_dev used too
}
```

These mutexes are used when single device operation requires several I2C
transactions in a row.

### How can I connect multiple I2C devices?

With i2cdev, you can use almost any way to connect I2C devices.

For example, in the case of using SSD1306 and two MCP3428s, I would recommend
connecting them like this:

- 2 GPIO outputs on ESP32 for dedicated screen connection via I2C bus 0
- 2 GPIO outputs to the second I2C bus, to which 2 MCP3428 are connected with
  different addresses.

If you need to connect more than one sensor with the same addresses and there
are free GPIOs, then you can directly connect these sensors to individual GPIO
outputs instead of using the I2C multiplexer. i2cdev will take care of
reconfiguring I2C driver to the according outputs when you exchange data
with these devices.

## Credits

- [Tomoyuki Sakurai](https://github.com/trombik) developer of the LM75 driver, 
  author of the RTOS SDK ESP82666 support, master of Travis CI
- [Gunar Schorcht](https://github.com/gschorcht), developer of SHT3x and BME680 drivers
- [Brian Schwind](https://github.com/bschwind), developer of TS2561 and TSL4531 drivers
- [Andrej Krutak](https://github.com/andree182), developer of BH1750 driver
- Frank Bargstedt, developer of BMP180 driver
- [sheinz](https://github.com/sheinz), developer of BMP280 driver
- [Jonathan Hartsuiker](https://github.com/jsuiker), developer of DHT driver
- [Grzegorz Hetman](https://github.com/hetii), developer of DS18B20 driver
- [Alex Stewart](https://github.com/astewart-consensus), developer of DS18B20 driver
- [Richard A Burton](mailto:richardaburton@gmail.com), developer of DS3231 driver
- [Bhuvanchandra DV](https://github.com/bhuvanchandra), developer of DS3231 driver
- [Zaltora](https://github.com/Zaltora), developer of INA3231 driver
- [Bernhard Guillon](https://gitlab.com/mrnice), developer of MS5611-01BA03 driver
- [Pham Ngoc Thanh](https://github.com/panoti), developer of PCF8591 driver
