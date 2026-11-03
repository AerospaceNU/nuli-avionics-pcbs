# Common components

Every part used on the boards in `hardware/boards/` that isn't in KiCad's standard libraries, one folder each:

```text
<Part>/
├── <Part>.kicad_sym   symbol named <Part>, its Footprint field set to <Part>:<Part>
├── <Part>.kicad_mod   footprint named <Part>
└── <Part>.step        3D model
```

A part that sits on a standard KiCad footprint has only its `.kicad_sym`, its Footprint field pointing at KiCad's
footprint (which brings KiCad's 3D model).

## Using them in KiCad

1. Set a path variable so the footprints find their 3D models: **Preferences → Configure Paths**, add
   `NULI_AVIONICS_COMMON` = the full path to this `common-components` folder.
2. Add a part to a project: **Preferences → Manage Symbol Libraries → Project Specific Libraries**, add
   `<Part>/<Part>.kicad_sym` with nickname `<Part>`; then in **Manage Footprint Libraries**, add the
   `<Part>` folder itself with nickname `<Part>` (KiCad reads a folder of `.kicad_mod` files as a footprint library).

## Where each part came from

Each part was taken from the board it was used on, as placed: the symbol from the schematic, the footprint
from the PCB (exported back to an unrotated, unflipped library footprint), and the 3D model the footprint used.
Every symbol pin has a matching footprint pad. Footprints that had no courtyard got one: the pads, fab and
silkscreen outline plus 0.25 mm.

| Part | Used on | Taken from | STEP | Notes |
|---|---|---|---|---|
| `20021521-00010T1LF` | BasicAltimeter, RoGer-GPS, SAMD21Breakout, SillyGooseV1, VoltV1-PinmapTest | SillyGooseV1 J2 | yes |  |
| `282834-4` | BasicAltimeter, FCB-V3, RoGer-GPS, SillyGooseV1, SillyGooseV2 | SillyGooseV2 J3 | yes |  |
| `282834-6` | SeriousGooseV1 | SeriousGooseV1 J3 | yes |  |
| `4259-63` | RadioBoard-RADIOGAGA | RadioBoard-RADIOGAGA U5 | **missing** |  |
| `ABS06-32.768KHZ-T` | FCB-V3 | FCB-V3 Y1 | yes | FCB-V3's PCB placed this 2.0x1.2mm crystal on a 3.2x1.5mm footprint; this uses the part's own footprint from its library folder; STEP found by part number (ABS06-32.768KHZ-T.step) - check its placement |
| `ABS07-32.768KHZ-T` | BasicAltimeter, LineCutter-R6, RoGer-GPS, SAMD21Breakout, SeriousGooseV1, SillyGooseV1, SillyGooseV2, VoltV1-PinmapTest | SeriousGooseV1 Y1 | yes |  |
| `AON7528` | LineCutter-R6, PayloadControlBoard | PayloadControlBoard Q3 | **missing** | From the Payload schematic (the part isn't on its PCB) |
| `AOZ2261AQI-15` | FCB-V3 | FCB-V3 U22 | **missing** |  |
| `ATSAMD21G18A-MU` | LineCutter-R6 | LineCutter-R6 U2 | yes | From the LineCutter schematic (its PCB is out of sync with it); STEP found by part number (ATSAMD21G18A-MU.step) - check its placement |
| `ATSAMD51P20A-AUT` | FCB-V3, VoltV1-PinmapTest | VoltV1-PinmapTest U1 | yes |  |
| `BLM18PG471SN1D` | RoGer-GPS | RoGer-GPS FL1 | yes | STEP found by part number (BLM18PG471SN1D.step) - check its placement |
| `BOB-09118` | PayloadControlBoard | PayloadControlBoard U8 | yes | SparkFun opto-isolator breakout |
| `BWSMA-KE-P001` | SeriousGooseV1 | SeriousGooseV1 J6 | yes |  |
| `CDMT40D30HF-3R3NC` | FCB-V3 | FCB-V3 L3 | **missing** |  |
| `CFSH05-20L` | PayloadControlBoard | PayloadControlBoard D1 | **missing** |  |
| `CGGBP.18.4.A.02` | FCB-V3 | FCB-V3 AE1 | **missing** |  |
| `CHS-01TA` | SeriousGooseV1, SillyGooseV2 | SeriousGooseV1 SW1 | yes |  |
| `CMI-1295-0585T` | FCB-V3 | FCB-V3 LS1 | **missing** |  |
| `CMT-0525-75-SMT-TR` | BasicAltimeter, SeriousGooseV1, SillyGooseV1, SillyGooseV2 | SeriousGooseV1 LS1 | yes |  |
| `D24V5F3` | PayloadControlBoard | PayloadControlBoard U5 | yes | Pololu 3.3V step-down regulator module |
| `E22-900M30S` | RoGer-GPS | RoGer-GPS U6 | yes | STEP found by part number (E22-900M30S.step) - check its placement |
| `E22-900MM22S` | SeriousGooseV1 | SeriousGooseV1 U7 | yes |  |
| `ECSTXO20CSMV320EYTR` | RadioBoard-RADIOGAGA | RadioBoard-RADIOGAGA Y2 | **missing** |  |
| `FCS0H104ZFTBR24` | LineCutter-R6 | LineCutter-R6 C41 | **missing** |  |
| `FDN306P` | BasicAltimeter, RoGer-GPS, SeriousGooseV1, SillyGooseV1, SillyGooseV2 | SeriousGooseV1 Q3 | yes |  |
| `FEATHER_M0_BASIC_PROTO` | PayloadControlBoard | PayloadControlBoard U1 | yes | Feather-format module; the STEP is the nRF91 Feather model the board used (same outline) |
| `ICM-20948` | LineCutter-R6 | LineCutter-R6 U13 | yes | From the LineCutter schematic (the part isn't on its PCB); STEP found by part number (ICM-20948.step) - check its placement |
| `ICM-20948-Breakout` | PayloadControlBoard | PayloadControlBoard U2 | yes | Adafruit ICM-20948 STEMMA QT breakout |
| `ICM-42605` | SeriousGooseV1, SillyGooseV2 | SeriousGooseV1 MT1 | yes |  |
| `ICM-42688-P` | FCB-V3 | FCB-V3 U14 | KiCad | symbol only - uses KiCad's `Package_LGA:LGA-14_3x2.5mm_P0.5mm_LayoutBorder3x4y` footprint and model |
| `LFD21868MMF1D386` | FCB-V3 | FCB-V3 U8 | **missing** |  |
| `MAX-M10S-00B` | FCB-V3, PayloadControlBoard | PayloadControlBoard U6 | yes |  |
| `MB85RS64V` | BasicAltimeter, SeriousGooseV1, SillyGooseV1, SillyGooseV2 | SeriousGooseV1 U3 | yes |  |
| `ML414H_IV01E` | RoGer-GPS | RoGer-GPS BT2 | yes | STEP found by part number (ML414H_IV01E.step) - check its placement |
| `MountingHole_M2.5_Fixed` | BasicAltimeter, SeriousGooseV1, SillyGooseV1, SillyGooseV2 | SeriousGooseV1 H1 | yes | M2.5 mounting hole with pad; the STEP is the socket-head screw |
| `MS412FE-FL26E` | PayloadControlBoard | PayloadControlBoard BT1 | yes |  |
| `MS8607-Breakout` | PayloadControlBoard | PayloadControlBoard U4 | yes | Adafruit MS8607 breakout |
| `MS860702BA01-50` | LineCutter-R6 | LineCutter-R6 U12 | yes | From the LineCutter schematic (the part isn't on its PCB); STEP found by part number (MS860702BA01-50.step) - check its placement |
| `NP2016DR-N-G` | SeriousGooseV1 | SeriousGooseV1 Q1 | yes |  |
| `PRTR5V0U2X_215` | BasicAltimeter, RoGer-GPS, SAMD21Breakout, SeriousGooseV1, SillyGooseV1, SillyGooseV2, VoltV1-PinmapTest | SeriousGooseV1 D2 | yes |  |
| `PTS810_SJM_250_SMTR_LFS` | BasicAltimeter, RoGer-GPS, SAMD21Breakout, SillyGooseV1, SillyGooseV2, VoltV1-PinmapTest | SillyGooseV2 SW1 | yes |  |
| `RH100-8.000-10-1010-EXT-TR` | FCB-V3 | FCB-V3 Y2 | KiCad | symbol only - uses KiCad's `Crystal:Crystal_SMD_3225-4Pin_3.2x2.5mm` footprint and model |
| `S25FL512SAGMFV010` | BasicAltimeter, FCB-V3, LineCutter-R6, PayloadControlBoard, SeriousGooseV1, SillyGooseV1, SillyGooseV2 | SeriousGooseV1 IC1 | yes |  |
| `SAM-M10Q-00B` | SeriousGooseV1 | SeriousGooseV1 U8 | yes |  |
| `SI7232DN-T1-GE3` | FCB-V3 | FCB-V3 U23 | **missing** |  |
| `SMA-J-P-H-ST-EM1` | RadioBoard-RADIOGAGA, RoGer-GPS | RoGer-GPS J3 | yes | STEP found by part number (SMA-J-P-H-ST-EM1.step) - check its placement |
| `SQJ974EP-T1_GE3` | FCB-V3, LineCutter-R6 | FCB-V3 Q2 | yes |  |
| `SRP5030CA-2R2M` | FCB-V3 | FCB-V3 L4 | yes | STEP is Bourns' SRP5030CA series model from FCB-V3's library - check its placement |
| `TL1015AF160QG` | RadioBoard-RADIOGAGA | RadioBoard-RADIOGAGA MCU_RST1 | **missing** |  |
| `TLV74018PDBVR` | LineCutter-R6 | LineCutter-R6 U1 | KiCad | symbol only - uses KiCad's `Package_TO_SOT_SMD:SOT-23-5` footprint and model; From the LineCutter schematic (its PCB is out of sync with it); KiCad's SOT-23-5 |
| `TPS2115A` | FCB-V3, LineCutter-R6 | FCB-V3 U15 | yes |  |
| `TPS629210DRLR` | SeriousGooseV1 | SeriousGooseV1 U5 | yes |  |
| `TPS630701RNMR` | LineCutter-R6 | LineCutter-R6 U5 | yes |  |
| `TXETBlSANF-40.000` | FCB-V3 | FCB-V3 X1 | KiCad | symbol only - uses KiCad's `Oscillator:Oscillator_SMD_TXC_7C-4Pin_5.0x3.2mm` footprint and model |
| `USB4085-GF-A` | VoltV1-PinmapTest | VoltV1-PinmapTest J1 | yes |  |
| `ZX62-AB-5PA_31_` | BasicAltimeter, RoGer-GPS, SAMD21Breakout, SeriousGooseV1, SillyGooseV1, SillyGooseV2 | SeriousGooseV1 J2 | yes |  |

## Missing 3D models

12 parts had no 3D model anywhere in the boards or their CADLab repos, so their folders have only the
symbol and footprint: `4259-63`, `AON7528`, `AOZ2261AQI-15`, `CDMT40D30HF-3R3NC`, `CFSH05-20L`, `CGGBP.18.4.A.02`, `CMI-1295-0585T`, `ECSTXO20CSMV320EYTR`, `FCS0H104ZFTBR24`, `LFD21868MMF1D386`, `SI7232DN-T1-GE3`, `TL1015AF160QG`.

## Duplicates merged

- `ATSAMD51P20A-AF` (FCB-V3) is the same chip and TQFP-128 package as `ATSAMD51P20A-AUT` (VoltV1-PinmapTest), which has a 3D model - use that one.
- `S25FL512SAGMFA010` (FCB-V3, LineCutter-R6) and PayloadControlBoard's flash are the same SOIC-16 part as `S25FL512SAGMFV010` (four Goose boards) - use that one.
- `MAX-M10S-00B`: FCB-V3 used a MAX-M8C footprint for it; this uses PayloadControlBoard's own MAX-M10S footprint and model.
- Parts used on several boards (`ABS07-32.768KHZ-T`, `ZX62-AB-5PA_31_`, `PTS810_SJM_250_SMTR_LFS`, `PRTR5V0U2X_215`, `FDN306P`, ...) come from the newest board that used them.

## Left out

- **Already in KiCad's libraries** (the boards used a standard symbol and a standard footprint, at most with a different 3D model):
  Molex 73251-1153 SMA, TE 282834-4/-8 terminal blocks (FCB-V3's), JST PH headers, Würth 629105150521 micro-USB,
  Raytac MDBT50Q, MB85RS64, `TestPoint_Pad_D0.5mm`, ICM-20602 on `LGA-16_3x3mm`, ATSAMD51J19A-MU on `QFN-64-1EP_9x9mm`.
- **Wrong:** `NUP2202` on LineCutter-R6 - a 6-pin part on a 4-pad SOT-143 footprint.
- **Wrong pairings from LineCutter-R6's out-of-sync PCB** (ATSAMD21G18A-MU on LGA-14, TLV74018PDBVR on LGA-8, S25FL512 on WSON-8,
  an AON7528 valued BSS138): the parts that are only on LineCutter-R6 were taken from its schematic instead.
