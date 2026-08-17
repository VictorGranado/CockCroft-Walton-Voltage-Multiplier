# Differential Cockcroft-Walton High-Voltage Multiplier

An experimental high-voltage project exploring **Cockcroft-Walton voltage multiplication, differential output configurations, corona discharge, plasma behavior, electric-field geometry, and high-voltage insulation**.

> **Status:** Experimental / In Development  
> **Current Configuration:** 36 total stages — **18 positive + 18 negative**

---

## Overview

This project began as a traditional **36-stage continuous Cockcroft-Walton multiplier** and was later redesigned into a **differential 18 + 18 stage configuration**.

### Original Configuration

```text
AC Source → 36-Stage CW Ladder → +HV
````

### Current Differential Configuration

```text
                 ┌→ 18-Stage Positive Ladder → +HV
AC HV Source ────┤
                 └→ 18-Stage Negative Ladder → -HV
```

The two ladders are mirrored with opposite diode orientations. Instead of placing the full voltage on one rail, the differential configuration produces approximately equal positive and negative potentials.

For example:

```text
+400 kV
   ↕
800 kV Differential
   ↕
-400 kV
```

The useful output is:

```text
Vdiff = V+ - V-
```

---

## Why Differential?

Splitting one 36-stage ladder into two 18-stage ladders provides several advantages:

* Lower voltage stress relative to the center reference
* Better insulation management
* More symmetrical electric-field distribution
* Shorter individual multiplier chains
* Reduced parasitic effects
* Lower voltage sag
* Better performance under load

Testing so far has shown noticeably improved discharge behavior compared with the original continuous configuration.

---

## Circuit Design

Both 18-stage ladders are driven from the same high-frequency AC source.

One ladder generates **+HV**, while the mirrored ladder generates **-HV**.

### Circuit Diagram

![Alt text](https://github.com/VictorGranado/CockCroft-Walton-Voltage-Multiplier/blob/bba988de6492d9c8374b10e4d0502db46ab13647/Screenshot%202026-08-16%20181642.png)

---

## Theoretical Output Calculations

For a standard Cockcroft-Walton multiplier:

```text
Vout = (2)(n)(Vin)
```

For the original 36-stage ladder:

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

Therefore, both configurations have approximately the **same ideal total output voltage**, but the differential design divides it between two rails.

### Output Scenarios

| Scenario         | AC Input |     +HV |     -HV | Ideal Differential Output |
| ---------------- | -------: | ------: | ------: | ------------------------: |
| **Best Case**    |    20 kV | +720 kV | -720 kV |               **1.44 MV** |
| **Conservative** |    12 kV | +432 kV | -432 kV |                **864 kV** |
| **Worst Case**   |     5 kV | +180 kV | -180 kV |                **360 kV** |

> These are theoretical no-load values and should not be interpreted as measured output voltages.

---

## Air Breakdown Estimates

A common approximation for the dielectric strength of air is:

```text
~3 kV/mm
~30 kV/cm
~3 MV/m
```

Using:

```text
Distance ≈ Voltage / 3 kV/mm
```

| Scenario     | Ideal Voltage | Approx. Uniform-Air Breakdown |
| ------------ | ------------: | ----------------------------: |
| Best Case    |       1.44 MV |                        ~48 cm |
| Conservative |        864 kV |                      ~28.8 cm |
| Worst Case   |        360 kV |                        ~12 cm |

Actual arc distance can differ significantly because of electrode geometry, humidity, corona, available current, streamer formation, and nearby conductive objects.

---

## Component Voltage Stress

Individual CW stages can experience voltages on the order of approximately:

```text
Vstage ≈ 2Vin
```

| Input | Approx. Stage Voltage |
| ----: | --------------------: |
| 20 kV |                ~40 kV |
| 12 kV |                ~24 kV |
|  5 kV |                ~10 kV |

This makes component voltage rating, insulation, spacing, and field control critical.

---

## Real-World Losses

The ideal equation assumes perfect components and zero load.

Actual output is closer to:

```text
Vreal ≈ Videal - voltage sag - source losses - corona losses - leakage - parasitic losses
```

Cockcroft-Walton voltage sag increases strongly with stage count and approximately follows:

```text
Vsag ∝ (I × n³) / (f × C)
```

where:

* `I` = load current
* `n` = number of stages
* `f` = AC frequency
* `C` = stage capacitance

This is one of the major advantages of the differential configuration.

For comparison:

```text
Single ladder:
36³ = 46,656

