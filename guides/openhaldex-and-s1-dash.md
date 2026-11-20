# OpenHaldex and S1 Dash

**Applies to:** S1 and A1 quattro (Haldex). S1 Dash also runs without a Haldex controller on any 8X with an aftermarket Android screen.

## OpenHaldex-C6

An ESP32-C6 controller that sits on the Haldex coupling's CAN line and lets you pick the AWD behaviour
(stock, more rear bias, locked, and so on) from a phone browser. Our fork with the extra features (CLI, PWA,
vehicle geometry, OTA updates) is [louij2/OpenHaldex-C6](https://github.com/louij2/OpenHaldex-C6). The original
project is Forbes Automotive's.

- The S1 8X has a **generation 5 Haldex** (on the 0AY/0BR rear drive). Check which generation the controller has
  detected on the live device instead of assuming.
- Haldex data can also be logged with SimosTools: see [SimosTools setup](simostools-s1.md).

## S1 Dash

An Android app for aftermarket head units and phones that shows cluster-style gauges (boost, oil, coolant,
Haldex clutch temperature), the Haldex mode, fault codes and a logger: [louij2/S1-Dash](https://github.com/louij2/S1-Dash).
Haldex data and mode switching come from the OpenHaldex HTTP API; engine data comes from the same BLE bridge
dongle SimosTools uses.

- Old head units often can't read exFAT. Use a **FAT32** USB stick to sideload the APK.
- Install SimosTools from the Play Store; don't share its APK.
