# Atas Scientific Wi-Fi Aquaponics & Pool Kit for ESPHome

Code for [**Atas Scientific Wi-Fi Aquaponics Kit**](https://atlas-scientific.com/product/wi-fi-aquaponics-kit/) to be compatable with [**ESPHome**](https://esphome.io/) and [**HomeAssistant**](https://www.home-assistant.io/) using [**Adafruit HUZZAH32 – ESP32 Feather Board**](https://www.adafruit.com/product/3405).  
This code will communitcate with all the sensors and send the data to HomeAssistant. The ESP device should be automatically discovered in your HomeAssitant instance once ready. Another .bin file as well as source code for calibration is located on the Releases page for this project.    

Code for [**Atas Scientific Wi-Fi Pool Kit**](https://atlas-scientific.com/product/wi-fi-aquaponics-kit/) to be compatable with [**ESPHome**](https://esphome.io/) and [**HomeAssistant**](https://www.home-assistant.io/) using [**Adafruit HUZZAH32 – ESP32 Feather Board**](https://www.adafruit.com/product/3405).  
This code will communitcate with all the sensors and send the data to HomeAssistant. The ESP device should be automatically discovered in your HomeAssitant instance once ready. Another .bin file as well as source code for calibration is located on the Releases page for this project.    

**My main project is [AquaPi](https://github.com/TheRealFalseReality/aquapi). These two systems literally use the same hardware, other than the main board, and thus, instead of writing code for each, I actually pull the specfic config from that repo. All instructions for my AquaPi project should apply to this project. Please, read the [AquaPi Wiki](https://github.com/TheRealFalseReality/aquapi/wiki) for calibraion instructions and further, more detailed documentation.**

# How to Learn This Repository

This repository is mostly a thin ESPHome configuration layer on top of shared AquaPi packages from `github://TheRealFalseReality/aquapi/...`.

Recommended reading order:

1. **Start with the board definition** in `/common/espboard.yaml`.  
   Use this as the hardware source of truth during development: this repo is currently targeting **ESP32-S2** (`esp32-s2-saola-1`), even if some product references elsewhere mention S3.

2. **Learn the TFT setup** in `/common/TFT-st7789v.yaml`.  
   This is the display configuration for the ST7789V TFT used by the kit, including SPI pins, backlight power, display control pins, and the render lambda for on-screen sensor values.

3. **Read the two firmware entrypoints**:
   - `/aquaponics-kit.yaml`
   - `/pool-kit.yaml`  
   These are the main configs. Compare their included packages and enabled sensors to understand how the two variants differ.

4. **Read the kit-specific overlays**:
   - `/common/aquaponics.yaml`
   - `/common/pool.yaml`  
   These provide substitutions and board-specific wiring details such as I2C pin assignments and dashboard import behavior.

5. **Treat AquaPi as the shared implementation layer**.  
   Most sensor behavior comes from imported packages like `device_base.yaml`, `ezo_ph.yaml`, `ezo_rtd.yaml`, and related files hosted in the AquaPi repository.

6. **Learn calibration separately** from `/Calibration Configs/README.md`, then inspect the individual calibration YAML files for each probe type.

7. **Learn the release flow last**:
   - `/.github/workflows/ci.yml` builds the YAML configs
   - `/.github/workflows/publish-firmware.yml` publishes firmware artifacts
   - `/.github/workflows/publish-pages.yml` publishes the install page

If you only want the fastest path: read `/common/espboard.yaml` → `/common/TFT-st7789v.yaml` → `/aquaponics-kit.yaml` → `/pool-kit.yaml` → `/Calibration Configs/README.md` → the workflow files.

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
