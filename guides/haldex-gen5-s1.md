# Four-wheel drive on the S1: Haldex gen 5 explained, serviced and diagnosed (S1 8X)

**Applies to:** S1 8X (CWZA 2.0 TFSI, 6-speed manual 0A8 four-wheel drive, built from 2014). The A1 quattro uses the
same rear final drive type but the **older generation 4 coupling**, so the pump, control unit and basic setting notes
don't apply to it. To change how the coupling behaves, see [OpenHaldex and S1 Dash](openhaldex-and-s1-dash.md); to log
it, see [SimosTools setup](simostools-s1.md).

## How the drive gets to the back

1. Engine and clutch into the **0A8** gearbox. On the S1 its code letters are PRY. It has two front final drive ratios:
   3.944 for gears 1-4 and 3.087 for 5th, 6th and reverse.
2. A **bevel box** (the power take-off) mounted on the gearbox's flank sends drive back towards the tunnel. It has
   its own 0.9 litres of oil, kept apart from the gearbox oil.
3. A **one-piece propshaft** runs down the tunnel. The front and rear tubes can't be split, and it rides on a centre
   bearing. At the back, a flexible coupling bolts to the flange on the rear final drive.
4. The **four-wheel drive coupling** (the Haldex) sits on the front of the rear final drive. It decides how much of
   the propshaft's torque gets through to the rear wheels.
5. The **rear final drive** on the S1 is type **0BR** (code letters PQX or PFZ) with a 27:17 ratio (1.588).

Of the four types in the rear final drive manual, only **0BR** is an 8X part (0AY, 0BS and 0CR are Q3 / RS Q3).

## Gen 5 vs gen 4: what's different

You can tell the two apart from the outside:

| | Gen 4 (A1 quattro) | Gen 5 (S1) |
|---|---|---|
| Control unit J492 | bolted to the side, carries the opening valve N373 | bolted to the **front** of the coupling, no separate valve |
| Pump V181 | high-pressure pump with a filter | electric pump, plugs into J492 |
| Pressure accumulator | yes (sealed, never open it) | **none** |

On gen 5 the manual lists just two electrical parts: the control unit and the pump. There's no accumulator, no valve
and no filter to service, so the pressure that closes the coupling comes straight from the electric high-pressure
pump V181, run by J492. The manuals in our set don't go deeper into the control strategy than that.

## The control unit (J492) and its wiring

- **Where:** on the nose of the coupling, at the rear final drive, held by two small bolts (9.5 Nm). The pump's own
  plug goes into J492.
- **Diagnostics:** address **22, "4WD electronics"**. The diagnostic socket is in the driver's footwell next to the
  bonnet release (the manual shows the left-hand-drive car).
- **Bus:** **powertrain CAN**, through the gateway J533. Its main inputs arrive over the bus from the ECU and from
  J104 (ABS/ESP). The manual also lists the accelerator position senders G79/G185 as part of the system.
- **Power and earth** (*Current flow diagram: All-wheel drive, CWZA*, from January 2014). J492 has an 8-pin plug:
  - permanent positive (terminal 30) from fuse 4 on fuse holder C, fuse carrier 2 (1.0 mm² red);
  - ignition positive (terminal 15) from fuse 1 on fuse holder C, fuse carrier 3 (0.35 mm² black);
  - earth (brown) to the earth point on the **left C-pillar**;
  - CAN high and CAN low (orange/black and orange/brown) to the gateway.
- **In-line plug:** the harness also runs through a 6-pin black connector, and the fuel tank removal has you unplug a
  "Haldex coupling" connector beside the left fuel sender flange, under the rear seat bench. The diagram gives no fuse
  ratings; check your car's fuse chart (see [Fuses by colour (RHD)](fuses-rhd-by-colour.md)).

## Oil: what goes where

The coupling and the rear diff have **separate oil circuits**, with separate plugs and different oils. Neither manual
names the oil specification. Both point to the electronic parts catalogue, so order by VIN. Don't use additives, and
don't refill with oil you've drained.

| | Capacity | Plugs (always fit new ones) |
|---|---|---|
| Haldex coupling, gen 5 on 0BR | 0.85 l total, about **0.70 l** at an oil change | drain 38 Nm, filler 15 Nm |
| Rear final drive 0BR (gear oil) | 0.95 l | drain 15 Nm, filler 15 Nm |
| Bevel box on the 0A8 | 0.9 l | drain 20 Nm, filler 20 Nm |

