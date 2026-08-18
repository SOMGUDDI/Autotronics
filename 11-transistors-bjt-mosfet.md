# 11. Transistors — BJT & MOSFET

## 11.1 Bipolar Junction Transistors (BJT)

A BJT is a **three-terminal, two-junction** device: **Emitter, Base,
Collector**. It comes in two flavours:

- **PNP** — P-type / N-type / P-type
- **NPN** — P-type / N-type / P-type (mirrored: N / P / N)

### Doping levels (why they matter)

- **Emitter** — heavily doped
- **Base** — lightly doped (and physically very thin)
- **Collector** — intermediate doping, between the heavy emitter doping and
  the light base doping

**Why "Bipolar"?** Operation depends on **both** free electrons *and*
holes — both types of charge carrier participate, unlike unipolar (FET)
devices which use only one carrier type.

![PNP/NPN construction and two-diode analogy](../assets/img/bjt-basics.png)

### Two-diode analogy

A BJT can be thought of as **two back-to-back diodes** sharing a common
base region — e.g. for NPN: Base–Emitter junction and Base–Collector
junction, each behaving like a diode, but the thin shared base region is
what creates transistor action (rather than two independent diodes).

## 11.2 Transistor currents and current gain

```
I_E = I_C + I_B          (Emitter current = Collector + Base current)
I_C ≈ I_E                 (since I_B is very small)

α_dc = I_C / I_E           (common-base current gain, ≈ close to 1)
β_dc = I_C / I_B           (common-emitter current gain — "current gain of the transistor")
```

![Transistor current directions and gain formulas](../assets/img/bjt-symbols.png)

### Worked example

> A transistor has a collector current of 10 mA and a base current of
> 40 µA. What is the current gain?

```
β_dc = I_C / I_B = 10 mA / 40 µA = 250
```

A **small base current controls a much larger collector current** — this
amplification property is the essence of transistor action.

## 11.3 Transistor operating regions

Looking at the **I_C vs V_CE** output characteristic curves (a family of
curves, one per base current `I_B`):

- **Saturation region:** the transistor acts like a **short circuit** —
  current flows freely from collector to emitter, `V_CE ≈ 0`.
- **Cut-off region:** the transistor acts like an **open circuit** — no
  current flows from collector to emitter, regardless of `V_CE` (until
  breakdown).
- **Active (linear) region:** collector current `I_C` is **proportional**
  to the base current `I_B` flowing in — this is the region used for
  linear amplification.

![Transistor I_C vs V_CE output characteristics — three regions](../assets/img/bjt-regions.png)

## 11.4 Transistor as a switch

The most common automotive/embedded use of a BJT is **not** as a linear
amplifier but as a **digital switch**:

```
+6V ── R1 ──┬── LED (cathode to collector)
            │
         [NPN] ── base driven via R2 by a control switch SW1
            │
           GND (emitter)
```

- **SW1 open → I_B = 0 → transistor in cut-off → LED off** (transistor
  acts as open circuit).
- **SW1 closed → I_B flows → transistor driven into saturation → LED
  on** (transistor acts as closed/short circuit, sinking current from
  the LED to ground).

![Transistor-as-switch driving an LED](../assets/img/transistor-switch.png)

## 11.5 Field Effect Transistors (FET) — the "unipolar" alternative

**Why "Unipolar"?** Operation depends on **either** free electrons **or**
holes (not both) — only one type of carrier does the conducting.

Three terminals: **Gate (G), Drain (D), Source (S)**. The gate voltage
`V_GD`/`V_GS` controls the current flowing from Drain to Source without
drawing (significant) gate current — this is the key structural difference
from a BJT, where base *current* controls the collector current.

![FET structure and symbol](../assets/img/fet-basics.png)

## 11.6 MOSFET

**MOSFET** = Metal-Oxide-Semiconductor Field-Effect Transistor.

### Structure

```
Source (S)         Gate (G)         Drain (D)
   │                  │                 │
  [n⁺]───Channel region───[n⁺]     (n-channel MOSFET shown)
   └──────────────────────────────────┘
              p-type substrate (Body)
                     │
                   Oxide (SiO₂) insulates the metal gate from the channel
```

- The **Gate** is separated from the channel by a thin **oxide (SiO₂)
  insulating layer** — hence "Metal-Oxide-Semiconductor."
- **Gate voltage controls drain current** by attracting (or repelling)
  carriers to form/deplete a conducting channel between source and drain —
  again, essentially **no gate current** flows in normal operation (very
  high input impedance).
- Because there's no need to physically move a base-current's worth of
  charge carriers to switch it, a MOSFET switches **much faster** than an
  equivalent BJT.

![MOSFET cross-section structure](../assets/img/mosfet-structure.png)
![MOSFET circuit symbol and substrate view](../assets/img/mosfet-symbol.png)

### MOSFET advantages (as listed in class) vs BJT

- **Input impedance — very high** (gate draws almost no current)
- **Size — very small** (easier to integrate at high density, e.g. in ICs)
- **Less noisy** than BJT
- **No thermal runaway** (a failure mode where a BJT's collector current
  increases with temperature, which further increases temperature, in a
  positive-feedback loop — MOSFETs don't share this weakness in the same
  way)

## 11.7 BJT vs MOSFET — summary

| | BJT | MOSFET |
|---|---|---|
| Carrier type | Bipolar (electrons + holes) | Unipolar (one carrier type) |
| Control terminal | Base — controlled by **current** | Gate — controlled by **voltage** |
| Input impedance | Moderate/low | Very high |
| Switching speed | Slower | Much faster |
| Size | Larger | Very small |
| Noise | More | Less |
| Thermal runaway risk | Yes | No |
