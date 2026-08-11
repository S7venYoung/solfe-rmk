# Sofle Dongle DYA — RMK port

RMK v0.8.2 port of `S7venYoung/zmk-sofle-dongle-dya` for three nice!nano v2 / nRF52840 boards:

- `central` → USB/BLE dongle
- `peripheral` → left half
- `peripheral2` → right half

## Build with GitHub Actions

Push this directory as the root of a GitHub repository. The **Build RMK firmware** workflow runs on pushes to `main`, pull requests, and manual dispatches.

Download the workflow artifact and flash:

| File | Target |
| --- | --- |
| `sofle-dongle-rmk.uf2` | Dongle |
| `sofle-left-rmk.uf2` | Left half |
| `sofle-right-rmk.uf2` | Right half |

Double-tap reset to expose the nice!nano bootloader drive, then copy the corresponding UF2 file to it.

## Local build

```sh
cargo install --locked cargo-make
cargo make uf2
```

## Port status

Implemented:

- ZMK 5×14 logical layout and four layers
- Original left/right matrix GPIO and col2row direction
- BLE dongle central with two peripherals
- Five BLE host profiles
- Mouse keys and left EC11 encoder mappings
- Vial support inherited from RMK

Not yet equivalent to the ZMK build:

- nice!view displays and dongle SH1106 status UI
- WS2812 underglow and PWM backlight wiring
- joystick/input-processor acceleration behavior
- ZMK combo soft-off behavior
- custom DYA Studio RPC modules and key statistics

The original keymap contains a plaintext password macro. It is intentionally not copied into this port. Add secrets only through a safer local customization mechanism.
