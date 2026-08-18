# Autotronics — Electrical & Electronics Fundamentals

**Course:** AELZG533 / AEZG533 — Autotronics
**Instructor:** Dr. Madhuri Bayya, BITS Pilani (Engineering Group)
**Session covered:** L2 & L3 — *Electrical and Electronics Fundamentals* (9 Aug 26)
**Source material:** Lecture slide deck (117 slides, with in-class handwritten annotations) + full class transcript/recording

---

## Why this lecture exists

Before the course can talk about specific automotive subsystems (engine
control, braking, EV powertrain, comfort/safety systems), everyone in the
class — mechanical or electrical background — needs a **common electrical
and electronics vocabulary**. This lecture builds that vocabulary from the
ground up, and it does so in a very deliberate order:

```
Engine subsystem example
        │
        ▼
What sensors does it need?
        │
        ▼
What technology does each sensor use?  (Resistive / Inductive / Capacitive)
        │
        ▼
What are we actually measuring/calibrating? (Voltage, Current — NOT power)
        │
        ▼
⇒ Therefore we must learn: R, L, C, V, I → Magnetics → Signal conditioning
   → Semiconductor switches → ADC/DAC → Digital fundamentals
```

The instructor's key teaching point: **you only measure or calibrate a
sensor in terms of Voltage and Current.** Power, speed, SOC (state of
charge), etc. are *calculated/derived* quantities, never measured directly.

## How these notes are organized

| # | File | Topic |
|---|------|-------|
| 00 | `00-overview.md` | This file — course map |
| 01 | `01-systems-and-signal-flow.md` | System flow, building blocks, engine control system, EV sensors |
| 02 | `02-sensors-classification.md` | Sensor types, technologies, signal chain (Sensor → Signal Conditioning → ADC → ECU) |
| 03 | `03-voltage-and-current.md` | Voltage/current basics, AC vs DC, water analogy, Ohm's law |
| 04 | `04-resistors-and-networks.md` | Resistors, colour code, series/parallel, voltage & current dividers |
| 05 | `05-capacitors.md` | Capacitor theory, energy storage, series/parallel |
| 06 | `06-inductors-and-magnetism.md` | Inductors, magnetic fields, Faraday's law, transformers, DC motor |
| 07 | `07-ac-fundamentals-impedance.md` | AC Ohm's law, reactance, impedance, phasors, power factor |
| 08 | `08-circuit-laws-and-thevenin.md` | KCL/KVL, mesh & nodal analysis, Thevenin's theorem |
| 09 | `09-semiconductor-basics.md` | Conductors/insulators/semiconductors, doping, PN junction |
| 10 | `10-diodes-and-applications.md` | Diode behaviour, rectification, alternator charging |
| 11 | `11-transistors-bjt-mosfet.md` | BJT, transistor as a switch, FET/MOSFET |
| 12 | `12-digital-logic-gates.md` | AND/OR/NOT/NAND/NOR/XOR gates, CMOS NOT gate, IC pinouts |
| 13 | `13-boolean-algebra.md` | Boolean laws, De Morgan's theorem, worked design example |
| 14 | `14-power-electronics-thyristors.md` | Voltage chopping, SCR/Thyristor, Triac |

## Quick-reference: the "fundamentals checklist" from class

The instructor built this list live in class — it is effectively the
syllabus for this block of lectures:

1. **Fundamentals of R, L, C, V, I** (this lecture — mostly done)
2. **Fundamentals of magnetic fields**
3. **Signal conditioning** — Op-amps, filters
4. **Semiconductor switches** — protection, power conversion
5. **Fundamentals of ADC & DAC**
6. **Digital fundamentals** — logic gates, Boolean algebra

Items 1, 2, 4, 6 were substantially covered in this lecture; items 3 and 5
(signal conditioning, ADC/DAC) are deferred until after sensors are
introduced, since they make more sense in that context.

## Golden rules repeated throughout the lecture

- **You cannot measure power directly** — only voltage, current, and
  temperature are measured; power, SOC, speed (in this EV context) etc. are
  calculated.
- **Voltage is measured in parallel; current is measured in series.**
- A **sensor** needs an electronic interface to be read; a **transducer**
  (e.g. an LVDT) can sometimes be read directly/mechanically. The line
  between the two terms is blurry, but this is the practical distinction
  drawn in class.
- Every sensor technology reduces to one of three physical properties:
  **resistive, inductive, or capacitive** (Hall-effect and piezoelectric are
  treated as sub-cases of inductive and capacitive respectively).
- Signal chain: **Measured quantity → Sensor → Signal Conditioning
  (amplify/attenuate/filter) → ADC → ECU → (DAC) → Actuator.**
