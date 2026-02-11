# Active Multiple

Active Multiple — an active buffered multiple for Eurorack modular systems.

**Overview**

This project contains schematics and PCB for an active multiple (signal buffer/split) designed by Dirty Dream — Nathanael Noir. The module accepts audio/CV inputs and provides buffered outputs so signals can be safely split with low impedance and minimal loading.

**Key Features**

- Two independent input channels (A and B).
- Each channel is fed to a TL074 quad op-amp used as low-noise buffers and splitters (four outputs per quad buffer sheet available in the schematic).
- Standard 3.5 mm (TS) input/output jacks (QingPu / Thonkiconn-style footprints used in the PCB).
- Standard Eurorack power: +12 V / -12 V / GND via a 2x5 (10-pin) connector.
- Simple, DIY-friendly through-hole and THT component selection for easy assembly.

**Specifications**

- Input impedance: buffered (high) via op-amp inputs
- Output impedance: low (buffered)
- Power: +12 V / -12 V / GND (Eurorack standard)
- Active buffers: TL074 (quad JFET-input op-amp) — compatible TL07x-series recommended

**Files in this repo**

- kicad/buffer-module.kicad_sch — top-level schematic (multiple sheets)
- kicad/quad buffer.kicad_sch — quad-buffer sheet used by the top-level schematic
- kicad/Europower +12 -12 GND.kicad_sch — Eurorack power connector sheet
- kicad/buffer-module.kicad_pcb — PCB layout
- kicad/buffer-module.kicad_pro — KiCad project file

**Build / Assembly Notes**

- Open the project using KiCad (open `kicad/buffer-module.kicad_pro`).
- Populate the board following the schematic: install the TL074 (observe pin 1 orientation), audio jacks (vertical 3.5 mm footprints), power connector (2x5 Eurorack), and decoupling capacitors on V+ / V- rails adjacent to each op-amp.
- Verify footprints: jacks use `AudioJacks2:Jack_3.5mm_QingPu_WQP-PJ398SM_Vertical` (Thonkiconn-style) and the power connector uses a 2x5 connector footprint.
- Before powering, check for shorts between rails and ensure the power connector is wired to the correct orientation for your case.

**Testing**

1. With no inputs connected, power up and verify ±12 V at the rails at the op-amp power pins.
2. Feed a known signal (sine or square) into `Input A` or `Input B` and confirm the outputs (`OutA`, `OutB`, `OutC`, `OutD` per quad buffer sheet) reproduce the signal without level change and with low noise.
3. Test multiple outputs simultaneously to ensure there is no loading or distortion.

**Bill of Materials (high level)**

- U1, U2 — TL074 (quad op-amp) or compatible
- J1..J9 — 3.5 mm TS audio jacks (vertical Thonkiconn/QingPu footprint)
- J(power) — 2x5 Eurorack power connector (standard 10-pin)
- assorted resistors and capacitors (see schematic for exact values)

For a full BOM, generate from KiCad's PCB/BOM tools or consult the `kicad` schematic files.

**License & Attribution**

Designed by Dirty Dream — Nathanael Noir. Please include licensing you prefer (e.g., MIT) if you want to release this project publicly.

**Contact / Notes**

If you'd like, I can generate a full BOM, panel graphic, or assembly instructions next. Open issues or pull-requests are welcome.

