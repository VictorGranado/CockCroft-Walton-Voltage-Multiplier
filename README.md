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

The full output voltage was developed on a single high-voltage rail relative to the reference potential.

### Current Differential Configuration

```text
                 ┌→ 18-Stage Positive Ladder → +HV
AC HV Source ────┤
                 └→ 18-Stage Negative Ladder → -HV
```

The two ladders are mirrored, with opposite diode orientations.

Instead of developing the entire voltage on one side, the system produces approximately equal positive and negative potentials.

For example, a theoretical **800 kV differential output** would ideally correspond to approximately:

```text
+400 kV
   ↕
800 kV Differential
   ↕
-400 kV
```

These values are theoretical. Actual output is strongly affected by loading, corona, leakage, parasitic capacitance, component tolerances, humidity, geometry, and insulation.

---

## Why Differential?

Moving from one continuous ladder to two shorter mirrored ladders provides several practical advantages:

* Lower voltage stress relative to the center reference
* Improved insulation management
* More symmetrical electric-field distribution
* Shorter individual multiplier chains
* Reduced influence of some parasitic effects
* Potentially reduced voltage sag under load
* Improved overall experimental performance

Testing so far has shown noticeably better discharge behavior compared with the original continuous configuration.

---

## Circuit Design

The system uses a high-frequency AC high-voltage source to drive two Cockcroft-Walton ladders.

One ladder pumps charge toward **+HV**, while the second ladder is mirrored to generate **-HV**.

The useful differential voltage is:

```text
Vdiff = V+ - V-
```

The circuit diagram for the current **18 + 18 differential configuration** is included in this repository.

### Circuit Diagram

```text
/circuit-diagram/
```

---

## Experimental Observations

### Stable Corona / Plasma Regions

Certain electrode positions and geometries generate a stable visible corona or plasma region without transitioning into a complete arc.

Small changes in:

* Electrode spacing
* Electrode shape
* Orientation
* Nearby conductive objects
* Surface geometry

can significantly affect discharge behavior.

This demonstrates how strongly high-voltage systems depend on **local electric-field concentration and geometry**, rather than voltage alone.

---

## Ionic Wind

During stable corona operation, a noticeable air current can form around the electrodes.

This is consistent with **electrohydrodynamic flow**, commonly known as **ionic wind**.

Charged particles accelerated by the electric field collide with neutral air molecules and transfer momentum to them, producing airflow without mechanical moving parts.

---

## Magnet Experiments

Permanent magnets placed near certain areas of the discharge noticeably changed its behavior.

Observed effects include:

* Collapse of stable plasma regions at certain positions
* Changes in discharge shape
* Slight increases in apparent arc distance when magnets were placed near the electrode tips

Several mechanisms may contribute:

* Electric-field distortion caused by the conductive magnet
* Changes in parasitic capacitance
* Additional loading of the multiplier
* Changes in electrode geometry
* Possible magnetic interaction with moving charged particles

Further controlled experiments are needed to distinguish magnetic effects from purely electrostatic effects.

---

## EMF / RF Observations

Strong electromagnetic activity has also been detected around the system.

Possible sources include:

* High-frequency transformer operation
* Rapid capacitor charging currents
* Displacement currents throughout the multiplier
* Corona discharge
* Streamer formation
* Fast arc-current transitions

Although the final multiplier output is primarily DC, the system contains significant high-frequency electrical activity.

---

## Next Steps

### Oil Insulation

The next major upgrade is immersing the multiplier in **dielectric insulating oil**.

The goal is to reduce:

* Unwanted corona
* Surface tracking
* Air breakdown between stages
* Leakage currents
* Premature internal discharge

Improved insulation should allow the multiplier to operate closer to its practical voltage limit.

### Improved Arc Performance

Future testing will focus on:

* Longer discharge distances
* More repeatable arcs
* Improved electrode geometry
* Reduced corona losses
* Improved output stability
* Comparing different terminal shapes
* Further magnetic-field experiments

---

## Project Goals

This project serves as an experimental platform for studying:

* Cockcroft-Walton voltage multiplication
* High-voltage power electronics
* Differential high-voltage systems
* Corona discharge
* Plasma formation
* Streamer development
* Ionic wind
* Electric-field geometry
* Parasitic capacitance
* High-voltage insulation
* Electromagnetic interference

---

## Development Series

The project is being documented as a multi-part experimental series.

* **Part 1** — Initial multiplier
* **Part 2** — Higher-voltage testing
* **Part 3** — Differential configuration and field experiments
* **Part 4** — Coming soon 

---

## Safety

> ⚠️ **EXTREME HIGH-VOLTAGE WARNING**

This project involves potentially lethal voltages.

High-voltage capacitors and multiplier stages can remain charged **after the power supply has been disconnected**.

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

All voltage calculations presented in this project are theoretical unless explicitly identified as measured values.

At high stage counts, ideal Cockcroft-Walton equations do not fully represent real-world behavior.

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

---

## Future Updates

More circuit diagrams, experimental results, insulation improvements, and discharge tests will be added as the project develops.

**Part 4 coming soon. **

```
```
