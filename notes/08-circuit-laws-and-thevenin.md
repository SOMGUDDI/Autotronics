# 8. Circuit Laws — KCL, KVL, Mesh/Nodal Analysis, Thevenin's Theorem

## 8.1 Kirchhoff's Current Law (KCL) — Junction Rule

> At any junction, the sum of the currents must equal zero.

```
Σ I_junction = 0
```

Equivalent statement: current entering a node = current leaving it.

## 8.2 Kirchhoff's Voltage Law (KVL) — Loop Rule

> The sum of the potential differences across all elements around any
> closed circuit loop must be zero.

```
Σ ΔV_closed loop = 0
```

### Worked example

Loop with two EMF sources and two resistors in series:
`ε₁ = 6.0 V`, `ε₂ = 10 Ω`(as resistor)... using the general form:

```
Σ ΔV = 0  ⇒  ε₁ − IR₁ − ε₂ − IR₂ = 0
I = (ε₁ − ε₂) / (R₁ + R₂) = (6.0 V − 12 V) / (8.0 Ω + 10 Ω) = −0.33 A
```

(The negative sign indicates the assumed current direction was opposite to
the actual direction — a standard KVL bookkeeping result.)

![KCL and KVL statements with worked example](/assets/img/kcl-kvl.png)

## 8.3 Two circuit-solving methods demonstrated

### Method 1 — Mesh Analysis

- Assume a **mesh current** in each independent loop (e.g. `I_A` in loop 1,
  `I_B` in loop 2).
- Write KVL around each mesh in terms of these mesh currents, e.g.:

```
Loop 1:  10·I_A + 10(I_A − I_B) + 10 − 10 = 0
Loop 2:  5·I_B − 20 − 10 + 10(I_B − I_A) = 0
```

- Solve the resulting simultaneous equations for `I_A`, `I_B`; branch
  currents like `I_3 = I_A` (or similar, depending on the circuit
  topology) fall out directly.
- Homework noted: solving the resulting system of simultaneous equations.

![Mesh analysis worked example](/assets/img/kvl-example.png)

### Method 2 — Nodal Analysis

- Assign a reference node (ground) and unknown node voltages.
- Apply **KCL** at each non-reference node, expressing branch currents via
  Ohm's law in terms of node voltages.
- Example equations built in class at two nodes (labelled 1 and 2):

```
Node 1:   10·I₁ − 10·I₂ + 10 = 10
Node 2:    5·I₃ − 20 − 10 + 10·I₂ = 0
Constraint: I₁ + I₂ = I₃
```

(Exact coefficients depend on the specific resistor values in the circuit
being solved — the structure/approach is the transferable part.)

![Nodal analysis setup](/assets/img/mesh-nodal.png)

### General series/parallel reduction (recap, avoid overkill)

For simpler circuits, plain series/parallel reduction plus KVL is often
enough — no need for full mesh/nodal machinery. Example shown in class:

```
V = V_R1 + V_R2     (KVL, series-ish branch)
R2 ∥ R3  ⇒  R_eq = R2R3/(R2+R3)
V = I·R1 + I·(R2R3)/(R2+R3)
```

## 8.4 Thevenin's Theorem

> **Thevenin voltage (V_TH)** is the voltage across the load terminals when
> the load resistor is removed (open-circuited).
>
> **Thevenin resistance (R_TH)** is the resistance an ohmmeter would
> measure across the load terminals **with all independent sources
> replaced by their internal resistance** (voltage sources shorted, current
> sources opened) and the load removed.

```
I_L = V_TH / (R_TH + R_L)
```

Any linear circuit with DC sources and linear resistances, as seen from two
load terminals A–B, can be replaced by a single voltage source `V_TH` in
series with a single resistor `R_TH`.

![Thevenin's theorem statement and equivalent-circuit concept](/assets/img/thevenin-intro.png)

### Worked example 1

Three resistor networks reducible via series/parallel combination rules to
find `R_TH`, then `V_TH` found by open-circuiting the load and solving the
remaining circuit (voltage-divider style, since no current flows into the
open load branch).

![Thevenin worked resistor network](/assets/img/thevenin-example1.png)

### Worked example 2 — step-by-step reduction

Given `R_L1 = 100 Ω`, `R_L2 = 1000 Ω`, `R_L3 = 5 kΩ` combined with a 6 kΩ,
4 kΩ, 3 kΩ network and a 72 V source:

1. **100 Ω in series with 4 kΩ** → `4100 Ω`
2. **4100 Ω in parallel with 3000 Ω** → `R_eq = (4100 × 3000)/(4100+3000) ≈ 2410 Ω`... (worked numerically on slide, shown as `4100×3000/7100`)
3. **Result in series with 6 kΩ** → final `R_eq`
4. **Current:** `I = 72V / R_eq`
5. Then find `I₁`, `I₂`, `I₃` in the individual branches using current
   division on the parallel section.

![Thevenin equivalent reduction, worked numeric example](/assets/img/thevenin-example2.png)

### General Thevenin worked circuit with two sources

A circuit with two batteries (`B₁ = 28V` with `R₁ = 4Ω`, `B₂ = 7V` with
`R₃ = 1Ω`) and a load `R₂ = 2Ω`:

1. Remove the load → find `V_TH` (open-circuit voltage across load
   terminals) via superposition/series-parallel analysis of the remaining
   two-source network. Result on slide: `E_Thevenin = 11.2 V`.
2. Replace sources with their internal resistances → find `R_TH` by
   combining `R₁ ∥ R₃` etc.
3. Re-attach the load `R_L = 2Ω` to the simplified Thevenin equivalent
   (`V_TH` in series with `R_TH`) and solve for load current/voltage
   directly.

## 8.5 Why Thevenin's theorem matters here

The instructor's framing: this circuit is a stand-in for **"any circuit
with DC sources and linear resistances"**, and the "load" terminal can be
swapped for *anything* — a TV, a washing machine, a microwave — the same
Thevenin-equivalent source (`V_TH`, `R_TH`) will correctly predict how that
new load behaves, without re-deriving the whole source network each time.
This is exactly the mental model used later for analysing how a sensor's
output behaves once it's connected to signal-conditioning circuitry.
