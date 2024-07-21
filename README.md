# JBD-ESP32-Cutoff Charging Logic
A WiFi monitoring/safety cutoff charging solution JBD LFP Packs for use with Dumb chargers.

## Introduction/Intended use cases
Q1: Why use this when I am already using state-of-the-art JBD BMS ?

A1: Li-ion batteries, which by definition LFP/LiFePO4 also is, require specialized chargers with appropriate communication features.
If you're using an ordinary 'DUMB' charger for Lead Acid batteries for your Lithium battery pack, the charger will try to do things
like, equalization, trickle charge that is not required and float at a higher voltage.

A BMS is just a safety device for over/under charge. It will do nothing for improper charging patterns.

A DUMB LeadAcid charger likely has a fixed voltage, constant charging current and no communication.
That is a bad environment for a Lithium pack to be in!
Invest ₹500/$10 in a ESP32 board and have piece of mind that your DIY built battery will last.

Q2. What is your solution to this problem?

A2. Simply prevent the battery from further charging by turning BMS ChargeMOS OFF. And then turn it back ON once the battery discharges a little.
The charging logic does this by monitoring individual cell voltage and detecting proper charge termination/cutoff point.

## Features
### Configurable LFP cutoff current
For example, if your 'dumb' charger has a constant current output of let's say, 10 Amps
then setting a value of 5 Amps for cutoff current will turn ChargeMOS OFF once charging currents tapers to 5A
and max cell voltage rises above 3.45V.

## Material requirements ?

Just an ESP32 WIFI+BT board of your choice and a power supply (USB/GPIO).
For UART version, an additional UART cable is needed.

## Installation
1. Install ESPHome https://esphome.io/guides/installing_esphome.html
2. Get the files
3. Edit the main YAML and configure your requirements by commenting/uncommenting the options.
4. Edit the secrets.yaml files if required for the specific use case.
6. Build/compile & Run the project to flash it on your ESP32 device.

```bash
esphome run esp32-ble-jbd.yaml
```

## Future Improvements
1. Implementing dynamic BMS MAC input after flashing the ESP32.

## References/Credits/Insights
1. https://github.com/syssi/esphome-jbd-bms/blob/main/yaml-snippets/esp32-ble-deepsleep-limit-charging-automation.yaml
2. https://github.com/syssi/esphome-jbd-bms
3. https://github.com/Sleeper85/esphome-jk-bms-can
