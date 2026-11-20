# VCDS coding notes (A1 / S1 8X)

**Applies to:** Headlight washer coding: any 8X with headlight washers (A1 and S1, same BCM family). Engine coding and P3019: S1 (CWZA, Simos 18) and other cars with an exhaust flap valve N321.

Results from coding our own S1. **Before you change anything:** save an Auto-Scan, write down the full original
coding of the module, and use the **Long Coding Helper** on the car (the label files for these modules can't be
read offline, so the helper is the only reliable source for bit names). Note every change old → new so you can roll back.

Unlock the car before working on 09 (Central Electronics). With the doors locked it may show as "Cannot be reached".

## Headlight washers off: works

- Module **09** (Central Electronics, J519, BCM PQ35).
- In the Long Coding Helper, untick the **headlight washer** bit. On our car that was **byte 20, bit 5**
  (`0x21 → 0x01`).
- Result: the windscreen washer still works; the headlight jets no longer fire.

## Start/stop off in the BCM: doesn't work

- Module 09, **byte 26, bit 7 "Enabling Start/Stop Function"** (`0x87 → 0x07`). Coding was accepted.
- Result: **no effect**, start/stop still worked. We put the bit back.
- Engine ECU 01, byte 6 bit 0 "Start/Stop System installed": the write was **rejected with error 22
  (conditionsNotCorrect)** on our tuned ECU (VCDS also flagged it as "uninitialised").
- What does work: turning start/stop off in the engine calibration (tune).

## Exhaust flap fault P3019 (N321 open circuit): coding won't fix it

With an aftermarket exhaust and no flap valve, the ECU logs **P3019 00 "Valve for Exhaust Flap 1 (N321) – Open
Circuit"**. In 01, **byte 9, bit 2 "Exhaust Flaps installed"** was already unticked on our car and the fault still
set, so coding doesn't switch the diagnostic off.

Options: disable the N321 fault in the tune, or fit a load resistor in place of the valve on its connector (measure
a real N321 first so the ECU sees the expected resistance). P3019 on its own did **not** request the engine light
on our car (its MIL bit wasn't set). Check the status bits before you blame it for the light.

## Tuned ECUs and coding

A remapped ECU can refuse coding writes (error 22) or show as uninitialised. Don't force it. Put the change in the
tune instead.
