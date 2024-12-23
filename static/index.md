# Atas Scientific Wi-Fi Aquaponics Kit for ESPHome

Code for [**Atas Scientific Wi-Fi Aquaponics Kit**](https://atlas-scientific.com/product/wi-fi-aquaponics-kit/) to be compatable with [**ESPHome**](https://esphome.io/) and [**HomeAssistant**](https://www.home-assistant.io/) using [**Adafruit HUZZAH32 – ESP32 Feather Board**](https://www.adafruit.com/product/3405) and various EZO sensors.  
This code will communitcate with all the sensors and send the data to HomeAssistant. The ESP device should be automatically discovered in your HomeAssitant instance once ready. Another .bin file as well as source code for calibration is located on the Releases page for this project.    

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


![Wi-Fi-aquaponics-kit-01](https://github.com/TheRealFalseReality/Aquaponics-Kit/assets/106857076/defb7d02-b80c-4f63-b4a5-78aa1691ac1f)


# Installation

## USB
You can use the button below to install the pre-built firmware directly to your device via USB from the browser. Then, while still connected to USB, connect to WiFi, then add to HomeAssisatnt.

Install:
<esp-web-install-button manifest="firmware/aquaponics-kit.manifest.json"></esp-web-install-button>

<script type="module" src="https://unpkg.com/esp-web-tools@9.1.0/dist/web/install-button.js?module"></script>  


## Connect to WiFi via WiFi (After Install)
The device will set up its own hotspot when it cannot connect to a WiFi network. On another device, connect to the `aquaponics-kit` network using `password` (there should be no internet access), then follow the next page that should pop up to enter your WiFi credentials. It should connect and be discoverble in your HomeAssistant instance.


## Connect to WiFi via Bluetooth Improv
*may not always work...*

<script
  type="module"
  src="https://www.improv-wifi.com/sdk-js/launch-button.js"
></script>

<improv-wifi-launch-button></improv-wifi-launch-button>
