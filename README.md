# Atas Scientific Wi-Fi Aquaponics & Pool Kit for ESPHome

Code for [**Atas Scientific Wi-Fi Aquaponics Kit**](https://atlas-scientific.com/product/wi-fi-aquaponics-kit/) to be compatable with [**ESPHome**](https://esphome.io/) and [**HomeAssistant**](https://www.home-assistant.io/) using [**Adafruit ESP32-S2 TFT Feather**](https://learn.adafruit.com/adafruit-esp32-s2-tft-feather/overview).  
This code will communitcate with all the sensors and send the data to HomeAssistant. The ESP device should be automatically discovered in your HomeAssitant instance once ready. Another .bin file as well as source code for calibration is located on the Releases page for this project.    

Code for [**Atas Scientific Wi-Fi Pool Kit**](https://atlas-scientific.com/kits/wi-fi-pool-kit/) to be compatable with [**ESPHome**](https://esphome.io/) and [**HomeAssistant**](https://www.home-assistant.io/) using [**Adafruit ESP32-S2 TFT Feather**](https://learn.adafruit.com/adafruit-esp32-s2-tft-feather/overview).  
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


![Wi-Fi-aquaponics-kit-01](https://github.com/TheRealFalseReality/Aquaponics-Kit/assets/106857076/defb7d02-b80c-4f63-b4a5-78aa1691ac1f)
![Wi-Fi-pool-kit-01](<img width="1000" height="1000" alt="Wi-Fi-PK-option-02" src="https://github.com/user-attachments/assets/ee020a3a-6408-45cc-8b59-45a682d58c3a" />)


# Installation

## USB
Install via USB here:  
[https://therealfalsereality.github.io/Aquaponics-Kit/](https://therealfalsereality.github.io/Aquaponics_Pool_Kit-AtlasScientific/)

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

To ensure you and other users of the `pool-kit` understand the system status at a glance, I have documented the NeoPixel color codes below.

---

### Status LED Documentation: Pool Kit

The NeoPixel LED provides immediate visual feedback regarding the health and connectivity of your pool controller.

| Color | State | Meaning |
| --- | --- | --- |
| **Purple** | Solid | **System Booting:** The controller is currently powering up and initializing core components. |
| **Blue** | Solid | **Wi-Fi Connected:** The device has successfully joined the local network. |
| **Green** | Solid | **System Ready:** The device is connected to Home Assistant and is fully operational. |
| **Pulsing Red** | Flashing | **Error / Disconnected:** The device has lost its connection to the network or Home Assistant. |

---

### Understanding the Startup Sequence

When you power on the device, it will follow this progression:

1. **Purple:** The initial power-on phase. You will see this for a few seconds while the internal sensors and the SPI bus initialize.
2. **Blue:** Once the device successfully negotiates with your Wi-Fi router, the LED will shift to blue.
3. **Green:** Once the handshake with Home Assistant is confirmed, the LED turns green, indicating that your sensor data is now actively streaming to your dashboard.

### Troubleshooting

If the LED enters a **Pulsing Red** state:

* **Check Wi-Fi:** Ensure your router is online and the `wifi_ssid_iot` credentials are correct.
* **Check Home Assistant:** If the Wi-Fi is active (Blue) but it switches to Pulsing Red, the device is failing to reach the Home Assistant API. Ensure your `api_key` in the YAML matches the integration key in your Home Assistant ESPHome settings.
* **Power Supply:** If the LED does not light up at all at boot, ensure your power supply provides stable 5V, as the NeoPixel requires consistent power to drive its color logic.
