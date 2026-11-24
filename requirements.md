# Device Requirements v0.1

## 1. Functional and Electrical Requirements 
| ID | Requirement | Target | Verified on |
|---|---|---|---|
| R1 | Motor current | Unidirectional 0-3 A, ±2%, 5 kHz timer-triggered ADC + DMA (INA240A2D, shunt inside flyback loop, Kelvin-sensed) | D16, D51 |
| R2 | Vibration | ±16 g, 3 axes, 4-wire SPI at 3200 Hz ODR (~1 kHz usable bandwidth) | D16, D19 |
| R3 | Temperature | Motor body 0-100 °C, ±2 °C (10 kΩ NTC with stated Beta value + 10 kΩ 1% divider) | D51 |
| R4 | Motor drive | 12 V DC, 20 kHz PWM, 0-100% duty, low-side MOSFET + 12 V gate driver (MCP1407), motor stall ≤ 3 A | D16 |
| R5 | Anti-alias filter | 2nd-order low-pass active filter (MCP6002, 5% C0G/NP0 or film caps) for fs = 5 kHz | D05, D16 |
| R6 | Fieldbus | Modbus RTU slave, 3.3 V half-duplex RS-485 (THVD1450DR, single-GPIO DE/RE control + 10 kΩ pull-down) | D32, D59 |
| R7 | Debug & programming | USB virtual COM port (UART printf) and flashing via onboard ST-LINK (CN1 Micro-B) | D09 |
| R8 | Power & safety | Extra-low voltage (ELV) only (≤ 24 V DC); 12 V rail current-limited or protected with 3.15–4 A slow-blow (T-rated) fuse; 3.3 V logic and 12 V motor grounds joined at a single star point | D16, D49 |

## 2. Key Hardware & Firmware Constraints

* **Voltage isolation:** Logic domain is strictly 3.3 V (18 NUCLEO-G474RE header pins including `A0`–`A4`, `D0`, `D6`, and `D11`–`D13` are not 5 V tolerant; 3.6 V absolute max). Motor power domain is 12 V.
* **High-current wiring:** The 12 V / up to 3 A motor loop is wired off-breadboard using WAGO 221 lever connectors or 5 mm screw terminals and 18-20 AWG wire.
* **Current-sense accuracy:** INA240A2D wired unidirectional (`REF1 = REF2 = GND`) with `IN+`/`IN-` Kelvin-sensed directly on the shunt leads.
* **ADC reference calibration:** Do not hard-code 3.30 V or 3.25 V (`JP8` default on NUCLEO-G474RE). Measure actual `VREF+` at runtime via the internal `VREFINT` channel and factory constant `VREFINT_CAL`.
* **Safe reset defaults:** 100 kΩ pull-down on the MCP1407 gate-driver input (motor stays off on MCU reset) and 10 kΩ pull-down on THVD1450 `DE`/`/RE` (transceiver defaults to receive mode on reset).