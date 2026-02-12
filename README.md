[![KiCad 9](https://img.shields.io/badge/KiCad-9-blue)](https://kicad.org)
[![Schematic v1.1](https://img.shields.io/badge/Sch-v1.1-blueviolet)](kicad/buffer-module.kicad_sch)
[![PCB v1.0](https://img.shields.io/badge/PCB-v1.0-blue)](kicad/buffer-module.kicad_pcb)
[![PCBs: 1](https://img.shields.io/badge/PCBs-1-brightgreen)](kicad/buffer-module.kicad_pcb)
[![Format: Eurorack](https://img.shields.io/badge/Format-Eurorack-0093ff)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)
[![Instagram](https://img.shields.io/badge/Instagram-@moonsofmercury-E4405F?logo=instagram&logoColor=white)](https://www.instagram.com/moonsofmercury/)

# Active Multiple

Active Multiple — a compact active buffered multiple for Eurorack modular synths.

## Contents

- Overview
- Features
- Quick start (KiCad 9)
- Files
- Build & assembly notes
- Testing
- High-level BOM
- License & contributing

## Overview

This repository holds the KiCad 9 project for an active multiple (buffered split). Designed by Dirty Dream — Nathanael Noir — the module accepts audio/CV inputs and provides low-impedance buffered outputs so signals can be split without loading downstream modules.

## Features

- Two independent channels (A & B).
- Per-channel quad buffering using TL074 op-amps (low-noise JFET-input quads).
- 3.5 mm TS jacks (QingPu / Thonkiconn footprint).
- Standard Eurorack power: +12 V / -12 V / GND via a 2x5 (10-pin) header.
- Mostly SMD (surface-mount) components; through-hole only for audio jacks and the Eurorack power header. Assembly is a mixed SMD + THT workflow.

## Quick start

1. Install KiCad 9 (this project was created/edited in KiCad 9).
2. Open the project: `kicad/buffer-module.kicad_pro`.
3. Inspect sheets and ERC, then run CV/PWR checks before exporting fabrication files.

## Files

- `kicad/buffer-module.kicad_sch` — top-level schematic (multi-sheet)
- `kicad/quad buffer.kicad_sch` — quad-buffer sheet (re-used per channel)
- `kicad/Europower +12 -12 GND.kicad_sch` — Eurorack power header sheet
- `kicad/buffer-module.kicad_pcb` — PCB
- `kicad/buffer-module.kicad_pro` — KiCad project file

Note: there is a single PCB layout file (`kicad/buffer-module.kicad_pcb`) for this project.

## Build & assembly notes

- Populate the PCB according to the schematic. Observe TL074 pin-1 orientation.
- Typical footprints:
	- Audio jacks: `AudioJacks2:Jack_3.5mm_QingPu_WQP-PJ398SM_Vertical` (vertical Thonkiconn-style)
	- Power connector: 2x5 Eurorack header (standard 10-pin)
- Add local decoupling (100 nF) on each op-amp power pin pair and bulk caps on rails.
- Double-check power-header orientation with your case header before applying power.

## Testing

1. With no inputs connected, power up and verify rails (+12 V / -12 V) at op-amp supply pins.
2. Feed a low-frequency sine into `Input A` and verify the outputs `OutA/OutB/OutC/OutD` reproduce it cleanly.
3. Connect multiple outputs to confirm splitting works without distortion or level loss.

## High-level BOM

- U1, U2 — TL074 (or compatible quad op-amp)
- J1..J9 — 3.5 mm TS jacks (vertical Thonkiconn/QingPu)
- Jpwr — 2x5 Eurorack power connector
- Resistors, caps, and decoupling components — see schematic for values and placement

For a detailed BOM, use KiCad's BOM export or ask me to generate a CSV from the project files.

### Bill of Materials (detailed)

| Designator(s) | Qty | Value / Part | Footprint | Datasheet |
|---|---:|---|---|---|
| C1, C2 | 2 | 10 µF | Capacitor_SMD:CP_Elec_5x5.4 | [datasheet](https://www.taydaelectronics.com/datasheets/files/a-1677.pdf) |
| C3–C8 | 6 | 100 nF | Capacitor_SMD:C_0805_2012Metric_Pad1.18x1.45mm_HandSolder | [datasheet](https://www.taydaelectronics.com/100nf-50v-smd-ceramic-chip-capacitor.html) |
| D1 | 1 | LED_Dual_A (bi-color) | LED_THT:LED_D3.0mm | [product](https://www.taydaelectronics.com/bi-color-led-3mm-red-green.html) |
| D2 | 1 | LED_Dual_B (bi-color) | LED_THT:LED_D3.0mm | [product](https://www.taydaelectronics.com/bi-color-led-3mm-red-green.html) |
| FB1, FB2 | 2 | Ferrite bead (small) | Inductor_SMD:L_0805_2012Metric_Pad1.05x1.20mm_HandSolder | [datasheet](https://www.taydaelectronics.com/datasheets/files/A-3191.PDF) |
| J1 | 1 | Jack_InA (3.5 mm TS) | AudioJacks2:Jack_3.5mm_QingPu_WQP-PJ398SM_Vertical | [datasheet](https://www.taydaelectronics.com/datasheets/files/w-qp-518ma_drawings.pdf) |
| J2 | 1 | Jack_InB (3.5 mm TS) | AudioJacks2:Jack_3.5mm_QingPu_WQP-PJ398SM_Vertical | [datasheet](https://www.taydaelectronics.com/datasheets/files/w-qp-518ma_drawings.pdf) |
| J3 | 1 | Jack_OutA-1 (3.5 mm TS) | AudioJacks2:Jack_3.5mm_QingPu_WQP-PJ398SM_Vertical | [datasheet](https://www.taydaelectronics.com/datasheets/files/w-qp-518ma_drawings.pdf) |
| J4 | 1 | Jack_OutA-2 (3.5 mm TS) | AudioJacks2:Jack_3.5mm_QingPu_WQP-PJ398SM_Vertical | [datasheet](https://www.taydaelectronics.com/datasheets/files/w-qp-518ma_drawings.pdf) |
| J5 | 1 | Jack_OutA-3 (3.5 mm TS) | AudioJacks2:Jack_3.5mm_QingPu_WQP-PJ398SM_Vertical | [datasheet](https://www.taydaelectronics.com/datasheets/files/w-qp-518ma_drawings.pdf) |
| J6 | 1 | Jack_OutB-1 (3.5 mm TS) | AudioJacks2:Jack_3.5mm_QingPu_WQP-PJ398SM_Vertical | [datasheet](https://www.taydaelectronics.com/datasheets/files/w-qp-518ma_drawings.pdf) |
| J7 | 1 | Jack_OutB-2 (3.5 mm TS) | AudioJacks2:Jack_3.5mm_QingPu_WQP-PJ398SM_Vertical | [datasheet](https://www.taydaelectronics.com/datasheets/files/w-qp-518ma_drawings.pdf) |
| J8 | 1 | Jack_OutB-3 (3.5 mm TS) | AudioJacks2:Jack_3.5mm_QingPu_WQP-PJ398SM_Vertical | [datasheet](https://www.taydaelectronics.com/datasheets/files/w-qp-518ma_drawings.pdf) |
| J9 | 1 | Conn_02x05_Odd_Even (Eurorack power header) | Connector_IDC:IDC-Header_2x05_P2.54mm_Vertical | [datasheet](https://www.taydaelectronics.com/datasheets/files/A-2939.pdf) |
| R1, R6 | 2 | 1 MΩ | Resistor_SMD:R_0805_2012Metric_Pad1.20x1.40mm_HandSolder | [SMD info](https://www.taydaelectronics.com/datasheets/files/SMD.pdf) |
| R2–R4, R7–R9 | 6 | 1 kΩ | Resistor_SMD:R_0805_2012Metric_Pad1.20x1.40mm_HandSolder | [SMD info](https://www.taydaelectronics.com/datasheets/files/SMD.pdf) |
| R5, R10 | 2 | 300 Ω | Resistor_SMD:R_0805_2012Metric_Pad1.20x1.40mm_HandSolder | [SMD info](https://www.taydaelectronics.com/datasheets/files/SMD.pdf) |
| TP1–TP3 | 3 | TestPoint | TestPoint:TestPoint_Pad_D1.5mm | ~ |
| U1, U2 | 2 | TL074 (quad op-amp) | Package_SO:SOIC-14_3.9x8.7mm_P1.27mm | [datasheet](https://www.taydaelectronics.com/datasheets/files/A-1137.PDF) |

## License & contributing

This repository is released under the MIT license. See `LICENSE` for full text.

Contributions, issues, and pull requests welcome. If you publish PCBs or panels based on this design, please credit the original author: Dirty Dream — Nathanael Noir.

---
