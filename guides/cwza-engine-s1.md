# The S1's 2.0 TFSI (CWZA): what's where, and the common DIY jobs (S1 8X)

**Applies to:** S1 8X with engine code CWZA (2.0 TFSI, EA888 generation III, Simos 18.1 ECU). Other A1 engines
differ. The gen III manuals also cover many non-A1 engine codes, so only the parts that apply to CWZA are here.

This is a map of the engine for owners: the key numbers, the parts that make this engine different from older
2.0 TFSIs, where the sensors you see in fault codes live, and which manual section to open before a job.
It is not a procedure. Look up the workshop manual for torques and steps.

## Key data

| | CWZA |
|---|---|
| Layout | Inline 4, 2.0 l, turbo petrol |
| Rated output / torque | 170 kW / 370 Nm |
| Bore × stroke | 82.5 × 92.8 mm |
| Compression ratio | 9.6 : 1 |
| Camshaft drive | Chain |
| Oil level check | Dipstick |

The engine code is stamped near the front of the engine-to-gearbox joint. A sticker on the top timing chain cover
shows it too.

## What's different about this engine

- **Exhaust manifold cast into the cylinder head.** The coolant diagram shows it as part of the head, so there is
  no separate exhaust manifold.
- **Electric wastegate.** Boost is set by an electric actuator on the turbo, the charge pressure positioner
  **V465**, with its own position sender **G581**. A new V465 must be taught in with the
  "set charge pressure adjuster" function in engine electronics (address 01).
- **Two injectors per cylinder.** The CWZA current flow diagram has the direct injectors (N30-N33) plus a second
  set of port injectors (N532-N535) and a low-pressure fuel sender **G410**. The engine manual treats port injection as one possible version, so lift
  the engine cover and look for the second rail if you need to be sure. The port injectors and G410 sit on
  top of the engine along the intake manifold. The high-pressure pump uses the fuel metering valve **N290** (not N276).

  ![Fuel from the tank delivery unit (pump G6, controlled by J538) splits: one low-pressure feed goes to the port-injection rail with sender G410 and injectors N532-N535, the other to the high-pressure pump with metering valve N290, which feeds the direct-injection rail with sender G247 and injectors N30-N33](../diagrams/cwza-fuel-system.svg)

- **Cam timing on both camshafts.** Inlet control valve **N205** and exhaust control valve **N318** sit in the top
  timing chain cover. The camshaft housing also carries **eight camshaft adjustment actuators** (F366-F373, two
  per cylinder). These are the valve-lift switching actuators on the exhaust camshaft (Audi valvelift system); the
  manuals list them but don't explain them.
- **Chains.** A chain drives the camshafts, a second chain drives the balance shaft, and a separate chain drives
  the oil pump.
- **Two-stage oil pump.** The ECU switches pump pressure with valve **N428**. Pressure switches F22 (blue
  insulation) and F378 (brown) watch it. With N428 unplugged the pump stays in its high stage.
- **Coolant pump in the thermostat housing.** The mechanical pump shares a housing with the engine temperature
  regulation actuator **N493** and is driven by a small toothed belt from the inlet-side balance shaft. The
  coolant diagram also shows an electric after-run pump **V51**, a coolant shut-off valve
  **N82** and, on CWZA only, an auxiliary radiator.
- **Air-to-air intercooler at the front.** It comes out together with the radiator.
- **Sound actuator.** A structure-borne sound actuator R214 with its own control unit J869, and an exhaust flap
  control unit J883.

## Sensors and actuators you'll meet in fault codes

| Code | What it is | Where it sits |
|---|---|---|
| G28 | Engine speed sender (crank) | Low on the engine, reached from below with the front undertray off |
| G40 | Hall sender (camshaft position) | Cylinder head, under the port-injector rail |
| G71 / G42 | Intake manifold pressure + intake air temp (one part) | Clipped into the intake manifold |
| G31 | Charge pressure sender (boost) | Air pipe on the front of the engine, reached from below |
| G247 | Fuel pressure sender, high pressure | On the direct-injection rail |
| G410 | Fuel pressure sender, low pressure | On the port-injection rail, top of manifold |
| N290 | Fuel metering valve | On the high-pressure pump |
| N205 / N318 | Inlet / exhaust camshaft control valve | Top timing chain cover |
| F366-F373 | Camshaft adjustment actuators | On top of the camshaft housing, two per cylinder |
| V465 / G581 | Electric wastegate actuator and its position sender | On the turbo |
| N249 | Turbo air recirculation (diverter) valve | On the turbo |
| N80 | Charcoal canister (EVAP) valve | Top of engine, hose from the oil separator |
| N316 / G336 | Intake manifold flap valve and flap potentiometer | Intake manifold |
| N70, N127, N291, N292 | Ignition coils, cylinders 1-4 | Pencil coils in the cam cover |
| G61 | Knock sensor 1 (the only one on the CWZA diagram) | Under the intake manifold, behind N493 |
| G62 | Coolant temperature sender | Cylinder head, gearbox end |
| G83 | Radiator outlet coolant temperature | In the bottom right radiator hose (CWZA) |
| G39 / G130 | Lambda probe before / after the cat | Exhaust, either side of the catalytic converter |
| J538 | Fuel pump control unit | On the fuel tank flange cover, under the rear seat bench |

