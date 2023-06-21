# About

Code for [**Atas Scientific Wi-Fi Aquaponics Kit**](https://atlas-scientific.com/product/wi-fi-aquaponics-kit/) to be compatable with [**ESPHome**](https://esphome.io/) and [**HomeAssistant**](https://www.home-assistant.io/) using [**Adafruit HUZZAH32 – ESP32 Feather Board**](https://www.adafruit.com/product/3405).  
This code will communitcate with all the sensors and send the data to HomeAssistant. The ESP device should be automatically discovered in your HomeAssitant instance once ready. Another .bin file as well as source code for calibration is located on the Releases page for this project.    

**Sensors** for this kit are:  
```
Temperature  
pH   
Conductivity (Salinity)  
Dissolved Oxygen  
Humidity  
CO2 (in air)  
Controlled Doser Pump  
```

![Wi-Fi-aquaponics-kit-01](https://github.com/TheRealFalseReality/Aquaponics-Kit/assets/106857076/defb7d02-b80c-4f63-b4a5-78aa1691ac1f)


# Installation

## USB
Install via USB here:  
https://therealfalsereality.github.io/Aquaponics-Kit/

## ESPHome Web (.bin)
Download latest .bin from [Releases](https://github.com/TheRealFalseReality/Aquaponics-Kit/releases) and install via [ESPHome Web](https://web.esphome.io/)  
You will also see the calibation binary if you need to calibrate the probes.

## From Source
1. Copy the code into ESPHome instance after adding an esp32 device named `Aquaponics Kit`. 
2. Remove the following lines:
```
name_add_mac_suffix: true
```
```
dashboard_import:
  package_import_url: github://TheRealFalseReality/Aquaponics-Kit/aquaponics-kit.yaml@main
```
using source code, you can also customize anything and add your own sensors! Make it your own!
