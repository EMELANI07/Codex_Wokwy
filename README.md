# Pico W Keypad-to-LED Controller

A Raspberry Pi Pico W firmware project that reads a 4x4 matrix keypad and controls 12 LEDs based on the pressed key.

## Repository Structure

```text
.
├── CMakeLists.txt
├── diagram.json
├── docs/
│   ├── architecture.md
│   └── wiring.md
├── include/
└── src/
    └── main.cpp
```

## Features

- 4x4 keypad scanning via `Keypad` library.
- Direct key-to-LED mapping for keys `1..8` and `A..D`.
- Group actions:
  - `9`: turn ON LEDs 1..8
  - `0`: turn OFF LEDs 1..8
  - `*`: turn ON LEDs A..D
  - `#`: turn OFF LEDs A..D
- Startup initialization keeps all LEDs OFF.

## Hardware Components

- 1x Raspberry Pi Pico / Pico W
- 1x 4x4 membrane keypad
- 12x LEDs (8 blue + 4 red in diagram)
- 12x 220Ω LED resistors
- 4x 1kΩ pull-up resistors for keypad rows
- Breadboard and jumper wires

## Build / Flash Options

This code uses Arduino-style APIs (`setup()`, `loop()`, `digitalWrite`, `Keypad`).

### Option A: Wokwi (recommended for this repo)

1. Create/open a Wokwi Raspberry Pi Pico project.
2. Copy `src/main.cpp` into the sketch source.
3. Add the 4x4 keypad and LED wiring described in `docs/wiring.md`.
4. Run simulation and press keypad buttons.

### Option B: Real Pico W with Arduino-Pico core

1. Install Arduino IDE.
2. Install the **Raspberry Pi Pico/RP2040** board package.
3. Install **Keypad** library from Library Manager.
4. Copy `src/main.cpp` into an `.ino` sketch (or include it in your preferred Arduino project structure).
5. Select **Raspberry Pi Pico W** board and correct serial port.
6. Upload and validate LED behavior against the key mapping table.

### Option C: CMake workflow wrapper (advanced)

A minimal `CMakeLists.txt` is included for repository structure consistency. For production builds, use your existing RP2040 + Arduino core toolchain integration.

## Wi-Fi Note

Pico W Wi-Fi is not used in the provided logic. No credentials are required.

## Behavior Preservation

The logic in `src/main.cpp` is preserved from the provided source (key mapping and LED control flow unchanged).

