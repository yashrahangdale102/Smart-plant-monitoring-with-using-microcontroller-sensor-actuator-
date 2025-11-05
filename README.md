# Smart Plant Monitoring & Auto-Watering (Arduino)

This repository contains a simple Arduino sketch to monitor soil moisture and automatically run a pump through a relay when the soil is dry. It also reads temperature and humidity using a DHT sensor.

Files:
- SmartPlantMonitor.ino â€” main Arduino sketch

Quick overview
- Soil moisture sensor -> analog A0
- DHT11/DHT22 -> digital pin 2
- Relay -> digital pin 8 (controls pump)
- Pump power should be supplied from an external power source and switched using the relay.

How it works
- Reads the soil analog sensor and converts it to a percent (0-100%).
- If moisture falls below configured threshold and cooldown period has passed, the pump runs for a configured duration.
- Hysteresis and a cooldown prevent rapid on/off cycles and repeated watering.

Calibration
1. Upload the sketch and open Serial Monitor (115200).
2. With the sensor completely dry (in air) note the "Soil raw" reading â€” set `sensorDry` to this value.
3. With the sensor completely wet (in water) note the "Soil raw" reading â€” set `sensorWet` to this value.
4. Fine-tune `moistureThreshold`, `pumpDurationMs`, and `pumpCooldownMs` to match your plant/pot size.

Safety
- Use a proper relay rated for your pump current.
- Ensure pump's power and Arduino's power grounds are connected where appropriate (follow relay and pump wiring best practices).
- For mains power pumps, take proper electrical safety precautions.

Customization ideas
- Add an LCD or OLED display for local status.
- Use an ESP8266/ESP32 variant to expose a web UI or MQTT integration.
- Add a water-level sensor to avoid dry-running the pump.
- Log sensor values to an SD card or cloud service.

If you'd like, I can:
- Convert this sketch to an ESP8266/ESP32 web-based controller with a dashboard
- Add MQTT support to push sensor values
- Add water-level monitoring and low-water safety cutoff

``` 
