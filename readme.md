# Soehnle air connect ESPHome component

A custom component for ESPHome that uses Bluetooth to connect to Soehnle air purifiers. Component is designed for the [AC500](https://www.amazon.nl/Soehnle-luchtreiniger-verbinding-verwijdert-luchtontvochtiger/dp/B079Q8TG8C).

## Usage

Requires an ESP32 for bluetooth.

Example config:
```yaml

external_components:
  - source: github://RoboMagus/esphome-soehnle-air-connect

ble_client:
  - mac_address: ${AC500_MAC}
    id: ac500

soehnle_air_connect:
  ble_client_id: ac500
  device_id: ac500_device
  name: AC500
  fan_mode:
    name: "fan speed"
  beeper:
    enabled: True
  raw:
    enabled: False
  pm_2_5:
    filters:
      - exponential_moving_average:
          alpha: 0.3
          send_every: 5
  temperature:
    filters:
      - throttle_average: 60s
  power_sensor:
    enabled: True


```