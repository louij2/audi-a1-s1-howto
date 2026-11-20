# Heater fan not blowing: diagnosis (S1 / A1 8X with Climatronic)

**Symptom:** the climate panel lights up and responds, the temperature changes, but no air comes out of the vents
at any fan speed. In VCDS, address 08 (Auto HVAC, J255) holds **B10BE "Air Blower - Voltage Implausible"**.
On our car it first showed on a 0 °C cold start.

The fan chain is: Climatronic J255 asks for a speed → the fan final stage **J126** (a power transistor with a heat
sink, behind the glove box) switches the current → the fan motor **V2**. Power comes through a big fuse and the
load-shedding feed (terminal X). Work through it in this order. Each step rules out a part of the chain without
taking anything apart.

## 1. Read what J255 is asking for

VCDS → 08 → Measuring values (Advanced measuring values):

| Value | What we saw | Meaning |
|---|---|---|
| Fresh air blower, specified | follows the panel up and down | J255 is asking correctly |
| Fresh air blower, actual voltage | **0 V the whole time** | nothing reaches the motor |

Specified OK + actual 0 V = **the power side** (fuse, feed, J126, motor or wiring), not the control panel.
You can also run an **output test** of the fan in 08 to command it directly.

## 2. Check the right fuse

The small 10 A fuses for the climate panel are not the fan's power. The fan has its own **40 A fuse**
in the dashboard fuse holder (holder C). On our RHD car it is in the **driver's side** dash end, **black row,
fuse 2**. It also feeds the X-contact relief relay J59. See [Fuses by colour (RHD)](fuses-rhd-by-colour.md).

Ours was not blown.

## 3. Rule out load shedding (terminal X)

The fan normally runs off terminal X (75x), which the body control module cuts when the battery is low
or when relay J59 fails. **Quick split, engine running:** do the heated rear window and the heated seats work?

- **Dead too** → terminal X / J59 / battery load shedding. Check VCDS 09 measuring values (terminal 75x, load
  reduction level) and the battery.
- **They work** (ours did) → the fault is J126, the motor V2, or the plug/wiring between them.

Also worth a look: the scuttle fresh-air intake (leaves) and the plenum drains. Water in the heater box is a
common way to kill J126 and the motor.

## 4. J126 or the motor?

Glove box out (see [the removal guide](cabin-filter-glovebox-blower.md)), then:

1. Look at the J126 and motor plugs: **melted or burnt pins** are common. If you find them, get the pigtail repair
   kit along with the part.
2. Ignition off, spin the fan wheel by hand: stiff or gritty = motor.
3. Command the fan (output test) and tap the motor housing: if it starts, the motor's brushes or bearings are worn.
4. With a multimeter at the motor plug while commanded: **12 V present but no spin = motor**.
   **12 V into J126 but nothing out = J126.**

No meter? J126 is the usual failure on these cars. Order by VIN.

After replacing either part: VCDS 08 → clear faults → **basic setting** → output test.

## Official references

- *Heating, air conditioning*, Rep. gr. 87: fresh-air blower V2 and fresh-air blower control unit J126 (removing and installing).
- Current flow diagrams: fuse assignment (holder C) and the Climatronic diagram.
