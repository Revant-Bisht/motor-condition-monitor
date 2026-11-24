# Motor Condition Monitor - Bill of Materials (BOM)

**Critical delivery deadlines**
* **Nucleo + Micro-B data cable:** arrive before **Wed 2 Dec (Day 09)**
* **All breadboard drive & sensing parts:** arrive before **Wed 9 Dec (Day 16)** (target by 8 Dec)
* **PCB Rev A + final SMD shunt + 0805 kit:** ordered on **Day 27**

---

## Order 1: DigiKey AU or element14 AU (Chips & Passives)

| # | Part | Role | Key spec checked (why it passes) | Qty | Supplier + part no. | Unit A$ | Ordered | ETA |
|---|---|---|---|---|---|---|---|---|
| 1 | NUCLEO-G474RE | MCU dev board | Cortex-M4F 170 MHz with FPU, 12-bit ADCs, ST-LINK (Micro-B), Arduino headers (fallback: NUCLEO-L476RG) | 1 | | | | |
| 2 | INA240A2D / A2DR | Current-sense amp | SOIC-8 (1.27 mm, not TSSOP PW), 50 V/V gain, −4 V to 80 V CM, enhanced PWM rejection | 3 | | | | |
| 3 | Shunt resistor 10 mΩ | Motor current shunt (option A) | Through-hole, 1%, ≥ 1 W; 0.5 V/A (~6 A FS if stall is 3.5–5.5 A) | 2 | | | | |
| 4 | Shunt resistor 20 mΩ | Motor current shunt (primary) | Through-hole, 1%, ≥ 1 W; 1.0 V/A (~3.1 A FS; 0.18 W @ 3 A) | 2 | | | | |
| 5 | Shunt resistor 50 mΩ | Motor current shunt (option C) | Through-hole, 1%, ≥ 1 W; 2.5 V/A (~1.2 A FS if stall is ~1 A) | 2 | | | | |
| 6 | MCP1407-E/P | Gate driver (breadboard) | DIP-8, non-inverting 6 A, 12 V supply (max 18 V), VIH ~2.4 V (< 3.3 V); Plan B: TC4420 (pin-compatible) | 2 | | | | |
| 7 | MCP1407-E/SN | Gate driver (PCB) | SOIC-8, non-inverting 6 A, 12 V supply; Plan B: TC4420 | 3 | | | | |
| 8 | IRLZ44N / FQP30N06L / STP55NF06L | Low-side MOSFET (breadboard) | TO-220, N-ch, ≥ 30 V, ≥ 20 A; fully enhanced at 12 V gate drive | 3 | | | | |
| 9 | AOD4184A | Low-side MOSFET (PCB) | DPAK/TO-252, active part, 40 V, 50 A, ±20 V max V_GS, < 7 mΩ @ 10 V (skip obsolete IRLR2905) | 3 | | | | |
| 10 | 1N5822 | Flyback diode (breadboard) | 3 A 40 V Schottky, through-hole | 4 | | | | |
| 11 | SS34 | Flyback diode (PCB) | 3 A 40 V Schottky, SMD | 5 | | | | |
| 12 | MCP6002-I/P | Anti-alias filter op-amp (breadboard) | DIP-8, dual, 3.3 V rail-to-rail I/O, 1 MHz GBW | 2 | | | | |
| 13 | MCP6002-I/SN | Anti-alias filter op-amp (PCB) | SOIC-8, dual, 3.3 V rail-to-rail I/O, 1 MHz GBW | 3 | | | | |
| 14 | THVD1450DR (or SP3485EN) | RS-485 transceiver | SOIC-8, native 3.3 V (3.0–5.5 V), half-duplex, DE & /RE exposed, ±18 kV IEC ESD | 3 | | | | |
| 15 | 100 nF X7R ceramic cap | IC decoupling (3.3 V & 12 V rails) | Through-hole, X7R dielectric, 50 V rating (covers both 3.3 V logic & 12 V MCP1407) | 20 | | | | |
| 16 | 4.7 µF or 10 µF cap | MCP1407 local bypass / rail reservoir | 25–50 V rating, ceramic or electrolytic, placed right at MCP1407 VDD | 8 | | | | |
| 17 | Filter caps: 1, 4.7, 10, 22, 47, 100 nF | 2nd-order anti-alias filter (D05/D16) | 5% C0G/NP0 ceramic or film (low drift; not Y5V/Z5U) | 5 ea | | | | |
| 18 | 470 µF electrolytic cap | 12 V motor-rail bulk decoupling | 25–35 V, low-ESR, placed across 12 V near motor/MOSFET | 3 | | | | |
| 19 | 10 kΩ NTC thermistor | Motor body temperature | Datasheet states Beta value (e.g. 3950 K); insulated leads or ring lug | 2 | | | | |
| 20 | 10 kΩ 1% metal-film resistor | NTC divider + DE/RE pull-down | 1% tolerance, 0.25 W, through-hole | 5 | | | | |

---

## Order 2: Core Electronics (Breakouts, Adapters & Debug)

