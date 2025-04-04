# ZMK Config

This repository contains configuration files for a ZMK (ZMK Firmware) powered keyboard.

ZMK is an open-source firmware designed for wireless and low-power keyboards, especially for split and custom boards using BLE. This configuration defines custom keymaps, behaviors, and hardware setups.

---

## 📁 Repository Structure

- `config/` - Keymap layers and behavior configurations
- `boards/` - (Optional) Custom board definitions
- `shields/` - Hardware configuration for custom keyboard halves or modules
- `.github/` - (Optional) GitHub Actions for CI builds (if configured)
- `build/` - Output directory for compiled firmware (generated locally)

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/psa1302/zmk-config.git
cd zmk-config
```

### 2. Set Up the ZMK Development Environment

Follow the official [ZMK Development Setup Guide](https://zmk.dev/docs/development/setup) to install:

- [West](https://docs.zephyrproject.org/latest/develop/west/index.html)
- Zephyr SDK
- Required toolchains and Python dependencies

### 3. Initialize the ZMK App (if not already)

If you're starting fresh, use ZMK's official `zmk` repo as a submodule or workspace:

```bash
west init -l config
west update
```

Or clone the ZMK app separately and link this config:

```bash
git clone https://github.com/zmkfirmware/zmk app
cd app
west init -l
west update
```

Then place this `zmk-config` as a sibling directory and use `-s ../zmk-config` when building.

---

## 🛠 Building the Firmware

Use this command to build the firmware:

```bash
west build -s app -b <board_name> -- -DSHIELD=<shield_name>
```

Examples:

```bash
west build -s app -b nice_nano_v2 -- -DSHIELD=corne_left
west build -s app -b nice_nano_v2 -- -DSHIELD=corne_right
```

Replace `<board_name>` and `<shield_name>` with your actual board and shield.

---

## 🔌 Flashing Firmware

After building, the firmware file (`zephyr/zmk.uf2`) will be generated in the `build/` directory.

1. Plug in your keyboard controller in bootloader mode.
2. Copy the `.uf2` file to the mounted drive (e.g., `NICE_NANO`).
3. Your keyboard will reboot with the new firmware.

---

## 🎛 Customization

To modify keymaps or layers:

- Open `config/<keyboard_name>.keymap`
- Use [ZMK behavior syntax](https://zmk.dev/docs/behaviors/behavior-mod-morph/) to define layers, combos, macros, tap dance, etc.

After changes:

```bash
west build -s app -b <board_name> -- -DSHIELD=<shield_name>
```

Flash again with the new `.uf2`.

---

## 🙌 Contributions & Community

- For issues, improvements, or questions, feel free to open a GitHub Issue or PR.
- For ZMK-specific discussions and troubleshooting, join the [ZMK Discord](https://discord.gg/zmk).

---

## 📚 Resources

- [ZMK Documentation](https://zmk.dev/docs)
- [ZMK GitHub](https://github.com/zmkfirmware/zmk)
- [Keymap Editors (Community)](https://nickcoutsos.github.io/keymap-editor)

---

**Note:** This is a personal keyboard firmware configuration repository. Please adapt paths, boards, and shield names to fit your own keyboard hardware.

Happy typing! ⌨️