**Interval:** the maintenance manual has a "four-wheel drive coupling: change oil" job that points to Rep. gr. 39.
The interval itself sits in the maintenance tables, which aren't in our copy. Go by your car's service schedule.

**The oil change in outline** (*Rear final drive 0AY, 0BR, 0BS, 0CR*, Rep. gr. 39, high-performance oil for the
four-wheel drive coupling):

- Drain the coupling completely through its own drain plug, then fit a new plug.
- Refilling isn't a squeeze bottle job. The workshop filler (VAS 6291 A) screws an adapter into the filler hole and
  feeds oil by gravity from a raised bottle, hose routed over the driveshaft, until oil spills back out at the adapter.
  Then the bottle is lowered and the surplus drains back. The manual lists extra adapters for the A1 quattro.
- Check the level with the car level and the oil at 20-40 °C (address 22 shows the coupling temperature). It's
  right anywhere from the lower edge of the filler hole down to 3 mm under it.
- The rear diff and the bevel box are checked the same way, but should be full right to the lower edge of the hole.

## After work: basic setting

- **New pump V181:** run the **basic setting** in address 22 (guided functions, four-wheel drive functions).
- **New J492:** run the **"replace control unit"** routine in address 22. It's in the same menu.
- **New rear final drive:** check both the gear oil and the coupling oil levels before the car goes back on the road.

## When 4WD faults show up

The manual's rule is to find the cause with the tester (guided fault finding, self-diagnosis, measuring values)
**before** taking anything off. Our suggested order:

1. Read faults in **22**, but also in the **engine**, **ABS/ESP** and **gateway** control units. J492 depends on
   their data over CAN, so a fault there is worth clearing up before you suspect the coupling.
2. Run the **final control diagnosis** (output test) in 22. On a road test, strap the tester down on the rear seat or
   have someone in the back hold it, never loose up front where an airbag could throw it.
3. Check the two **fuses** in holder C, the **left C-pillar earth**, the plug on J492 and the in-line connector.
4. Check the **coupling oil level** at the right temperature (see above).
5. Replacing the pump or J492? Do the basic setting or replacement routine above, or the fault will stay.

## Propshaft and rear diff, at a high level

- **The propshaft is a sealed unit.** No repairs, and the two halves don't come apart. Before removing it, find the
  factory paint dots on the rear flexible coupling and diff flange (or add your own marks) and refit it in the same
  position, to keep the balance. Keep it straight: support it while it's out and never let it hang from a joint.
- At the front it's **clipped onto the bevel box output shaft**. The circlip and O-ring there are always renewed,
  and the splines get clutch-spline grease. Once it's on, you shouldn't be able to pull it off by hand.
- At the back it slides over a **centring pin** on the diff flange, with a seal inside the propshaft flange. Push it
  on and off square, because a damaged seal means a new propshaft. The flex coupling takes three bolts at 60 Nm.
- Leave the **centre bearing** bolts loose until both ends are on. Let the bearing settle in its slotted holes with no
  load, then tighten (25 Nm).
- On the S1 the **rear final drive** comes out from below by lowering the rear subframe a little (no more than 35 mm)
  on the spindle tools, with the propshaft and driveshafts unbolted. The fuel tank stays in. The diff-to-subframe bolts
  are stretch bolts and must be renewed.
- **Coupling off on its own:** the A1 procedure takes out the tunnel cross-piece, the **fuel tank** and the rear exhaust
  to get at it. You drain the oil, undo four bolts (50 Nm) and slide the coupling out of the diff. It goes back with a
  new oiled O-ring.
- The diff's two driveshaft seals and the propshaft flange seal can be replaced individually. The propshaft flange
  seal's lips get Haldex oil, not grease.
- Whenever the exhaust is split for this work, protect the **flex section of the front pipe**: no bending past 10°
  and no pulling on it.

**Sources:** *Rear final drive 0AY, 0BR, 0BS, 0CR* (edition 11.2017), *6-speed manual gearbox 0A8, four-wheel drive*
(edition 06.2017), *Maintenance* (editions 11.2015 and 06.2018), *Current flow diagram: All-wheel drive, CWZA* (from
January 2014) and *Fuel supply system, petrol engines* (Rep. gr. 20, fuel tank), all Audi A1 2011 ➤.