| # | Part | Role | Key spec checked (why it passes) | Qty | Supplier + part no. | Unit A$ | Ordered | ETA |
|---|---|---|---|---|---|---|---|---|
| 21 | ADXL345 breakout | 3-axis vibration sensor | 3.3 V, ±16 g, 3200 Hz ODR, 4-wire SPI pins exposed (CS, SDO, SDA/SDI, SCL) | 2 | | | | |
| 22 | SOIC-8 to DIP-8 adapter boards | Breadboard adapters for SOIC-8 chips | Fits 150 mil SOIC-8 (e.g. 2× SparkFun 4-packs = 8 boards) | 8–10 | | | | |
| 23 | 2.54 mm breakaway male pin headers | Pins for SOIC-8 adapters & ADXL345 | Standard 0.1" pitch (adapters ship bare) | 3 | | | | |
| 24 | USB-to-RS485 adapter (FTDI) | Mac Modbus RTU interface | Genuine FT232R chip (native macOS support), screw terminals | 1 | | | | |
| 25 | 24 MHz 8-ch USB logic analyser | SPI / UART / Modbus debug | FX2-based ("Saleae-clone"), works with PulseView | 1 | | | | |
| 26 | Jumper wire packs (M-M, M-F, F-F) | Breadboard & Nucleo interconnects | Covers Nucleo female Arduino headers & male Morpho pins | 1 ea | | | | |

---

## Order 3: Local Pickup (Altronics Myaree / Jaycar O'Connor / Bunnings)

| # | Part | Role | Key spec checked (why it passes) | Qty | Supplier + part no. | Unit A$ | Ordered | ETA |
|---|---|---|---|---|---|---|---|---|
| 27 | 12 V brushed DC motor (RS-385 class) | Motor test rig | Stall current ≤ 3 A, threaded face mounting holes, known shaft dia (2.0/2.3 mm) | 1 | | | | |
| 28 | Fan / propeller / flywheel | Imbalance load (D19) | Hub matches exact motor shaft diameter (check in person) | 1 | | | | |
| 29 | Rigid base plate + L-bracket/fasteners | Mechanical rig mount | Rigid mount so ADXL345 measures motor vibration, not rattle | 1 | | | | |
| 30 | USB-C to Micro-B data cable | Nucleo ST-LINK (CN1) to Mac | Verified data cable (not charge-only) | 1 | | | | |
| 31 | Bench power supply (0–30 V, 0–5 A CC) | Safe current-limited 12 V supply | Constant-current limiting (0.2 A logic / 1 A motor bring-up); OR 12 V 3 A plug pack + barrel-to-screw adapter + inline 3.15–4 A slow-blow (T) fuse | 1 | | | | |
| 32 | WAGO 221 lever connectors (or 5 mm screw terminals) | Off-breadboard 12 V power loop | Keeps 3 A PWM motor current off breadboard spring clips | 1 pk | | | | |
| 33 | 18–20 AWG stranded wire (red/black) | 12 V motor loop + star ground | Adequate ampacity; add banana-to-alligator leads if buying bench supply | 2 | | | | |
| 34 | 22 AWG solid-core hook-up wire | Breadboard logic wiring | Clean flat routing on breadboard | 1 pk | | | | |
| 35 | 830-point solderless breadboards | Logic & analog front-end prototype | Quality spring clips | 2 | | | | |
| 36 | Through-hole 1% metal-film resistor kit (E12/E24) | Gate, pull-down, RS-485 & filter resistors | Covers 10–22 Ω gate, 100 kΩ driver PD, 10 kΩ DE/RE PD, 120 Ω RS-485 termination, filter R | 1 kit | | | | |

---

## Bench tools checklist (Long-term gear — Order and tick when owned)

| Status | Tool | Key spec checked | Supplier | Est. / Actual A$ |
|---|---|---|---|---|
| [ ] | Temperature-controlled soldering iron | Pinecil V2 (+ ≥ 65 W USB-C PD charger) or Hakko FX-888D class; fine tip | | |
| [ ] | Solder + no-clean flux | 0.5–0.8 mm rosin-core 63/37 + no-clean flux pen/syringe (for SOIC-8) | | |
| [ ] | Desoldering wick, ESD tweezers, cutters, strippers | 2 mm braid, fine-tip ESD tweezers | | |
| [ ] | Auto-ranging multimeter | Fused 10 A range + continuity beeper (UNI-T UT61E+ / Brymen class) | | |
| [ ] | USB-C hub | Enough USB-A ports for Nucleo, FTDI RS-485, and logic analyser at once | | |

---

## Deferred to Day 27 (PCB Fabrication Order)

| Item | Notes | Target Date |
|---|---|---|
| JLCPCB 2-layer PCB Rev A (×5) | Express shipping to Perth (Christmas lead time) | Day 27 |
| Matching 2512 SMD shunt (1%, ≥ 1 W) | Value (10 / 20 / 50 mΩ) selected from the stall current measured on arrival | Day 27 |
| 0805 SMD resistor/capacitor assortment kit | For PCB assembly on Day 44 (not breadboard-compatible) | Day 27 |

---