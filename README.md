# Atas Scientific Wi-Fi Aquaponics Kit for ESPHome

Code for [**Atas Scientific Wi-Fi Aquaponics Kit**](https://atlas-scientific.com/product/wi-fi-aquaponics-kit/) to be compatable with [**ESPHome**](https://esphome.io/) and [**HomeAssistant**](https://www.home-assistant.io/) using [**Adafruit HUZZAH32 – ESP32 Feather Board**](https://www.adafruit.com/product/3405).  
This code will communitcate with all the sensors and send the data to HomeAssistant. The ESP device should be automatically discovered in your HomeAssitant instance once ready. Another .bin file as well as source code for calibration is located on the Releases page for this project.    

**My main project is [AquaPi](https://github.com/TheRealFalseReality/aquapi). These two systems literally use the same hardware, other than the main board, and thus, instead of writing code for each, I actually pull the specfic config from that repo. All instructions for my AquaPi project should apply to this project. Please, read the [AquaPi Wiki](https://github.com/TheRealFalseReality/aquapi/wiki) for calibraion instructions and further, more detailed documentation.**

**Sensors** for this kit are:  
```
RTD - Temperature  
PH - pH   
EC - Conductivity (Salinity)  
DO - Dissolved Oxygen  
HUM - Humidity  
CO2 - CO2 (in air)  
PMP - Controlled Doser Pump  
```

Individual packages that are included by default:
```
packages:
  aquaponics: !include common/aquaponics.yaml
  TheRealFalseReality.device_base: github://TheRealFalseReality/aquapi/common/device_base.yaml
  TheRealFalseReality.ph: github://TheRealFalseReality/aquapi/common/ezo_ph.yaml
  TheRealFalseReality.ec: github://TheRealFalseReality/aquapi/common/ezo_ec.yaml
  TheRealFalseReality.hum: github://TheRealFalseReality/aquapi/common/ezo_hum.yaml
  TheRealFalseReality.rtd: github://TheRealFalseReality/aquapi/common/ezo_rtd.yaml
  TheRealFalseReality.c02: github://TheRealFalseReality/aquapi/common/ezo_co2.yaml
  TheRealFalseReality.pmp: github://TheRealFalseReality/aquapi/common/ezo_pmp.yaml
  # TheRealFalseReality.orp: github://TheRealFalseReality/aquapi/common/ezo_orp.yaml
  # TheRealFalseReality.do: github://TheRealFalseReality/aquapi/common/ezo_do.yaml
  # TheRealFalseReality.debug: github://TheRealFalseReality/aquapi/common/debug.yaml
  # TheRealFalseReality.commands: github://TheRealFalseReality/aquapi/common/ezo_commands.yaml
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
1. Copy the contents of `aquaponics-kit.yaml` into ESPHome instance after adding an esp32 device named `Aquaponics Kit`. 
2. Remove the following lines:
```
name_add_mac_suffix: true
```
```
dashboard_import:
  package_import_url: github://TheRealFalseReality/Aquaponics-Kit/aquaponics-kit.yaml@main
```
using source code, you can also customize anything and add your own sensors! Make it your own!
