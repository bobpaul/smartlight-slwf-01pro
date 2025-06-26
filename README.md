# smartlight-slwf-01pro
ESPHome firmware for the SMARTLIGHT SLWF-01pro with features added to make it easier to adopt via the ESPHome dashboard. This YAML file matches the configuration I use for my Midea U-Shaped window AC units. I use the SLWF-01pro hardware instead of the fob shipped with the midea units for easier integration into Home Assistant. 

(There is an [unstable ESPHome](https://github.com/libretiny-eu/libretiny/issues/44) that can be run on the fob that came with your midea; I've not tried this yet.)

YAML format updated for ESPHome Device Builder addon v2025.6.1

## Steps

1. Add ESP Home Builder to Home Assistant, if you don't already have it
2. Using a Chromium browser, attach to the SLWF-01pro's serial port (usb-c on the side for rev2 boards) and
3. ESP Home Builder will flash a minimal ESPHome and create a yml with OTA password and API password
4. Replace the yaml with the one from this repo (or your fork). Build a firmware.
  - note OTA and API tokens are missing!
5. You can flash this to ALL of your AC fobs. It will be just like they came from the factory and they'll show up with the fallback AP and you can use that to join your wifi.
   On discovery, ESPHome will let you adopt the device to customize it.

## Alt Steps
1. Follow Steps 1-3 above
3. Edit the YAML. It should contain an API key and OTA password. Keep these and merge it with the YAML below. :

```YAML
substitutions:
  name: my-window-ac
  friendly_name: My AC
packages:
  SMLIGHT.SLWF-01Pro: github://bobpaul/smartlight-slwf-01pro/slwf-01pro.yaml@main
esphome:
  name: ${name}
  name_add_mac_suffix: false
  friendly_name: ${friendly_name}

api:
  encryption:
    key: "KEEP THE KEY FROM YOUR PREVIOUS FILE"

wifi:
  ssid: !secret wifi_ssid
  password: !secret wifi_password
  # use_address : 192.x.x.x   # <-- optional: put the IP address here and ESPHome will use this instead of mdns to find the device for OTA flashing. Useful if you want to rename over wifi.

ota:
  - platform: esphome
    password: "KEEP THE PASSWORD"
```

(See https://community.home-assistant.io/t/what-is-dashboard-import/422519/7)

# Upstream

Check the downloads tab for latest ESPHome firmware build + YAML files from the device manufacturer.

https://smartlight.me/smart-home-devices/wifi-devices/wifi-dongle-air-conditioners-midea-idea-electrolux-for-home-assistant

# Documentation
[Midea AC for ESPHome](https://esphome.io/components/climate/midea.html)
