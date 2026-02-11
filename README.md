# Active Multiple

![KiCad 9](https://img.shields.io/badge/KiCad-9-blue)
![Version v1.1](https://img.shields.io/badge/version-v1.1-brightgreen)
![Format: Eurorack](https://img.shields.io/badge/Format-Eurorack-0093ff)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow)
[![Instagram](https://img.shields.io/badge/Instagram-@moonsofmercury-E4405F?logo=instagram&logoColor=white)](https://www.instagram.com/moonsofmercury/)

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

## License & contributing

This repository is released under the MIT license. See `LICENSE` for full text.

Contributions, issues, and pull requests welcome. If you publish PCBs or panels based on this design, please credit the original author: Dirty Dream — Nathanael Noir.

---
