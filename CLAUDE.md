# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a ZMK (Zephyr Mechanical Keyboard) firmware configuration for a custom split keyboard called "Chipper". The project targets the Seeeduino XIAO BLE microcontroller and implements a 36-key split keyboard layout with advanced features.

## Build Commands

### Building Firmware
The project uses GitHub Actions for automated building. The build configuration is defined in `xiaoBle/build.yaml`:
- Target board: `seeeduino_xiao_ble`
- Shields: `chipper_left` and `chipper_right`
- Build matrix generates firmware for both keyboard halves

### Local Development
- West workspace manifest: `xiaoBle/config/west.yml`
- ZMK source repository: https://github.com/zmkfirmware/zmk (main branch)
- Configuration path: `xiaoBle/config`

## Architecture Overview

### Hardware Configuration
- **Microcontroller**: Seeeduino XIAO BLE (nRF52840)
- **Layout**: 36-key split keyboard (3x6 + 3 thumb keys per half)
- **Matrix**: 4 rows × 12 columns (col2row diode direction)
- **Display**: SSD1306 OLED (128x32) connected via I2C
- **GPIO Mapping**: Rows on GPIO pins 2, 3, 28, 29

### Key Components

#### Device Tree Configuration (`chipper.dtsi`)
- Matrix transform definitions for 6-column and 5-column layouts
- GPIO matrix scan configuration
- I2C pinctrl setup for OLED display
- SSD1306 display driver configuration

#### Keymap Configuration (`chipper.keymap`)
- **5 layers**: DEF (base), NAV (navigation), FN (function), NUM (numbers/symbols), SYS (system/bluetooth)
- **Conditional layers**: NAV + FN = SYS layer
- **Hold-tap behaviors**: Balanced hold-tap with 280ms tapping term
- **Combo system**: Key position 6+30 triggers "nayeon" macro
- **Bluetooth management**: Device selection and pairing controls

#### Firmware Features
- OLED display support (`CONFIG_ZMK_DISPLAY=y`)
- Bluetooth connectivity with device switching
- Bootloader and system reset functions
- RGB underglow support (commented out)
- USB logging support (commented out)

### File Structure
```
xiaoBle/
├── build.yaml                    # GitHub Actions build matrix
├── config/
│   ├── west.yml                 # West workspace manifest
│   └── boards/shields/chipper/
│       ├── Kconfig.defconfig    # Shield defaults
│       ├── Kconfig.shield       # Shield configuration
│       ├── chipper.conf         # Base configuration
│       ├── chipper.dtsi         # Device tree include
│       ├── chipper.keymap       # Keymap definition
│       ├── chipper_left.conf    # Left half config
│       ├── chipper_left.overlay # Left half overlay
│       ├── chipper_right.conf   # Right half config
│       └── chipper_right.overlay# Right half overlay
```

## Development Guidelines

### Keymap Modifications
- Layer definitions use `#define` constants (DEF=0, NAV=1, etc.)
- Hold-tap timings configured via `bht` behavior (280ms tapping term)
- Combo timeout set to 60ms via `COMBO_TIMEOUT`
- Use `___` for transparent keys and `XXX` for disabled keys

### Hardware Customization
- GPIO assignments in `chipper.dtsi` row-gpios section
- I2C pins configured for SDA (GPIO 4) and SCL (GPIO 5)
- Display parameters in ssd1306 device node

### Build Process
- Firmware builds automatically via GitHub Actions
- Artifacts generated for both left and right keyboard halves
- Configuration changes require pushing to trigger new builds

### Feature Flags
Enable optional features by uncommenting in `chipper.conf`:
- RGB underglow: `CONFIG_ZMK_RGB_UNDERGLOW=y` + `CONFIG_WS2812_STRIP=y`
- Rotary encoder: `CONFIG_EC11=y` + `CONFIG_EC11_TRIGGER_GLOBAL_THREAD=y`
- USB logging: `CONFIG_ZMK_USB_LOGGING=y`

## Firmware Update and Bluetooth Operations

### Bootloader Access (Firmware Upload Mode)
To enter bootloader mode for firmware updates:
1. **Hold SPACE** (left thumb) → activates NAV layer
2. **Hold Z** (left pinky) → activates FN layer
3. **NAV + FN** automatically activates SYS layer
4. **Press F or H** while holding both → triggers `&bootloader`

The keyboard will disconnect and reconnect as a USB drive. Drag `.uf2` files to upload new firmware.

### Bluetooth Device Management
Access via same key sequence (SPACE + Z for SYS layer):
- **Q, W, E, R**: Connect to Bluetooth devices 1-4
- **T or Y**: Clear all Bluetooth connections
- Supports up to 4 paired devices simultaneously
- Persistent connection memory

### Firmware Build Process
1. Modify keymap in GitHub repository
2. Commit and push → GitHub Actions builds automatically
3. Download generated `.uf2` files
4. Use bootloader sequence to upload:
   - `chipper_left-*.uf2` → left half
   - `chipper_right-*.uf2` → right half
5. Update one half at a time

### Emergency Recovery
- Physical reset: Double-click RST button on microcontroller
- System reset: SPACE + Z + B/N keys (`&sys_reset`)