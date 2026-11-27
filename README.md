# Audi A1 / S1 (8X) how-to guides

Practical guides for the Audi A1 and S1 (type 8X, 2010-2018), written from hands-on work on a right-hand-drive
S1 quattro (CWZA 2.0 TFSI, 6-speed manual, Haldex gen 5). Most of the car is shared with the A1, so most guides apply
to both: each guide starts with an **Applies to** line.

Everything here is **our own write-up**: what we did, what we measured, what worked and what didn't. Where an
official Audi procedure exists, the guide names the workshop manual and section so you can look it up
(for example *Heating, air conditioning, Rep. gr. 87*). No Audi text, tables or figures are copied.
The guides use facts (sizes, capacities, limits, part codes, locations) learnt from the official manuals,
always written up our own way. Where the manuals leave something to the parts catalogue or your VIN, the guides
say so rather than guess.

Diagrams sit inside the guides, next to the text they explain. They are our own drawings of flows, decisions and
how parts connect. None of them is traced from an Audi figure or wiring diagram. The SVGs are in
[`diagrams/`](diagrams/) and their editable sources in `diagrams/src/`. They were made with
[diagram-design](https://github.com/cathrynlavery/diagram-design).

| Guide | What it covers |
|---|---|
| [Heater fan not blowing: diagnosis](guides/heater-fan-diagnosis.md) | Fault B10BE, VCDS measuring values, the blower fuse, the terminal-X check, J126 vs. motor |
| [Cabin filter, glove box, fan motor and J126](guides/cabin-filter-glovebox-blower.md) | Pollen filter swap (no glove box removal), glove box out, fan V2 and final stage J126 |
| [Fuses by colour (RHD)](guides/fuses-rhd-by-colour.md) | How the dash fuse holders are laid out on a right-hand-drive car, and the heater/AC fuses we verified |
| [VCDS coding notes](guides/vcds-coding-notes.md) | Headlight washer off (works), start/stop off (doesn't), exhaust flap coding vs. P3019, tuned ECUs refusing coding |
| [SimosTools setup for the S1](guides/simostools-s1.md) | Gearing, PIDs, Haldex logging, logging triggers, and the BLE dongle lessons |
| [OpenHaldex and S1 Dash](guides/openhaldex-and-s1-dash.md) | Where to get them and how they fit together |
| [Servicing the S1 (CWZA)](guides/servicing-s1.md) | Service display, oil and filter, plugs, filters, brake fluid, coolant mixing, gearbox/bevel box/diff/Haldex capacities |
| [The S1's 2.0 TFSI (CWZA)](guides/cwza-engine-s1.md) | Key data, what's different on this engine, a fault-code sensor map, common DIY jobs, the timing chain check |
| [Four-wheel drive: Haldex gen 5](guides/haldex-gen5-s1.md) | Driveline layout, gen 5 vs gen 4, J492 wiring, oil change in outline, basic settings, 4WD fault order |
| [Brakes, wheels and DCC](guides/brakes-wheels-dcc-s1.md) | Disc and pad limits by PR code, bleeding with ESP, S1 wheel/tyre sizes, settings after suspension work, adaptive dampers |
| [Battery and control units](guides/battery-and-control-units.md) | Boot battery, jump points, battery adaptation, energy management, terminals, where the main control units are |

## Disclaimer

Not affiliated with or endorsed by AUDI AG. "Audi", "S1", "quattro" and "S tronic" are trademarks of AUDI AG.
You work on your own car at your own risk: airbags, fuel and high-current circuits can hurt you. When in doubt,
follow the official workshop manual (erWin) for your car's build.

Corrections and additions welcome: open an issue or a PR.

## Licence

Text: [CC BY 4.0](LICENSE).
