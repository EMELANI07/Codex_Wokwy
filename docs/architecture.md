# Firmware Architecture

## Design Goal

Simple deterministic keypad-to-LED control with no dynamic allocation and no networking.

## File Layout

- `src/main.cpp`: full application logic and key handling loop.
- `docs/wiring.md`: hardware wiring and GPIO map.
- `diagram.json`: Wokwi hardware model source.

## Runtime Flow

1. **Startup (`setup`)**
   - Configure all 12 LED GPIO pins as outputs.
   - Force all LEDs OFF.

2. **Main Loop (`loop`)**
   - Poll keypad via `keypad.getKey()`.
   - If a key is pressed, dispatch in `switch(key)`.
   - Update one or more LEDs.
   - Delay for 10 ms.

## Key Handling Summary

- `1..8` -> turn ON individual LEDs 1..8
- `9` -> turn ON LEDs 1..8
- `0` -> turn OFF LEDs 1..8
- `A..D` -> turn ON individual LEDs 9..12
- `*` -> turn ON LEDs 9..12
- `#` -> turn OFF LEDs 9..12

## Assumptions and Constraints

- Debounce/scanning behavior is delegated to the `Keypad` library.
- No explicit LED OFF for individual keys (`1..8`, `A..D`) unless group-off keys are pressed.
- Pico W wireless hardware is unused in this firmware.
