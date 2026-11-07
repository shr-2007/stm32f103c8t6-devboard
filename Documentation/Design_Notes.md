# Design Notes

## Project
Canal Star Tech — STM32F103C8T6 Development Board

## Current status
- [x] Schematic and PCB designed in KiCad
- [x] Two-layer PCB layout
- [x] Back-copper GND zone
- [x] Ground net visually checked using KiCad net highlighting
- [x] Gerber and drill outputs generated
- [x] Gerber files opened in KiCad Gerber Viewer
- [ ] Final schematic-to-PCB consistency review
- [ ] Final fabrication-focused DRC review
- [ ] Final datasheet-based electrical review
- [ ] Fabricated
- [ ] Hardware bring-up and testing

## Known design notes
- MCU: STM32F103C8T6
- External crystal: 16 MHz (confirm final value and load-capacitor selection from schematic)
- Regulator: AMS1117-3.3 (confirm input voltage, capacitor selection, and thermal limits)
- Intended interfaces: USB, SWD, UART, I²C
- Back copper: GND zone

## Before fabrication
Record the KiCad version, manufacturer design rules, final DRC report, and any intentional DRC exclusions here. An intentional exception should include the affected item, reason, and evidence that the resulting geometry is acceptable.

## Bring-up plan (after fabrication)
1. Inspect the assembled board for shorts and solder bridges.
2. Verify input supply polarity and regulator output/current behaviour.
3. Check reset and boot-mode levels.
4. Connect an ST-Link over SWD and attempt device identification.
5. Flash a minimal GPIO test.
6. Verify clock configuration, then test UART, I²C, and USB separately.
