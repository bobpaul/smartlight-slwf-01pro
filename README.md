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
5. You can flash this to ALL of your AC fobs. On discovery, ESPHome will let you adopt the device to customize it.

(See https://community.home-assistant.io/t/what-is-dashboard-import/422519/7)

# Upstream

Check the downloads tab for latest ESPHome firmware build + YAML files from the device manufacturer.

https://smartlight.me/smart-home-devices/wifi-devices/wifi-dongle-air-conditioners-midea-idea-electrolux-for-home-assistant

# Documentation
[Midea AC for ESPHome](https://esphome.io/components/climate/midea.html)
