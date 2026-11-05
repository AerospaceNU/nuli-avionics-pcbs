# AvionicsRadioBoardCameras-2026V1

2026 avionics radio board: an ATSAMD21 with an E22-900MM22S LoRa module and SMA antenna connector.

## Contributors

SaiCharan Challapalli

## Status

**Version:** v1.0.0
**Status:** In development - schematic drawn, parts placed, PCB not yet routed

## Description

2026 avionics radio board: an ATSAMD21 (QFN-48) with an E22-900MM22S LoRa module and SMA antenna connector.

- KiCad project: `AvionicsRadioBoardCameras-2026V1.kicad_pro`, last saved with KiCad 10.0
- Schematic sheets: `AvionicsRadioBoardCameras-2026V1.kicad_sch` (single sheet)
- Board size: 76.8 x 50.1 mm
- `libs/`: the board's own symbols, footprints and 3D models
  - `ABS07-32.768KHZ-T/`: crystal symbol and footprints, with its STEP
  - `easyeda2kicad/`: parts imported with easyeda2kicad (E22-900MM22S symbol; footprints for the 8x8 mm inductor,
    mini-USB, SMA connector, SDA01H1SBD switch and the E22 module), with their 3D models
- `3d-models/`: board STEP export
- `fabrication/`: not generated yet (board is not routed)

## Manufacturing

- Layers: 2
- Thickness: 1.6 mm
- Surface finish: not set in the board stackup
- Minimum trace/space: 0.2 mm / 0.2 mm (default netclass)
- Manufacturer: not chosen yet

## Known Issues

From ERC/DRC run with KiCad 10.0.8 on 2026-11-05:

- PCB is not routed (169 unconnected items).
- J6: the schematic symbol's shield pin SH (GND) has no matching pad, and its two mounting PTH pads have no annular ring.
- ERC: two power symbols (#PWR032, #PWR058) are not connected, and one wire has an unconnected end.
- ERC: 16 pin-type warnings (Unspecified pins on the crystal and the E22 module connected to Passive/Bidirectional pins).
- DRC: silkscreen overlaps and silkscreen clipped by the board edge.

## Revision History

| Version | Date | Changes |
|---|---|---|
| v1.0.0 | 2026-11-05 | Added to this repo (in development, unrouted) |
