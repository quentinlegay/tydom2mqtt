# Gladys Assistant integration

`tydom2mqtt` is compatible with [Gladys Assistant](https://gladysassistant.com) through the
[**gladys-tydom-v2**](https://github.com/quentinlegay/gladys-tydom-v2) external integration.

```
Tydom gateway <──> tydom2mqtt <──> MQTT broker <──> gladys-tydom-v2 <──> Gladys
```

## How it works

- **tydom2mqtt runs as a Gladys sub-container.** You fill in the usual settings
  (`TYDOM_MAC`, `TYDOM_PASSWORD`, `TYDOM_IP`, `MQTT_HOST`, `MQTT_USER`, `MQTT_PASSWORD`…)
  in the integration configuration, and Gladys starts `tydom2mqtt` for you.
- **Devices are discovered automatically.** The integration relies on the
  [MQTT Discovery](https://www.home-assistant.io/docs/mqtt/discovery/) messages published by
  `tydom2mqtt` and maps each entity to Gladys devices and features.
- **States and commands go through the MQTT broker.**

## Supported devices

| tydom2mqtt entity         | Gladys features                                                 |
| ------------------------- | --------------------------------------------------------------- |
| `cover` (shutter, garage) | shutter state (open / close / stop) + position                  |
| `light`                   | on/off + brightness                                             |
| `switch` (gate, door)     | on/off (sends the toggle impulse)                               |
| `climate`                 | target temperature + temperature sensor                         |
| `sensor`                  | battery, temperature, humidity, power, energy, current, voltage |
| `binary_sensor`           | battery-low, motion                                             |

?> Installation and configuration are documented in the
[gladys-tydom-v2 repository](https://github.com/quentinlegay/gladys-tydom-v2)
([English](https://github.com/quentinlegay/gladys-tydom-v2/blob/main/docs/en.md) ·
[Français](https://github.com/quentinlegay/gladys-tydom-v2/blob/main/docs/fr.md)).
Please report Gladys-specific issues there.
