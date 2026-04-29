# Wiring (Raspberry Pi Pico W)

## Overview

The circuit has:
- One 4x4 keypad matrix (4 row lines + 4 column lines)
- Twelve discrete LEDs, each driven by one GPIO through a 220Ω resistor
- Common GND return for all LED cathodes
- 1kΩ pull-ups on keypad row lines to 3.3V (as shown in the provided diagram)

## GPIO Mapping

### Keypad

| Keypad Pin | Pico W GPIO |
|---|---|
| R1 | GP26 |
| R2 | GP22 |
| R3 | GP21 |
| R4 | GP20 |
| C1 | GP19 |
| C2 | GP18 |
| C3 | GP17 |
| C4 | GP16 |

### LEDs

`ledPins[] = {11, 10, 9, 8, 7, 6, 5, 4, 3, 2, 28, 27}`

| Logical LED | Key Trigger | Pico W GPIO |
|---|---|---|
| LED1 | `1` | GP11 |
| LED2 | `2` | GP10 |
| LED3 | `3` | GP9 |
| LED4 | `4` | GP8 |
| LED5 | `5` | GP7 |
| LED6 | `6` | GP6 |
| LED7 | `7` | GP5 |
| LED8 | `8` | GP4 |
| LED9 | `A` | GP3 |
| LED10 | `B` | GP2 |
| LED11 | `C` | GP28 |
| LED12 | `D` | GP27 |

## Electrical Notes

- Use 220Ω series resistor per LED anode connection.
- Tie all LED cathodes to GND.
- Keep all GPIO levels at 3.3V logic only.
- Do not power keypad lines with 5V.

## Wokwi Run Notes

- Ensure the diagram includes all keypad row/column wires and LED resistor chains.
- Keep UART wires (GP0/GP1) optional unless serial debug is needed.
