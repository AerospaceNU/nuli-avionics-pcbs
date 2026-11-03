# VoltV1-PinmapTest

VoltV1 pinmap test board.

## Contributors

Riley Post

## Status

**Version:** not recorded (the board's title block has no revision)
**Status:** Moved here from CADLab NULIAvionics/Volt-Pinmap-Test; this folder is now the working copy.

## Description

VoltV1 pinmap test board.

- KiCad project: `VoltV1 Pinmap Test.kicad_pro`, last saved with KiCad 9.0
- Schematic sheets: `VoltV1 Pinmap Test.kicad_sch`, `mcu.kicad_sch`, `pwr.kicad_sch`
- Board size: 26.1 x 88.0 mm
- No fabrication outputs were in the source repo.

## Manufacturing

- Layers: 4
- Thickness: 1.6 mm
- Surface finish: not set in the board stackup
- Minimum trace/space: 0.15 mm / 0.15 mm (smallest track on the board / default netclass clearance)
- Minimum drill: 0.3 mm (design rule)
- Manufacturer: not recorded

## Known Issues

- Its library tables point at another machine's folders, so KiCad warns about missing libraries; the symbols and footprints stored in the design still open fine, and the parts are in `hardware/common-components/`.

## Revision History

| Version | Date | Changes |
|---|---|---|
| - | 2025-08-10 | Moved into this repo from CADLab NULIAvionics/Volt-Pinmap-Test (history from 2025-08-10 to 2025-08-10 stays there) |
