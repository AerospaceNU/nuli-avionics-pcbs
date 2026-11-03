# PayloadControlBoard

Payload control board V1.

## Contributors

Patrick McGuire, Riley Post

## Status

**Version:** not recorded (the board's title block has no revision)
**Status:** Moved here from CADLab NULIAvionics/Payload-Control-Board; this folder is now the working copy.

## Description

Payload control board V1.

- KiCad project: `payloadV1.kicad_pro`, last saved with KiCad 8.0
- Schematic sheets: `payloadV1.kicad_sch`
- Board size: 77.8 x 52.3 mm
- `3d-models/`: board STEP export
- `fabrication/`: `bom/`, `drill/`, `gerbers/`, `pick-and-place/`

## Manufacturing

- Layers: 4
- Thickness: 1.6 mm
- Surface finish: not set in the board stackup
- Minimum trace/space: 0.157 mm / 0.2 mm (smallest track on the board / default netclass clearance)
- Minimum drill: 0.3 mm (design rule)
- Manufacturer: JLCPCB (the fabrication outputs are JLCPCB's)

## Known Issues

- Its library tables point at another machine's folders, so KiCad warns about missing libraries; the symbols and footprints stored in the design still open fine, and the parts are in `hardware/common-components/`.

## Revision History

| Version | Date | Changes |
|---|---|---|
| - | 2025-05-23 | Moved into this repo from CADLab NULIAvionics/Payload-Control-Board (history from 2024-12-06 to 2025-05-23 stays there) |
