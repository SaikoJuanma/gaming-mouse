# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a wireless gaming mouse hardware design project using KiCad 10.0 for PCB/schematic design, with firmware development planned for future implementation.

## Hardware Design (KiCad)

All PCB work lives in `pcb/`. Open the project with KiCad 10.0 via `pcb/mouse-pcb.kicad_pro`.

### Key Components

- **MCU:** Nordic NRF52840-QIAA-R7 (BLE/2.4GHz SoC)
- **Sensor:** PixArt PAW3395-T6QU (gaming motion sensor)
- **RF Antenna:** TDK ANT016008LCS2442MA2 (2.4GHz chip antenna)
- **Connector:** USB-C (HRO TYPE-C-31-M-12)
- **Switch:** Omron D2FC-F-7N20M

### Custom Library

`pcb/mouse_library/` contains all custom KiCad components:
- `mouse_library.kicad_sym` — schematic symbols
- `mouse_library.pretty/` — PCB footprints
- `3d_models/` — 3D visualization models

### PCB Design Rules (from kicad_pro)

- Track widths: 0.156mm (signal), 0.5mm (power)
- Via drill: 0.2mm min, 0.4mm max
- Via diameter: 0.4mm min, 0.6mm max
- Clearance: 0.2mm minimum
- Teardrops enabled for manufacturing robustness

## Firmware

Firmware skeleton is at `firmware/src/main.c` (currently empty). No build system configured yet. The target is Nordic NRF52840, so the firmware will likely use Nordic's nRF5 SDK or Zephyr RTOS with `arm-none-eabi-gcc`.

## Repository Layout

```
pcb/               KiCad project files
pcb/mouse_library/ Custom component library
firmware/src/      Firmware source (not yet started)
```

## .gitignore Notes

The `.gitignore` intentionally excludes most of `pcb/` except:
- `mouse_library/` (custom library)
- `*.kicad_pcb`, `*.kicad_pro`, `*.kicad_sch`, `*.kicad_prl` (design files)

Backup files (`*-backups/`, `.history/`, `*.bak`) are excluded.
