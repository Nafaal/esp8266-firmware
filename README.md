# 'climate' branch
Branch for climate sensor firmware implementation. This firmware sends
temperature, humidity and atmospheric pressure data to cloud each 3 minutes.
Notifications named `climate` and look like
```
{"temperature":24.9375,"humiduty":29,"pressure":998540}
```
Temperature is in Celsius, humidity is in percentages, pressure is in Pascals.
In pauses between cycles esp8266 put's into deep sleep mode to prevent heating
and mismesurement of temperature sesnor. If some sensor are not connected to
chip, result json will be without this sensor field. This implementation uses
DS18B20, DHT11, BMP180 sensors. Sensors pin map: DS18B20->GPIO1, DHT11->GPIO2,
BMP180 SDA->GPIO12, SCL->GPIO14, Powering sensors - GPIO4, WAKE(GPIO16)->RST.
Optionaly DHT22 can be connected to GPIO5, temperature will be taken from that
sensors instedof DS18B20 in this case.
`climate-monitor.html` file is a sample web page for monitoring data from
sensors. Specify DeviceHive server, AccessKey and devices id pattern (part of
deviceid which is common for all devices) and table will print live data from
sensors.

# DeviceHive ESP8266 Firmware
Special firmware for usage ESP8266 in DeviceHive clouds.
This repo consist of few parts of this project which can be used with
other projects. Each project has dedicated readme file.

![](demo-device.jpg?raw=true)
Photo above is a real photo of the demo device contructed with esp8266. See
http://youtu.be/hzi4djt-wdg

# Demo videos
Zero wireless configuring with Android http://youtu.be/2J98YDpbJKo  
BH1750 Ambient light http://youtu.be/AkSFdO0soyo  
DS18B20 + iButton + DHT11 http://youtu.be/IuvxwCPNZCc  
Muscle connected to the cloud http://youtu.be/8L96nBNHE14  
SSD1306 OLED display http://youtu.be/gKgU6RzaxFU  
Multple sensor connection http://youtu.be/hzi4djt-wdg  
Smart socket http://youtu.be/hCdzcCjYYMw  
Wireless Configuring with Mac and Linux http://youtu.be/sFD2TTZNNvo  
BMP180 Atmospheric pressure http://youtu.be/P2rxnVjRPyc  
MPU6050 Accelerometer + Gyroscope http://youtu.be/IRj4tOfLTAM  
MFRC522 RFID Reader http://youtu.be/VMT3v49d57g  
Simple relay http://youtu.be/ZLq2X2n_wR0  

# esp-utils
Simple utils for flashing and connecting to ESP8266.

# examples
Simple web pages with JavaScript sample of sendind recieving command
from device via cloud. Onewire DS18B20 examples use 0x33[SKIP ROM] command
which means that examples work only with one currently connected device. Some
browsers(for example Firefox) block cross domen requests even for local file.
Allow temporary cross domain requests in setting or use another browser to run
examples.

# firmware-src
Sources of DeviceHive ESP8266 firmware.

# firmware-src/genbin.sh
Small utils which is written on bash and can be used on any OS. This util
creates binary firmware files files from crosstool-NG binary file output.

# firmware-tests
Tests for firmware. Youcan find sample of command in file requests.html. Each
addtest() instance have boolean third parameter. If this parameters is true it
means that command and parameters is written correctly and you can use it as
a sample.

# release
Pre built binaries of utils and released firmwares.

# sdk
SDK from chip manufactor. Included in this repo to make sure that we are
using the same version of this SDK to avoid any surprises from changing APIs

# DeviceHiveESP8266commands.pdf
Document contains cloud commands specification for this firmware.

# License
The MIT License. See LICENSE file. Except sdk directory, it has ESPRSSIF MIT 
License, see sdk/License file for details.

# Authors
Nikolay Khabarov
