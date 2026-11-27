# SimosTools setup for the S1 (Simos 18.1)

**Applies to:** S1 (CWZA 2.0 TFSI, Simos 18.1). The gearing table is S1-only; the logging, Haldex and dongle notes also apply to other Simos 18 cars.

[SimosTools](https://play.google.com/store/apps/details?id=com.app.simostools) logs and flashes Simos 18 ECUs
through an ESP32 BLE-to-ISO-TP bridge dongle. It has no S1 in its vehicle list, so set these by hand.

## Gearing (the two-final-drive trick)

The S1's 6-speed manual has **two final drives**: 3.944 for gears 1-4 and 3.087 for gears 5-6. SimosTools only
multiplies gear × final, so enter the **overall ratios** and set Final to **1.0**:

| Gear | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|
| Overall ratio | 13.24 | 8.231 | 5.841 | 4.291 | 3.386 | 2.815 |

Leave the vehicle and transmission pickers blank. Picking a car would overwrite these values.

Body values (only used by the accelerometer power estimate): tyre 225/35 R18 = 0.615 m diameter, weight about
1,350 kg, Cd 0.32, frontal area 2.1 m².

## ECU and logging

- Mode 22, 8 PIDs per request, read type SIMOS_18_1 (stock ASW, no patch needed for mode 22).
- **Haldex logging can be turned on.** A gen 5 Haldex answers DIDs 0x2BF0 (axle speed delta), 0x2BF1 (clutch
  temperature) and 0x2BE6/7/9 (pump current, PWM, voltage). Leave newer DIDs your Haldex hasn't answered disabled:
  one unsupported DID can spoil the whole request it's grouped with.
- Useful trigger: start logging on held cruise **or pedal > 70 %**, with a 2 s lead-in and tail.
- Gauge tweaks worth making: boost in bar (the stock metric list still shows psi), battery gauge 10-15 V (it ships
  as 0-2 V), sensible ranges for torque, rpm and turbo speed.
- Leave all the "fast" / experimental flash options off unless you know why you need them.

## Dongle lessons

- If SimosTools connects to the dongle but says **"No ECU reply"**, try another dongle before blaming the car. One of
  our older dongles gave exactly that in the S1 while a freshly flashed one worked fine.
- You can build a spare from a plain ESP32 board with the public BridgeLEG firmware
  ([Switchleg1/esp32-isotp-ble-bridge](https://github.com/Switchleg1/esp32-isotp-ble-bridge)). To get a board
  with no auto-reset circuit into download mode, hold its BOOT button as you plug it in. SimosTools may update the
  bridge firmware itself on first use.
- Back up a dongle's existing flash (`esptool read_flash`) before you overwrite it.
