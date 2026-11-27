# Battery, energy management and where the control units are (A1 / S1 8X)

**Applies to:** A1 / S1 8X. The S1 (CWZA, quattro) has its battery in the boot and has start/stop, so it has the
full energy management system. A1s without start/stop skip the energy management parts (no battery adaptation,
no LIN alternator). Fuse positions are in [Fuses by colour (RHD)](fuses-rhd-by-colour.md), not repeated here.

## Where the battery is

| Car | Battery | Notes |
|---|---|---|
| S1 | Boot, under the floor panel | Shares its boot layout with A1s from model year 2015 on |
| A1 quattro | Boot | Its own variant: the floor panel comes right out, and the subwoofer is in the way |
| A1 1.2 TFSI | Engine bay, left side | Fuse holder SB sits straight on top of the positive post |
| Other A1s | Boot | Per the A1 launch training material (SSP 477) |

On a boot-battery car:
- The **positive post** carries **fuse holder A (SA)**. Built into it is the **battery isolation igniter N253**, a
  small pyrotechnic charge. When the airbags fire, it cuts the main battery lead. Once it has fired it must be
  replaced, and it is only sold together with SA.
- The main lead runs from the boot to the engine bay. It is aluminium, to save weight.
- The **negative post** carries the earth cable with the **battery monitor control unit J367** (if fitted, and it is
  on start/stop cars).
- A vent hose runs from the battery through a grommet in the body (central gas venting). Refit it whenever the
  battery comes out.

## Jump-starting and charging

You never need to get at the boot battery to jump or charge. There are **remote terminals in the engine bay**:
a positive stud with a flip-up cover and an earth stud, on the same mounting that holds the air cleaner
housing. The launch material places them at the front left (it describes an LHD car), with an earth bolt near the
left strut tower.

- Use the remote terminals for jump leads and for a charger. Leave the boot lid open while charging a boot battery.
- Charge with the battery **still in the car and connected** where you can. J367 only counts the charge that passes
  through it, so a battery charged on the bench comes back with a wrong state of charge.
