# LineCutter-R6

Line cutter, revision 6 (project files are still named r5).

## Contributors

Patrick McGuire, zilinSi

## Status

**Version:** not recorded (the board's title block has no revision)
**Status:** Moved here from CADLab NULIAvionics/Line-Cutters-R6; this folder is now the working copy.

## Description

Line cutter, revision 6 (project files are still named r5).

- KiCad project: `line_cutter_r5.kicad_pro`, last saved with KiCad 7.0
- Schematic sheets: `line_cutter_r5.kicad_sch`, `storage.kicad_sch`, `power.kicad_sch`, `input_prot.kicad_sch`, `mcu.kicad_sch`, `sensors.kicad_sch`, `usb_hub.kicad_sch`, `pyros_servos.kicad_sch`, `pyro_chan.kicad_sch`
- Board size: 61.1 x 30.6 mm
- `fabrication/`: `assembly/`, `bom/`, `gerbers/`, `pick-and-place/`

## Manufacturing

- Layers: 4
- Thickness: 1.606 mm
- Surface finish: not set in the board stackup
- Minimum trace/space: 0.127 mm / 0.127 mm (smallest track on the board / default netclass clearance)
- Minimum drill: 0.305 mm (design rule)
- Manufacturer: not recorded

## Known Issues

- The schematic and PCB are out of sync: 21 parts have a different footprint on the PCB than in the schematic, and 23 schematic parts aren't on the PCB. Run Update PCB from Schematic before the next spin.
- Its library tables also point at `../fcb_v2_lib.kicad_sym` and `../fcb_footprints.pretty`, which weren't in the CADLab repo.

## Revision History

| Version | Date | Changes |
|---|---|---|
| - | 2024-12-06 | Moved into this repo from CADLab NULIAvionics/Line-Cutters-R6 (history from 2024-11-14 to 2024-12-06 stays there) |
