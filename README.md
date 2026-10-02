# MajorHack KiCad Libraries

Personal KiCad symbol and footprint library — one `Custom` library shared
across my projects, consolidated 2026-10-02 from several previously
per-project copies so there's a single place to find and fix these parts.

## Using it

Add both files to KiCad's library tables (Preferences → Manage Symbol
Libraries / Manage Footprint Libraries, Global scope), nickname `Custom`:

| File | Type |
|------|------|
| `Custom.kicad_sym` | Symbols |
| `Custom.pretty/` | Footprints |

A project that references `Custom:<part>` will resolve it from wherever
you've cloned this repo. Projects distributed without this library still
open and export fine — every part actually used is embedded in the
schematic/PCB file itself — but placing a new instance or doing "Update
from library" needs this repo checked out and registered.

## Symbols (`Custom.kicad_sym`)

| Symbol | Description |
|--------|-------------|
| `AG1170_SIL` | Silvertel Ag1170 SLIC (subscriber line interface circuit) module — 14-pin SIL, analog telephone line driver/hook-switch/ring generator |
| `AG1171_SIL` | Silvertel Ag1171 SLIC module — pin-compatible successor to the Ag1170, same 14-pin SIL footprint |
| `WM8731` | Wolfson/Cirrus WM8731 stereo audio codec, SSOP-28 |
| `BM64SPKS1MC2-0003AA` | Microchip BM64 Bluetooth 5.0 stereo audio module, Class 2, DSPK 2.1.5 firmware, 43-pad SMD with RF shield |
| `Choke_Schaffner_RC212-0.5-10M` | Schaffner RC212 current-compensated (common-mode) choke |

## Footprints (`Custom.pretty/`)

| Footprint | Description |
|-----------|--------------|
| `AG1170_SIL.kicad_mod` | 14-pin single-in-line module footprint, Silvertel Ag1170 SLIC |
| `AG1171_SIL.kicad_mod` | 14-pin single-in-line module footprint, Silvertel Ag1171 SLIC (shared with the Ag1170, pin-compatible) |
| `WM8731_SSOP-28.kicad_mod` | SSOP-28 (JEDEC MO-150, 1.75 mm body), Wolfson/Cirrus WM8731 codec |
| `BM64_MCH.kicad_mod` | 43-pad SMD module footprint, Microchip BM64 Bluetooth module |
| `ESP32-C6-WROOM-1.kicad_mod` | Espressif ESP32-C6-WROOM-1 module, castellated-edge SMD |
| `ESP32-C6-DevKitC-dual.kicad_mod` | ESP32-C6-DevKitC-1 dev board footprint — dual-row through-hole pin headers, all GPIO broken out |
| `ESP32-C6-DevKitC-cheap.kicad_mod` | Pad-compatible footprint for the cheaper AliExpress ESP32-C6 dev board clone (pin assignment differs from the genuine DevKitC on a couple of pads — see the footprint's own notes before swapping one for the other) |
| `RJ12_Amphenol_87180_Horizontal.kicad_mod` | Amphenol 87180-series 6-position modular jack (RJ11/RJ12), horizontal, tab down |
| `AMPHENOL_87180-062LF.kicad_mod` | Amphenol 87180-062LF, the 6P2C member of the same 87180 series, through-hole with 2 mounting posts |
| `PhoenixContact_PT_2,5_3-7,5_H_1x03_7.50mm_Horizontal.kicad_mod` | Phoenix Contact PT 2,5/3-7,5-H 3-pin screw terminal block, 7.5 mm pitch, horizontal |
| `Relay_SPST_TE_T9GS1L14-5.kicad_mod` | TE Connectivity PCH-series SPST (1 Form A) miniature PCB relay |
| `Choke_Schaffner_RC212-7.4x12.7mm.kicad_mod` | Schaffner RC212 common-mode choke, 7.4×12.7 mm body |
| `TestPoint_Pad_4mmx6mm.kicad_mod` | 4 mm SMD test point pad |

## Provenance

Folded together from four sources on 2026-10-02:
- This machine's `6.0/footprints/Scott_Library.pretty` and
  `6.0/symbols/Scott_Library.kicad_sym` (the choke, Phoenix terminal, relay,
  test point)
- A standalone `BM64/` library (the BM64 module symbol + footprint)
- Two per-project `Custom_Symbol_Library.kicad_sym` / `Custom.pretty` /
  `WM8731_lib.kicad_sym` copies, from the
  [Analog Redial](https://github.com/sdylewski/Analog-Redial) ESP32 rotary
  phone project (SLICs, RJ12/Amphenol, ESP32-C6 footprints, WM8731)

Where the same symbol existed in more than one source with differing
content (`AG1171_SIL`, `RJ12_Amphenol_87180_Horizontal`, `WM8731`), the
version actually in use on built/tested hardware was kept.
