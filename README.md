# Canal Star Tech - STM32F103C8T6 Development Board

A custom STM32F103C8T6 development-board design created in KiCad as a hands-on electronics and PCB-design learning project.

> **Project status:** Designed in KiCad; not yet fabricated or hardware-tested.
> This repository documents the hardware design and its manufacturing outputs. It does not currently include firmware.

## Overview

The board is built around the **STM32F103C8T6** microcontroller and is intended as a compact platform for learning STM32 development, embedded hardware, and PCB design.

### Intended board features

- STM32F103C8T6 microcontroller
- 16 MHz external high-speed crystal (verify against the final schematic before fabrication)
- USB connectivity
- SWD programming/debug header
- UART header
- I²C header
- 3.3 V regulation using an AMS1117-3.3 regulator
- BOOT0 and reset access
- Front- and back-copper routing on a two-layer PCB
- GND copper zone on the back copper layer

**Important:** Confirm all component values, connector pinouts, USB circuitry, power-input limits, and regulator requirements against the committed schematic and datasheets. The feature list above reflects the current design notes and should be updated if the final schematic differs.

## Repository layout

```text
.
├── Hardware/
│   ├── KiCad/          # Native KiCad project files and required local libraries
│   ├── Gerber/         # Gerber artwork, drill files, and job file
│   └── PDF/            # Schematic PDF and other exported drawings
├── Images/             # PCB renders, layout screenshots, schematic preview
├── Documentation/
│   ├── BOM.csv         # Bill of materials template
│   └── Design_Notes.md # Design decisions and verification notes
├── LICENSE
├── README.md
└── .gitignore
```

## Design files

| Artifact | Location |
|---|---|
| KiCad schematic | `Hardware/KiCad/` |
| KiCad PCB layout | `Hardware/KiCad/` |
| Schematic PDF | `Hardware/PDF/` |
| Gerber files | `Hardware/Gerber/` |
| Excellon drill files (`.drl`) | `Hardware/Gerber/` |
| 3D render and board images | `Images/` |
| Bill of materials | `Documentation/BOM.csv` |


## Interfaces

The design currently provides headers or connections intended for:

| Interface | Purpose |
|---|---|
| USB | USB connectivity |
| SWD | Programming and debugging |
| UART | Serial communication |
| I²C | External peripherals and sensors |
| BOOT0 | Boot-mode selection |
| NRST | Reset |

Refer to the schematic and PCB silkscreen for the exact pin assignments. Do not infer pinouts from connector position alone.

## Design and verification notes

The board has been laid out as a two-layer PCB. The back copper layer contains a GND copper zone. Ground-net highlighting was used during design review to check the intended ground network.

Gerber and drill outputs were generated and opened in KiCad Gerber Viewer for visual inspection.

Before fabrication, perform and record a final review of:

- Schematic-to-PCB consistency (Update PCB from Schematic / comparison)
- Final DRC results, including any intentional exceptions
- Unconnected items
- USB schematic and routing against the STM32F103C8T6 datasheet and USB design guidance
- Crystal placement, load capacitors, and oscillator routing
- BOOT0 and NRST circuitry
- SWD header pinout
- Regulator input/output capacitors, dissipation, and input-voltage limits
- Drill sizes, plated/non-plated hole assignments, and mounting-hole dimensions
- Solder-mask and silkscreen clearances
- Manufacturer capability limits for trace width, spacing, annular ring, and drill size

A clean DRC report is useful, but it does not prove that the circuit is electrically correct or that the board has been hardware-tested.

## Getting started

1. Install KiCad (use a version compatible with the project files).
2. Clone this repository:
   ```bash
   git clone https://github.com/shr-2007/stm32f103c8t6-devboard.git
   cd stm32f103c8t6-devboard
   ```
3. Open the `.kicad_pro` file from `Hardware/KiCad/` in KiCad.
4. Check that any project-specific symbol and footprint libraries resolve correctly.
5. Review the schematic and PCB before making changes.

## Manufacturing outputs

The `Hardware/Gerber/` folder is intended to contain:

- Front and back copper Gerbers
- Front and back solder-mask Gerbers
- Front and back silkscreen Gerbers, if used
- Board outline (`Edge.Cuts`)
- PTH and NPTH Excellon drill files
- Gerber job file

Before sending files to a manufacturer, compress only the required fabrication outputs into a separate ZIP and inspect that ZIP with the manufacturer's Gerber viewer or upload preview. Do not include the native KiCad files in the fabrication ZIP unless the manufacturer specifically requests them.

## License

The hardware design is intended to be released under **CERN Open Hardware Licence Version 2 — Strongly Reciprocal (CERN-OHL-S-2.0)**. See [`LICENSE`](LICENSE).

If you add software, firmware, documentation, images, or third-party assets later, review whether separate licenses or attribution notices are appropriate. Do not assume the hardware license automatically covers third-party assets.

## Credits

Designed as an independent electronics and PCB-design
learning project.

Board branding: Canal Star Tech (fictional project identity).
Designed by: shr-2007.

