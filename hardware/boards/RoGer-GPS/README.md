# RoGer-GPS

RoGer GPS board.

## Contributors

irelandhunter

## Status

**Version:** not recorded (the board's title block has no revision)
**Status:** Moved here from CADLab NULIAvionics/RoGer; this folder is now the working copy.

## Description

RoGer GPS board.

- KiCad project: `GPS.kicad_pro`, last saved with KiCad 9.0
- Schematic sheets: `GPS.kicad_sch`
- Board size: 61.0 x 39.5 mm
- No fabrication outputs were in the source repo.

## Manufacturing

- Layers: 4
- Thickness: 1.6 mm
- Surface finish: not set in the board stackup
- Minimum trace/space: 0.157 mm / 0.2 mm (smallest track on the board / default netclass clearance)
- Minimum drill: 0.25 mm (design rule)
- Manufacturer: not recorded

## Known Issues

- Its library tables point at another machine's folders, so KiCad warns about missing libraries; the symbols and footprints stored in the design still open fine, and the parts are in `hardware/common-components/`.

## Revision History

| Version | Date | Changes |
|---|---|---|
| - | 2026-02-07 | Moved into this repo from CADLab NULIAvionics/RoGer (history from 2026-02-07 to 2026-02-07 stays there) |
