# Differential Cockcroft-Walton High-Voltage Multiplier

A completed experimental high-voltage demonstrator exploring **Cockcroft-Walton voltage multiplication, differential high-voltage generation, corona discharge, plasma behavior, electric-field geometry, ionic wind, and high-voltage insulation**.

> **Status:** Completed — v1.0  
> **Configuration:** 36 total stages — **18 positive + 18 negative**  
> **Observed Arc Length:** ~25 cm  
> **Current DC Supply:** 19 V, 3 A  
> **Estimated Vout from Air Breakdown:** ~750 kV

---
![Differential Cockcroft-Walton](https://github.com/VictorGranado/CockCroft-Walton-Voltage-Multiplier/blob/4058a9b3048b7875c07844f9e2f0f6bc7336b2ce/voltage_multiplier_2.jpg)

## Overview

This project began as a traditional **36-stage continuous Cockcroft-Walton multiplier** and was later redesigned into a **differential 18 + 18 stage configuration**.

### Original Configuration

```text
AC Source → 36-Stage CW Ladder → +HV
```

### Final Differential Configuration

```text
                 ┌→ 18-Stage Positive Ladder → +HV
HV AC Source ────┤
                 └→ 18-Stage Negative Ladder → -HV
```

The two ladders are mirrored with opposite diode orientations.

Instead of placing the full voltage on one high-voltage rail, the final design generates approximately equal positive and negative potentials.

```text
       +HV
        │
        │
   Differential
      Output
        │
        │
       -HV
```

The useful output voltage is:

```text
Vdiff = V+ - V-
```
![Differential Cockcroft-Walton](https://github.com/VictorGranado/CockCroft-Walton-Voltage-Multiplier/blob/4058a9b3048b7875c07844f9e2f0f6bc7336b2ce/voltage_multiplier_1.jpg)
---

## How the Cockcroft-Walton Multiplier Works

A Cockcroft-Walton multiplier uses a ladder of **diodes and capacitors** to convert a high-voltage AC input into a much higher DC potential.

During alternating half-cycles of the AC waveform, different capacitors charge through the diodes. Their voltages are effectively stacked from stage to stage.

For an ideal ladder:

```text
Vout ≈ 2 × n × Vin
```

Where:

- `n` = number of stages
- `Vin` = peak AC input voltage

For the final differential configuration:

```text
V+ ≈ +(2)(18)(Vin)

V- ≈ -(2)(18)(Vin)

Vdiff ≈ 72Vin
```

---

## Why Differential?

Splitting the original 36-stage ladder into two mirrored 18-stage ladders provides several practical advantages:

- Lower voltage stress relative to the center reference
- Better insulation management
- More symmetrical electric-field distribution
- Shorter individual multiplier chains
- Reduced influence of some parasitic effects
- Improved behavior under load
- More stable discharge performance

The differential configuration performed noticeably better during experimental testing.

---

## Circuit Design

Both 18-stage ladders are driven from the same high-frequency AC source.

One ladder pumps charge toward **+HV**, while the mirrored ladder pumps charge toward **−HV**.

### Circuit Diagram

![Differential Cockcroft-Walton Circuit](https://github.com/VictorGranado/CockCroft-Walton-Voltage-Multiplier/blob/bba988de6492d9c8374b10e4d0502db46ab13647/Screenshot%202026-08-16%20181642.png)

---

## Components

| Component | Specification | Quantity |
|---|---|---:|
| DC Power Supply | 19 V DC, 3 A | 1 |
| DC to HV AC Inverter/Transformer | High-frequency HV AC output | 1 |
| High-Voltage Capacitors | 1000 pF (1 nF), ≥20 kV rated | 72 |
| High-Voltage Diodes | 2CL77 or equivalent, ≥20 kV | 72 |
| Positive HV Output Terminal | High-voltage insulated | 1 |
| Negative HV Output Terminal | High-voltage insulated | 1 |
| High-Voltage Wire | HV-rated | As needed |
| PVC Multiplier Enclosures | Insulated cylindrical housings | 2 |
| 3D-Printed Transport Support | Custom designed | 1 |
| High-Voltage Safety Labels | Custom printed | Multiple |

---

## Theoretical Output Calculations

For a standard Cockcroft-Walton multiplier:

```text
Vout = (2)(n)(Vin)
```

For the original 36-stage continuous ladder:

```text
Vout = (2)(36)(Vin)
     = 72Vin
```

For the differential 18 + 18 configuration:

```text
V+ = +(2)(18)(Vin)

V- = -(2)(18)(Vin)

Vdiff = (2)(18)(Vin) + (2)(18)(Vin)
      = 72Vin
```

Therefore, both configurations have approximately the **same ideal total voltage**, but the differential design divides that voltage between positive and negative rails.

### Estimated Ideal Output

| Scenario | AC Input | +HV | −HV | Ideal Differential Output |
|---|---:|---:|---:|---:|
| **Best Case** | 20 kV | +720 kV | −720 kV | **1.44 MV** |
| **Conservative** | 12 kV | +432 kV | −432 kV | **864 kV** |
| **Low Estimate** | 5 kV | +180 kV | −180 kV | **360 kV** |

> These are theoretical no-load calculations and are **not measured output voltages**.

---

## Air Breakdown Estimates

A commonly used approximation for the dielectric strength of air is:

```text
~3 kV/mm
~30 kV/cm
~3 MV/m
```

Using:

```text
Distance ≈ Voltage / 3 kV/mm
```

Gives the following idealized uniform-field values:

| Scenario | Ideal Voltage | Approx. Uniform-Air Breakdown |
|---|---:|---:|
| Best Case | 1.44 MV | ~48 cm |
| Conservative | 864 kV | ~28.8 cm |
| Low Estimate | 360 kV | ~12 cm |

These values should **not** be interpreted as predicted or measured arc lengths.

Actual breakdown distance depends strongly on:

- Electrode geometry
- Humidity
- Atmospheric pressure
- Polarity
- Corona
- Streamer propagation
- Stored energy
- Available output current
- Nearby conductive objects

---

## Component Voltage Stress

Individual Cockcroft-Walton stages can experience voltages on the order of approximately:

```text
Vstage ≈ 2Vin
```

| AC Input | Approx. Stage Voltage |
|---:|---:|
| 20 kV | ~40 kV |
| 12 kV | ~24 kV |
| 5 kV | ~10 kV |

This makes component ratings, physical spacing, insulation, and field control critical.

---

## Real-World Performance

The ideal voltage equation assumes:

- Perfect capacitors
- Perfect diodes
- Zero source impedance
- No corona
- No leakage
- No parasitic capacitance
- No external load

Real output is better represented as:

```text
Vreal ≈ Videal
        - voltage sag
        - source losses
        - corona losses
        - leakage
        - parasitic losses
```

Cockcroft-Walton voltage sag increases strongly with stage count and can be approximated as:

```text
Vsag ∝ (I × n³) / (f × C)
```

Where:

- `I` = load current
- `n` = number of stages
- `f` = AC drive frequency
- `C` = stage capacitance

This relationship was one motivation for moving to two shorter 18-stage ladders instead of one long 36-stage ladder.

### Stage-Count Comparison

```text
Single 36-stage ladder:

36³ = 46,656
```

```text
Two 18-stage ladders:

2 × 18³ = 11,664
```

```text
11,664 / 46,656 ≈ 0.25
```

In an idealized comparison, the stage-count-related sag contribution can therefore be significantly reduced by splitting the multiplier into two shorter ladders.

At very high voltages, however, other effects such as **corona, leakage, parasitic capacitance, transformer impedance, and insulation losses** can become dominant.

---

## Experimental Results

### ~25 cm Arc

After replacing the original **9 V, 1 A supply** with a **19 V, 3 A supply**, the system produced sustained arcs approaching approximately:

```text
25 cm
```

The available source power increased substantially:

```text
Original Supply:

9 V × 1 A ≈ 9 W
```

```text
Final Supply:

19 V × 3 A ≈ 57 W
```

The multiplier does not necessarily consume the full 57 W, but the larger power supply gives the transformer and multiplier significantly more available power during streamer and arc formation.

This allows the circuit to maintain its voltage more effectively once a discharge begins.

> **Note:** Arc length is not used as a direct voltage measurement. Breakdown distance depends on electrode geometry, humidity, streamer propagation, available current, polarity, and stored energy.

---

## Corona and Plasma Behavior

Certain electrode positions and geometries produced stable visible corona or plasma without immediately transitioning into a full arc.

Small changes in:

- Electrode spacing
- Electrode shape
- Orientation
- Nearby conductive objects
- Surface geometry

Produced significant changes in discharge behavior.

This demonstrated the importance of **local electric-field concentration and electrode geometry** in high-voltage systems.

---

## Ionic Wind

Stable corona operation also produced noticeable airflow around the electrodes.

This is consistent with **ionic wind**, also known as electrohydrodynamic flow.

Charged particles accelerated by the electric field collide with neutral air molecules and transfer momentum to them, producing airflow without mechanical moving parts.

---

## Magnet Experiments

Permanent magnets placed near the discharge produced several noticeable effects:

- Collapse of stable plasma regions at certain positions
- Changes in discharge geometry
- Changes in streamer behavior
- Slight increases in apparent arc distance when magnets were placed near electrode tips

Possible contributing mechanisms include:

- Electric-field distortion
- Changes in parasitic capacitance
- Changes in electrode geometry
- Additional multiplier loading
- Possible magnetic interaction with moving charged particles

Further controlled testing would be required to separate purely electrostatic effects from direct magnetic interaction with the ionized gas.

---

## EMF / RF Observations

Strong electromagnetic activity was detected around the operating system.

Likely sources include:

- High-frequency transformer operation
- Rapid capacitor charging currents
- Displacement currents
- Corona discharge
- Streamer formation
- Fast arc-current transitions

Although the final multiplier output is primarily DC, the system contains significant high-frequency and transient electrical activity.

---

## Electrode Geometry

Electrode geometry strongly influences the type and stability of the discharge.

### Sharp Electrodes

Sharp points create strong local electric-field concentration.

```text
Sharp Electrode
      ↓
High Local Electric Field
      ↓
Early Corona Formation
      ↓
Streamer Development
```

This makes sharp electrodes useful for studying:

- Corona
- Plasma formation
- Streamers
- Ionic wind

However, early corona can also continuously load the multiplier and reduce terminal voltage.

### Rounded Electrodes

Smooth or rounded electrodes reduce local field concentration.

```text
Rounded Electrode
       ↓
Reduced Field Enhancement
       ↓
Less Premature Corona
       ↓
Higher Voltage Before Breakdown
```

Rounded electrodes can therefore produce cleaner and more repeatable arc behavior.

---

## Mechanical Design

The completed project consists of two enclosed multiplier modules representing the **+HV and −HV ladders**.

Each multiplier is housed inside a cylindrical PVC enclosure for mechanical protection and organization.

A custom **3D-printed tower support** was designed and manufactured to hold both multiplier modules together.
![Differential Cockcroft-Walton](https://github.com/VictorGranado/CockCroft-Walton-Voltage-Multiplier/blob/4058a9b3048b7875c07844f9e2f0f6bc7336b2ce/voltage_multiplier_3.jpg)
The support provides:

- Improved organization
- Easier transportation
- Faster setup for demonstrations
- Protection during storage
- Consistent module spacing
- Integrated carrying handle

This transformed the original bench prototype into a portable high-voltage demonstrator.

---

## Safety System

The completed multiplier includes dedicated high-voltage safety labeling.

Labels identify:

- +HV output
- −HV output
- Stored-charge hazard
- High-voltage handling instructions
- Service precautions
- General high-voltage warnings

> ⚠️ **EXTREME HIGH-VOLTAGE WARNING**
>
> The capacitors and multiplier stages can remain charged after input power is removed.

Potential hazards include:

- Electric shock
- Stored-energy discharge
- Burns
- Fire
- Component failure
- Unexpected arcing
- RF / EMI interference
- Damage to nearby electronics
- Ozone and reactive gas generation from corona

Never assume the multiplier is discharged simply because visible corona or arcing has stopped.

The system should be fully discharged and verified safe before handling or servicing.

---

## Ozone Generation

Corona and high-voltage arcs can generate ozone by ionizing oxygen molecules in the surrounding air.

For this reason, testing should be performed with adequate ventilation.

Oil insulation and improved field control can reduce unwanted corona within the multiplier itself, although exposed output discharges can still generate ozone.

---

## Project Goals

The completed system serves as a practical demonstration platform for studying:

- Cockcroft-Walton voltage multiplication
- Differential high-voltage generation
- Capacitive energy storage
- High-voltage rectification
- Corona discharge
- Plasma formation
- Streamer development
- Ionic wind
- Electric-field geometry
- Dielectric breakdown
- Parasitic capacitance
- High-voltage insulation
- Electromagnetic interference
- Electrode geometry
- Mechanical design
- 3D printing
- High-voltage safety

---

## Development Timeline

The project evolved through several major stages:

```text
Initial Cockcroft-Walton Prototype
                ↓
36-Stage Continuous Ladder
                ↓
Differential 18 + 18 Redesign
                ↓
Corona / Plasma Experiments
                ↓
Magnetic and EMF Experiments
                ↓
Higher-Power 19 V Supply
                ↓
~25 cm Arc Testing
                ↓
Protective PVC Enclosures
                ↓
High-Voltage Safety Labels
                ↓
Custom 3D-Printed Transport Tower
                ↓
Completed v1.0
```

---

## Educational Demonstration

The finished multiplier has also been used as a **Physics 3 classroom demonstration**.

The project provides a practical way to demonstrate concepts including:

- Electric potential
- Electric fields
- Capacitance
- Charge storage
- Dielectric breakdown
- Plasma formation
- Corona discharge
- Electric-field geometry
- Electromagnetic interference
- Energy transfer

The project will also be demonstrated as part of an end-of-semester Physics 3 presentation.

---

## Project Status

### ✅ Differential Cockcroft-Walton Voltage Multiplier v1.0 — Complete

The primary design and construction phase of the project is complete.

The finished system includes:

- Differential 18 + 18 multiplier architecture
- Dual insulated multiplier housings
- High-frequency HV AC input
- 19 V, 3 A source
- Dedicated +HV and −HV outputs
- High-voltage safety labeling
- Custom mechanical support
- Integrated carrying handle
- Portable demonstration configuration

Future work may include additional measurements, experiments, electrode testing, insulation improvements, and further plasma studies, but the core system is complete.

---

## Disclaimer

All voltage calculations presented in this repository are theoretical unless explicitly identified as measured values.

Actual output depends strongly on:

- Corona
- Leakage
- Parasitic capacitance
- Source impedance
- Voltage sag
- Humidity
- Atmospheric conditions
- Insulation
- Electrode geometry
- Load current
- Transformer performance

The theoretical voltage values should therefore be treated as upper-bound design calculations rather than direct measurements.

This repository documents an experimental engineering project and is **not intended as a beginner construction guide**.

---

## Final Version

### Differential Cockcroft-Walton High-Voltage Multiplier v1.0

**36 total stages**  
**18 positive stages**  
**18 negative stages**  
**Differential high-voltage output**  
**~25 cm demonstrated arc length**

### Project Complete
