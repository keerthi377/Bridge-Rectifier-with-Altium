
# Bridge Rectifier Design in Altium

A full-wave bridge rectifier PCB designed in Altium Designer with EMI protection and surge suppression circuitry for safe AC-to-DC conversion.

This project includes:

* Schematic design
* PCB layout
* EMI filtering
* Component selection
* Custom footprint creation
* Design rule checking (DRC)

---

# Basic Working Principle

A bridge rectifier converts AC voltage into DC voltage using four diodes arranged in a bridge configuration.

* During the positive half-cycle, two diodes conduct.
* During the negative half-cycle, the other two diodes conduct.

This produces a full-wave rectified output.

Without a filter capacitor, the output is pulsating DC.
A large electrolytic capacitor is added across the output to:

* reduce ripple voltage,
* increase charging/discharging time,
* smooth the output voltage closer to DC.

The ripple frequency of a full-wave bridge rectifier is:

f_{ripple}=2f_{input}

---

# Input and Output Specifications

| Parameter                | Value          |
| ------------------------ | -------------- |
| Input Voltage            | 115V AC        |
| Output Voltage (Peak DC) | 162.63V DC     |
| Output Current           | 1A             |
| Output Power             | ~162W          |
| Voltage Ripple           | 10% (~16.2V)   |
| Output Voltage Range     | 130V – 162.63V |
| Estimated Efficiency     | ~90%           |
| Maximum Input Current    | ~2.2A          |

---

# Design Calculations

## Peak Output Voltage

For a bridge rectifier:

V_{DC}=V_{RMS}\sqrt{2}-2V_D

---

## Ripple Voltage

Ripple voltage is selected as 10% of the output voltage as a trade-off between:

* capacitor size,
* ripple performance.

Higher capacitance results in lower ripple.

---

## Filter Capacitor Calculation

Capacitance is calculated using:

C=\frac{I}{2fV_r}

Calculated value:

```text id="7m0-vesm"
C ≈ 601.8µF
```

Selected capacitor:

```text id="4q1y8m"
720µF Electrolytic Capacitor
```

---

# Protection and EMI Filtering

## Bleeder Resistor

A bleeder resistor is connected across the filter capacitor to safely discharge stored energy after power-off.

Selected value:

```text id="0v7q3n"
220kΩ
```

---

## Fuse

A slow-blow fuse is used to tolerate startup inrush current while still protecting against overcurrent conditions.

Selected fuse:

```text id="6m0t4p"
3.15A Slow-Blow Fuse
```

---

## NTC Thermistor

An NTC thermistor is used for inrush current limiting.

At startup:

* resistance is high,
* current is limited.

As temperature increases:

* resistance decreases,
* normal operation resumes.

Selected value:

```text id="1x9r2w"
5Ω NTC Thermistor
```

---

## MOV (Metal Oxide Varistor)

The MOV protects the circuit from:

* voltage spikes,
* surge transients.

During overvoltage conditions:

* MOV resistance decreases rapidly,
* surge current is diverted safely.

---

## X and Y Safety Capacitors

### X Capacitor

Connected between:

```text id="4p7m0v"
Line ↔ Neutral
```

Used to suppress:

```text id="7q1n8m"
Differential-mode noise
```

---

### Y Capacitor

Connected between:

```text id="0m4-vesm"
Line/Neutral ↔ Earth
```

Used to suppress:

```text id="5r2q7n"
Common-mode noise
```

---

## Common-Mode Choke

The common-mode choke suppresses:

* high-frequency EMI noise,
* conducted noise on AC mains lines.

---

# Component Selection

| Component         | Part Number              |
| ----------------- | ------------------------ |
| Slow Blow Fuse    | 04653.15DR               |
| Connector         | 691311500103             |
| MOV               | 07D241K                  |
| Bridge Rectifier  | KBP206G-G                |
| Y2 Capacitor      | Vishay AY2471K29Y5SS63L7 |
| Common-Mode Choke | PM3700-50-RC             |
| X2 Capacitor      | BFC233990027             |
| Bleeder Resistor  | 3522220KJT               |
| NTC Thermistor    | SL125R003                |
| Filter Capacitor  | ELHU401VSN721MQ60S       |

---

# Symbol, Footprint, and 3D Models

Most symbols, footprints, and 3D models were imported from:

* Mouser
* DigiKey
* SamacSys

Custom symbols and footprints were created in Altium for:

* SL125R003
* 3522220KJT
* ELHU401VSN721MQ60S

All custom footprints were designed using manufacturer datasheets.

---

# PCB Design Flow

1. Component Selection
2. Symbol and Footprint Creation
3. Schematic Design
4. Annotation and ERC
5. PCB Import
6. Mechanical Board Outline
7. Design Rule Configuration
8. Component Placement
9. Routing
10. Polygon Pour
11. Design Rule Check (DRC)

---

# PCB Design Considerations

* Components are placed to minimize routing complexity.

* Separate routing is used for high-voltage and low-voltage sections.

* Track widths are selected according to current requirements.

* Polygon pours are used for:

  * Ground
  * Earth

* Vias are used for:

  * ground interconnection,
  * earth connectivity.

* Clearance constraints are applied for high-voltage safety.

---

# Features

* Full-wave bridge rectification
* EMI filtering
* Surge protection
* Inrush current limiting
* High-voltage DC generation
* Custom Altium footprints
* DRC-compliant PCB layout

---

# Software Used

* Altium Designer

---

# Future Improvements

* Transformer-isolated version
* Regulated DC output
* Buck converter stage
* Thermal analysis
* EMI compliance optimization
* 3D enclosure integration

---