Two 18-stage ladders:
2 × 18³ = 11,664
```

Therefore:

```text
11,664 / 46,656 ≈ 0.25
```

In an idealized comparison, the **18 + 18 configuration can reduce the stage-count-related voltage sag to roughly one quarter of a single 36-stage ladder**, assuming comparable frequency, capacitance, and loading conditions.

At these voltages, however, **corona, parasitic capacitance, leakage, insulation losses, and transformer impedance can dominate**, so actual output may be substantially below the ideal calculations.

---

## Experimental Observations

### Stable Corona / Plasma Regions

Certain electrode geometries produce stable visible corona or plasma without transitioning into a complete arc.

Small changes in:

* Electrode spacing
* Shape
* Orientation
* Nearby conductive objects

can significantly affect discharge behavior, demonstrating the importance of **electric-field geometry and concentration**.

---

## Ionic Wind

Stable corona operation produces noticeable airflow around the electrodes.

This is consistent with **ionic wind**, where charged particles accelerated by the electric field transfer momentum to surrounding air molecules.

---

## Magnet Experiments

Permanent magnets placed near the discharge produced several noticeable effects:

* Collapse of stable plasma regions
* Changes in discharge geometry
* Slightly increased arc distance when placed near electrode tips

Possible causes include:

* Electric-field distortion
* Changes in parasitic capacitance
* Changes in electrode geometry
* Multiplier loading
* Possible interaction between magnetic fields and moving charged particles

Further controlled testing is needed to separate magnetic effects from electrostatic effects.

---

## EMF / RF Observations

Strong electromagnetic activity has also been detected around the system.

Possible sources include:

* High-frequency transformer operation
* Capacitor charging currents
* Corona discharge
* Streamer formation
* Fast arc-current transitions

Although the final multiplier output is primarily DC, the system contains significant high-frequency electrical activity.

---

## Next Steps

### Oil Insulation

The next major upgrade is immersing the multiplier in **dielectric insulating oil** to reduce:

* Corona losses
* Surface tracking
* Air breakdown between stages
* Leakage currents
* Premature internal discharge

Better insulation should allow the multiplier to operate closer to its practical voltage limit.

### Improved Arc Performance

Future testing will focus on:

* Longer and more repeatable arcs
* Improved electrode geometry
* Reduced corona losses
* Better output stability
* Different terminal designs
* Further magnetic-field experiments

---

## Project Goals

This project serves as an experimental platform for studying:

* Cockcroft-Walton voltage multiplication
* Differential high-voltage systems
* Corona and plasma formation
* Streamer development
* Ionic wind
* Electric-field geometry
* Parasitic capacitance
* High-voltage insulation
* Electromagnetic interference

---

## Development Series

* **Part 1** — Initial multiplier
* **Part 2** — Higher-voltage testing
* **Part 3** — Differential configuration and field experiments
* **Part 4** — Coming soon

---

## Safety

> ⚠️ **EXTREME HIGH-VOLTAGE WARNING**

This project involves potentially lethal voltages.

High-voltage capacitors and multiplier stages can remain charged **after power has been disconnected**.

Potential hazards include:

* Electric shock
* Stored-energy discharge
* Burns
* Fire
* Component failure
* Unexpected arcing
* RF / EMI interference
* Damage to nearby electronics

Never assume the circuit is discharged simply because visible corona or arcing has stopped.

This repository documents an experimental engineering project and is **not intended as a beginner construction guide**.

---

## Disclaimer

All voltage calculations are theoretical unless explicitly identified as measured values.

Actual performance is affected by:

* Corona
* Leakage
* Parasitic capacitance
* Source impedance
* Voltage sag
* Humidity
* Insulation breakdown
* Electrode geometry
* Load current

The theoretical values provide an upper-bound reference for comparing future measurements and design improvements.

---

## Future Updates

More circuit diagrams, experimental results, insulation improvements, and discharge tests will be added as the project develops.

**Part 4 coming soon.**

```
```
