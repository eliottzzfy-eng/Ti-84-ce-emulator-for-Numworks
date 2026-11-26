# Ti-84-ce-emulator-for-Numworks
A TI-84 CE emulator for numworks !
# cemu-numworks

A port of the [CEmu](https://github.com) TI-84 Plus CE emulator core to **NumWorks** graphing calculators (built as a standalone `.nwa` external application).

> **Note:** This repository contains **only** the open-source emulator core and NumWorks platform wrapper. **No Texas Instruments ROM, OS, or copyrighted files are included.**

---

## Features

- **Full eZ80 Emulation:** Runs the TI-84 Plus CE operating system and native/TI-BASIC programs on NumWorks hardware using CEmu's C emulation engine.
- **Native 320×240 Color Output:** Renders the TI-84 Plus CE screen pixel-for-pixel onto the NumWorks 320×240 RGB565 LCD.
- **Zero-RAM ROM Mapping:** Reads your TI-84 Plus CE ROM directly from memory-mapped external QSPI Flash via EADK external data (`eadk_external_data`).
- **Standalone `.nwa` App:** Runs directly on stock Epsilon firmware without requiring custom firmware or hardware modifications.

---

## Legal & ROM Notice

This project is licensed under the **GNU General Public License v3.0 (GPL-3.0)**, matching upstream [CEmu](https://github.com).

- **No ROM Included:** You must supply your own `.rom` image legally dumped from a TI-84 Plus CE calculator that you personally own. Do not open issues or pull requests requesting or linking to TI ROM files.
- **No Affiliation:** This is an independent community project and is not affiliated with, endorsed by, or sponsored by Texas Instruments or NumWorks. *TI-84 Plus CE* is a trademark of Texas Instruments Incorporated. *NumWorks* is a trademark of NumWorks SAS.

---

## Requirements

### Hardware
- **NumWorks Calculator:** Designed for the **N0120** (STM32H725 with 564 KB SRAM and 8 MB external Flash).
- **TI-84 Plus CE ROM:** A valid `.rom` dump from your own calculator.

---

## Installation

1. **Get the `.nwa` binary:**
   - Download `cemu-numworks.nwa` from the [Releases](../../releases) page (or build it from source below).
2. **Prepare your TI-84 Plus CE ROM:**
   - Use a ROM dump from your own TI-84 Plus CE calculator.
   - *(Optional)* If your Epsilon version enforces an external data size limit (~1.9–2.5 MB), trim unused upper `0xFF` archive sectors from your `.rom` file before uploading.
3. **Install onto your NumWorks:**
   - Connect your NumWorks calculator via USB.
   - Open the [NumWorks External App Uploader](https://numworks.com) in a WebUSB-compatible browser (such as Chrome or Edge) or use `nwlink`.
   - Select `cemu-numworks.nwa` as the application file and attach your TI-84 Plus CE `.rom` file as the **external data** file.
   - Flash the app and launch **TI-84 CE** from your NumWorks home screen.
   - # make sure you did the [nwagra](https://nwagyu.org/fr/guide/help/enlarge-your-memory.html) tutorial before installing or you're not gonna have enough storage

---

## Controls & Key Mapping

| NumWorks Key | TI-84 Plus CE Key | Notes |
| :--- | :--- | :--- |
| **Directional Pad** | Arrow Keys (`▲` `▼` `◄` `►`) | Menu & cursor navigation |
| **`shift`** | `2nd` | Secondary functions |
| **`alpha`** | `ALPHA` | Alpha lock / letters |
| **`EXE`** / **`OK`** | `ENTER` | Execute / confirm |
| **`←` (Backspace)** | `DEL` / `CLEAR` | Delete or clear entry |
| **`x,n,t`** | `X,T,θ,n` | Variable key |
| **`sin` / `cos` / `tan`** | `SIN` / `COS` / `TAN` | Trig functions |
| **`ln` / `log`** | `LN` / `LOG` | Logarithms |
| **`x²`** | `x²` | Square |
| **`0`–`9`, `.`, `+`, `-`, `×`, `÷`** | `0`–`9`, `.`, `+`, `-`, `×`, `÷` | Standard keypad |
| **`Home` (House)** | *Exit Emulator* | Returns to NumWorks Epsilon home screen |

---

## Known Limitations

- **SRAM & Flash Constraints:** Because NumWorks external apps have limited SRAM (~140 KB heap/BSS) and external app Flash (~1.9 MB on recent Epsilon builds), full 4 MB un-trimmed ROMs or heavy Flash write operations may be restricted.
- **Emulation Speed:** Software emulation of the 48 MHz eZ80 CPU runs slower than native NumWorks apps, though standard calculations, menus, and graphing are functional.
- **Exam Mode:** External `.nwa` applications are disabled in NumWorks Exam Mode and are not permitted on standardized tests.

---

## Credits & Acknowledgments

- **[CEmu Developers](https://github.com):** For the open-source TI-84 Plus CE emulation core.
- **NumWorks & Community:** For the EADK external application framework and toolchain documentation.