The S1 uses the four-wheel-drive fuel tank: a delivery unit with the pump G6, two fuel gauge senders (G and
G169) and a suction-jet pump. Cars built from 2015 have the fuel filter inside the delivery unit; earlier
cars have an external one.

## Common jobs and where to look

**Spark plugs and coils.** Engine cover off, unbolt the earth strap from the coils, unplug them, then pull each
coil with the coil puller (T10530 or a copy). Coils come out more easily with the engine warm. Plugs are
**30 Nm**. Push coils on by hand, never tap them. *Maintenance*, "Spark plugs: renewing", 1.8/2.0 TFSI
version 1; *Servicing 2.0 TFSI EA888 gen III*, Rep. gr. 28.

**Oil and filter.** The filter is a paper cartridge in a screw cap on top of the engine (32 mm socket, cap
**25 Nm**). Cracking the cap open lets the housing drain back to the sump, so wait a few minutes before lifting it
out. A steel sump has a drain plug (**30 Nm**, new seal). A plastic sump has a sealing plug you turn with a coin or
screwdriver. *Maintenance*, "Engine oil" sections; *Servicing ... gen III*, Rep. gr. 17.

**Air filter.** The box sits on a bracket it shares with the jump-start terminal. Unclip the vacuum hose on the
lid, undo the lid screws, swing the lid and its ducts aside, swap the element. Clean leaves and salt out of the
lower half and check the water drain valve at the bottom. *Maintenance*, "Air cleaner: renewing filter element";
*4-cyl. direct injection engine 1.8/2.0 TFSI gen III*, Rep. gr. 24.

**PCV / oil separator.** It bolts to the cylinder head cover. One hose runs to the turbo, one to N80. Coils 3 and 4
must come out first. The gasket and seals are single-use and the bolts are thread-forming, so start them by hand
in the old threads. *Servicing ... gen III*, Rep. gr. 17, Crankcase breather.

**Coolant pump / thermostat housing (N493).** A bigger job: drain the coolant, then the air box, a charge-air pipe
and a row of connectors have to come off before the housing is reachable. Fill with a vacuum
filler and run the coolant bleed routine in guided functions. N493 needs an adaption after renewal. *4-cyl. ... gen
III*, Rep. gr. 19 (A1 prep work), then *Servicing ... gen III*, Rep. gr. 19.

**Boost leaks.** Check every charge-air pipe and hose first. The workshop test pressurises the system from the turbo
outlet at no more than **0.2 bar** and hunts leaks by ear, hand or leak spray. Don't expect it to hold pressure: air
always bleeds past the valves into the engine. Logging boost (G31) against the requested value in
[SimosTools](simostools-s1.md) is a useful first look. *4-cyl. ... gen III* and *Servicing ... gen III*,
Rep. gr. 21, Charge air system.

**Timing chain stretch.** There is no measured-value check in these manuals. The workshop check is mechanical:
remove a sealing plug to see the chain tensioner piston, turn the crankshaft forwards only (24 mm socket)
until the piston is fully out, and count the teeth showing. **Six or fewer: chain OK** (if a chain-elongation fault is stored, run the guided
function "chain elongation adaption diagnosis" and clear it). **Seven or more: new chain.**
The same adaption is also needed after replacing G28, G40, the chain, the camshafts or the head. Use a new sealing
plug. *Servicing ... gen III*, Rep. gr. 15, Chain drive, "Checking timing chain".

![Timing chain check: remove the sealing plug, turn the crank forwards only until the tensioner piston is fully out, count the teeth; six or fewer is OK (adapt and clear any stored chain fault), seven or more means a new chain then the adaption, and always a new sealing plug](../diagrams/timing-chain-check.svg)

## Sources

*Technical data for engines* (Ed. 11.2015); *4-cylinder direct injection engine 1.8, 2.0 ltr. 4-valve TFSI -
generation III* (Ed. 11.2019); *Servicing 4-cylinder engine 2.0 ltr. 4-valve TFSI EA 888 Gen. III*
(Ed. 12.2019); *Fuel supply system, petrol engines* (Ed. 07.2018); *Maintenance* (Ed. 11.2015); current flow
diagram *2.0l petrol engine, CWZA* (from January 2014). All Audi AG workshop information for the A1/S1 8X, used here
for facts only.
