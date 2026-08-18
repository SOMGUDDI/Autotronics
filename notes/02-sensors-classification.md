# 2. Sensor Classification

## 2.1 Three-way classification

| Category | Sub-types |
|---|---|
| **Physical sensors** | Temperature, Pressure, Position, Level |
| **Electrical sensors** | Current, Voltage |
| **Chemical / environmental sensors** | Gas concentration, Humidity, Fluid |

## 2.2 Classification by underlying technology

All sensor technologies used in this course reduce to **three broad
categories** (the property of the material/component is exploited to build
the sensor):

1. **Resistive** — potentiometers, voltage-divider based sensors, series &
   parallel resistor networks
2. **Inductive** — magnetic-field based; Hall-effect sensors are treated as
   a sub-case of inductive sensing
3. **Capacitive** — depends on voltage and the distance between plates;
   piezoelectric sensors are treated as a capacitive sub-case

> There are more categories in general sensor engineering, but for this
> course these three are the broad buckets everything is mapped into.

## 2.3 What is actually measured vs calculated

- **Measured (has a sensor):** Speed, Temperature, Pressure, Flow, Position,
  Voltage, Current
- **Calculated (no direct sensor):** Power, SOC, and similar derived
  quantities

All of the above measured physical quantities are ultimately **calibrated
in terms of Voltage and Current**, using resistive, inductive, or
capacitive technology.

## 2.4 Sensor vs. Transducer (class discussion)

A student asked about the difference. The instructor's practical answer:

- Historically the terms are used interchangeably.
- Practically, a device like an **LVDT (Linear Variable Differential
  Transformer)** can, in principle, be read directly/mechanically (a
  "screw-gauge"-like physical readout) — this is closer to what people
  originally meant by *transducer*.
- What this course calls a **sensor** always needs an **electronic
  interface**: you cannot read a value off it without processing an
  electrical signal.

This is not a universally agreed distinction, but it is the working
definition used in the course.

## 2.5 Amplitude ranges and signal conditioning motivation

- Many raw sensor outputs are only **millivolts or microvolts** — too small
  for the ECU to use directly, so they must be **amplified**.
- Some signals (e.g. **engine knock**) sit inside a noisy environment, so
  the true signal has to be **filtered** out of surrounding disturbance.
- Amplification + attenuation + filtering + noise elimination are
  collectively called **signal conditioning**, covered in a later module
  (Op-amps, filters).

## 2.6 The complete instrumentation loop (repeated for emphasis)

```
Measurable/measured quantity
        │
        ▼
     Sensor  (Resistive / Inductive / Capacitive)
        │  (raw analog signal, may be mV–µV range, 0–5V typical after scaling)
        ▼
 Signal Conditioning  (amplify / attenuate / filter noise)
        │  (clean analog signal)
        ▼
      ADC   (Analog-to-Digital Converter)
        │  (digital word)
        ▼
      ECU
        │  (digital output, if actuation needed)
        ▼
      DAC   (Digital-to-Analog Converter)
        │
        ▼
    Actuator
```
