# FCB-V3

The third FCB.

## Contributors

Scott A, Patrick McGuire

## Status

**Version:** not recorded (the board's title block has no revision)
**Status:** Moved here from CADLab NULIAvionics/FCB-V3; this folder is now the working copy.

## Description

The third FCB.

- KiCad project: `fcb_v3.kicad_pro`, last saved with KiCad 7.0
- Schematic sheets: `fcb_v3.kicad_sch`, `storage.kicad_sch`, `power.kicad_sch`, `input_prot.kicad_sch`, `periph_pwr.kicad_sch`, `mcu.kicad_sch`, `radio.kicad_sch`, `sensors.kicad_sch`, `umbilical.kicad_sch`, `usb_hub.kicad_sch`, `ble.kicad_sch`, `pyros_servos.kicad_sch`, `pyro_chan.kicad_sch`, `buffers.kicad_sch`, `buzzer.kicad_sch`
- Board size: 101.4 x 50.9 mm
- `fabrication/`: `bom/`, `drill/`, `gerbers/`, `pick-and-place/`

## Manufacturing

- Layers: 4
- Thickness: 1.606 mm
- Surface finish: not set in the board stackup
- Minimum trace/space: 0.127 mm / 0.127 mm (smallest track on the board / default netclass clearance)
- Minimum drill: 0.305 mm (design rule)
- Manufacturer: JLCPCB (the fabrication outputs are JLCPCB's)

## Known Issues

- Y1 (ABS06-32.768KHZ-T, a 2.0x1.2 mm crystal) is placed on KiCad's 3.2x1.5 mm `Crystal_SMD_3215` footprint. The part's own footprint is in `hardware/common-components/ABS06-32.768KHZ-T/`.
- Its library tables point at `../fcb_v2_lib.kicad_sym`, which wasn't in the CADLab repo.

## Revision History

| Version | Date | Changes |
|---|---|---|
| - | 2025-01-15 | Moved into this repo from CADLab NULIAvionics/FCB-V3 (history from 2024-11-13 to 2025-01-15 stays there) |