- For a car left on a charger for a long time (Audi's case is a display car), the *Maintenance* manual asks for a
  charger of at least 30 A, set to no more than 14.8 V.
- **Wet and EFB batteries have a "magic eye".** If it shows clear or pale yellow, don't charge, test or jump the
  battery at all: it can explode. Replace it. AGM batteries have no magic eye.

## Battery type: replace like with like

Three kinds turn up on the 8X: a standard wet battery, **EFB** (enhanced flooded, a wet battery built for
start/stop, used on some A1s from 08.2011) and **AGM** (electrolyte held in a glass mat, sealed). An EFB must be
replaced by an EFB and an AGM by an AGM. The type is printed on the lid. Audi also wants batteries to meet their
TL 82506 / VW 75073 specs.

## After disconnecting or replacing it

Order matters when reconnecting. Positive first, then earth. On cars with J367: **unplug the small J367
connector, fit and tighten the earth clamp, then plug J367 back in.**

Things to do afterwards (from *Electrical system*, Rep. gr. 27, Battery):

| What | Why / how |
|---|---|
| Window one-touch up/down | Has to be re-taught; the owner's manual describes it |
| "Low voltage" faults | Expect them in many control units. Read all fault memories and clear them |
| Date in the cluster | Cars without a radio-controlled clock may lose the date after a long disconnect. Set it in address 17 |
| ESP/TCS warning lamp | May stay lit until the car has rolled a few metres. That is normal |
| **New battery: adapt it** | Energy management (start/stop) cars only, which includes the S1. Gateway J533, **address 19, "Adapt battery"** |

One exception to the usual rule: when working on airbags or belt tensioners, the manual disconnects the earth
lead **with the ignition on**.

The manual does not list steering angle or other resets for a plain battery disconnect. If something else needs
attention, the fault memory will say so.

## Energy management (start/stop cars)

The brain is the **gateway J533**. It is the LIN master for three helpers:

- **J367 battery monitor** (on the negative post): measures battery current through a shunt, battery voltage and
  battery temperature. It has no address of its own; read it through 19.
- **Alternator C** with a LIN regulator: J533 tells it what voltage to make, anywhere from about 12.2 V to 15 V. If
  the LIN message stops, the regulator falls back to a fixed 14.3 V. Non-start/stop cars have a conventional
  regulator instead.
- **Voltage stabiliser J532** (under the front passenger seat): during cranking it holds 12 V for a few consumers
  (cluster, ABS unit, radio and similar), so they don't reset when the starter drags the battery down.

What J533 does with it: it lowers the charge voltage under throttle (the battery carries the load), and raises it
on the overrun to recharge (brake energy recuperation). It also handles **transport mode** (address 19), which
shuts down comfort functions so a stored car will still start. If a car arrives with the radio and other
features restricted, check whether transport mode was left on.

Battery testing differs too: on energy management cars the battery is checked with the diagnostic tester through
J533; on cars without it, Audi uses a separate battery tester.

When testing the alternator, put the dipped beam on: otherwise recuperation can make the reading look low.

## Terminals in plain words

| Terminal | Meaning on this car |
|---|---|
| 30 | Permanent battery positive |
| 31 | Earth |
| 15 | Ignition on. J519 switches the terminal 15 relay |
| 75 | Accessory feed. J519 switches the terminal 75 relay |
| 50 | Starter. The engine ECU J623 drives the starter relays; J519 and J623 both watch it |
| X (75x) | Big comfort loads (the blower, for one), fed through the X-contact relief relay J59 so they can be switched off as a group to take load off the battery |

The manuals name J519's seat-heating enable line as load management, but they don't publish the shedding
stages, so we don't list them here. For a practical terminal X check, see the
[heater fan guide](heater-fan-diagnosis.md).

## Main control units

Locations below are from the workshop manuals and SSP 477, which describe LHD cars. On an RHD car, expect the
driver's-side units to sit on the right; we haven't checked every one. Addresses in *italics* are the standard VAG
diagnostic addresses (as VCDS shows them); the manuals don't list them for the 8X.

| Code | What it does | Where | Address |
|---|---|---|---|
| J533 | Gateway, diagnostics, energy management | Behind the driver's-side dash end cover, in a clip-in frame | 19 |
| J519 | Body control (lights, wipers, heated rear window, terminal 15/75 relays). The A1 has no separate comfort unit | Driver's footwell, behind the relay carrier | *09* |
| J285 | Instrument cluster | Dashboard | 17 |
| J623 | Engine control unit | Engine bay, by the air cleaner housing (the air box comes out first) | 01 |
| J104 | ABS/ESP, built on the hydraulic unit | Engine bay; on the S1 the air box and ECU are moved aside to reach it | *03* |
| J255 | Climatronic, the panel itself | Centre of the dashboard | *08* (see the [heater guide](heater-fan-diagnosis.md)) |
| J492 | Haldex control unit | On the Haldex coupling at the rear final drive | 22 (see the [Haldex guide](haldex-gen5-s1.md)) |
| J500 | Electric power steering | On the steering column | 44 |
| J250 | DCC (adaptive dampers) | Behind the dash at the glove box; side varies | *14* |
| J234 | Airbag | Centre tunnel under the centre console; its earth is through its mounting studs | *15* |
| J386 / J387 | Driver / passenger door units (windows, locks, mirrors) | Inside each front door, behind the trim | *42* / *52* |
| J367 | Battery monitor | Battery negative post | none (via 19) |
| J532 | Voltage stabiliser | Under the front passenger seat | none (via 19) |

When you replace J519, J533, J623, J500, J104 or J250, run "Replace control unit" in the diagnostic tester. A new J533
also has to be coded.

Sources: *Electrical system* (Edition 07.2018), Rep. gr. 27 and 97; *Electrical system, General information*
(Edition 08.2019), Rep. gr. 27; *Maintenance* (Editions 11.2015 and 06.2018); *Running gear, front-wheel drive and
four-wheel drive* (Edition 09.2017), Rep. gr. 43 and 48; *Brake system* (Edition 09.2018), Rep. gr. 45; *General
body repairs, interior* (Edition 01.2015), Rep. gr. 69; *Rear final drive 0AY, 0BR, 0BS, 0CR* (Edition 11.2017),
Rep. gr. 39; *4-cylinder direct injection engine 1.8, 2.0 TFSI gen. III*, Rep. gr. 24; current flow diagrams for
CWZA (start/stop, basic equipment, fuse assignment); *Audi A1 technical introduction*, Self-Study Programme 477.
