# Chipper - 36-Key Split Keyboard

A custom ZMK firmware configuration for a 36-key split keyboard using Seeeduino XIAO BLE controllers.

## 🎯 Overview

The Chipper keyboard is a compact split mechanical keyboard featuring:
- **36 keys total** (18 per half)
- **3x6 key matrix + 3 thumb keys** per side
- **Wireless Bluetooth** connectivity
- **OLED display** support (128x32 SSD1306)
- **5 layers** for maximum functionality in minimal space

## 🔧 Hardware

- **Microcontroller**: Seeeduino XIAO BLE (nRF52840)
- **Layout**: Split 3x6 columnar stagger + 3 thumb keys
- **Display**: SSD1306 OLED (128x32) via I2C
- **Connectivity**: Bluetooth Low Energy
- **Matrix**: Col2row diode direction

## ⚡ Features

### Layer System
- **DEF** (0): Base QWERTY layout with modifiers
- **NAV** (1): Navigation, arrows, and basic symbols
- **FN** (2): Function keys F1-F12
- **NUM** (3): Numbers and mathematical symbols
- **SYS** (4): Bluetooth management and system controls

### Advanced Features
- **Hold-tap behaviors**: Most keys have dual functions
  - **Ctrl/Cmd key**: Bottom left corner - TAP for CONTROL, HOLD for COMMAND
- **Conditional layers**: NAV + FN automatically activates SYS
- **Bluetooth multi-device**: Support for up to 4 paired devices
- **Combo keys**: Special key combinations for shortcuts
- **Bootloader access**: Wireless firmware updates

## 🚀 Quick Start

### Building Firmware
1. Fork this repository
2. Modify keymap in `config/boards/shields/chipper/chipper.keymap`
3. Commit changes to trigger GitHub Actions build
4. Download generated `.uf2` files from Actions artifacts

### Flashing Firmware
1. Enter bootloader mode: **SPACE + Z + F**
2. Keyboard appears as USB drive
3. Drag `.uf2` files:
   - `chipper_left-*.uf2` → left half
   - `chipper_right-*.uf2` → right half
4. Automatic reboot with new firmware

### Bluetooth Setup
1. Access SYS layer: **SPACE + Z** (hold both)
2. Select device slot: **Q/W/E/R** (devices 1-4)
3. Pair normally from your device's Bluetooth settings
4. Switch devices using same key combination

## 📖 Documentation

- **[Layout Guide](layout-guide.md)**: Visual guide to all layers and key functions
- **[Bootloader Guide](docs/bootloader-bluetooth-guide.md)**: Detailed firmware update and Bluetooth instructions (Portuguese)
- **[CLAUDE.md](CLAUDE.md)**: Development guide for Claude Code

## 🔄 Layer Access

| Layer | Activation | Purpose |
|-------|------------|---------|
| DEF | Default | Base typing layer |
| NAV | Hold left SPACE | Navigation and symbols |
| FN | Hold P or Z | Function keys F1-F12 |
| NUM | Hold right SPACE | Numbers and math symbols |
| SYS | NAV + FN | Bluetooth and system controls |

## 🎹 Key Layout Summary

```
┌─────┬─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┬─────┐
│ ESC │  Q  │  W  │  E  │  R  │  T  │   │  Y  │  U  │  I  │  O  │  P  │ DEL │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│ TAB │  A  │  S  │  D  │  F  │  G  │   │  H  │  J  │  K  │  L  │  ;  │Enter│
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│Ctrl │  Z  │  X  │  C  │  V  │  B  │   │  N  │  M  │  ,  │  .  │  ?  │RAlt │
└─────┴─────┴─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┴─────┴─────┘
                  │Shift│ GUI │Space│   │Space│Bspc │Enter│
                  └─────┴─────┴─────┘   └─────┴─────┴─────┘
                            NAV         NUM
```

## 🛠️ Development

### File Structure
```
xiaoBle/
├── build.yaml                    # GitHub Actions build config
├── config/
│   ├── west.yml                 # West workspace manifest
│   └── boards/shields/chipper/  # Shield configuration
│       ├── chipper.keymap       # Main keymap definition
│       ├── chipper.dtsi         # Hardware configuration
│       └── *.conf/*.overlay     # Board-specific configs
└── docs/                        # Documentation
```

### Customization
- **Keymap**: Edit `chipper.keymap` for layout changes
- **Hardware**: Modify `chipper.dtsi` for GPIO/display settings
- **Features**: Toggle options in `chipper.conf`

### Building Locally
Requires ZMK development environment:
```bash
west build -p -b seeeduino_xiao_ble -- -DSHIELD=chipper_left
west build -p -b seeeduino_xiao_ble -- -DSHIELD=chipper_right
```

## 🔧 Troubleshooting

### Firmware Issues
- **Emergency reset**: Double-click physical RST button
- **Bootloader stuck**: Hold SPACE + Z + B for system reset
- **Build fails**: Check keymap syntax in Actions tab

### Bluetooth Issues
- **Won't pair**: Clear connections with SPACE + Z + T
- **Connection drops**: Re-pair device or try different slot
- **Multiple devices**: Use SPACE + Z + Q/W/E/R to switch

## 📜 License

This project uses ZMK firmware which is licensed under the MIT License.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test with GitHub Actions build
5. Submit a pull request

## 📞 Support

For issues or questions:
- Check existing documentation
- Review keymap configuration
- Test with default ZMK examples
- Open an issue with build logs if needed