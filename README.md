# Baby Monitor Wearable

This repository contains firmware, hardware design files, and a companion mobile application for a BLE enabled baby monitoring wearable.

## Repository structure

- **Docs** – diagrams and other reference documentation.
- **Firmware** – Zephyr based firmware for the device.
- **PCB** – Eagle schematics and board layout.
- **baby_alert** – Flutter app that displays data and alerts from the monitor.

## Building the firmware

The firmware located in `Firmware/baby_mon` targets Nordic development boards such as the `nrf5340dk_nrf5340_cpuapp` (an overlay for the `adafruit_feather_nrf52840` is also provided). A working Zephyr environment with the Zephyr SDK and `west` tool is required.

1. Install the Zephyr SDK and Python dependencies as described in the [Zephyr documentation](https://docs.zephyrproject.org/latest/getting_started/index.html). Ensure `west` and the SDK are on your path and source `zephyr-env.sh`.
2. From this repository run:

```sh
cd Firmware/baby_mon
west build -b nrf5340dk_nrf5340_cpuapp
```

Replace the board name if building for another supported board.

## Running the Flutter application

The `baby_alert` directory contains the Flutter app used to connect to the device and display alerts. To run it you need Flutter installed and configured.

```sh
cd baby_alert
flutter pub get
flutter run
```

You can also build release binaries using `flutter build` for your chosen platform.

## Supported hardware

The system targets an nRF53/52 series MCU and uses the following sensors and peripherals:

- **MAX32664** biometric sensor hub with an integrated **MAX30102** pulse oximeter
- **MAX30205** temperature sensor
- **APA102** addressable LED strip

