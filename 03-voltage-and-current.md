# 3. Voltage and Current Fundamentals

## 3.1 The water analogy

| Electrical quantity | Water analogy |
|---|---|
| Charge | Water |
| Voltage | Pressure |
| Current (charge per unit time) | Flow |

![Water analogy for voltage/current](../assets/img/vi-water-analogy.png)

Batteries in series behave like water tanks stacked in series — each cell
adds its pressure (voltage), e.g. 1.5 V + 1.5 V + 1.5 V = 4.5 V, and so on.
A comparison of an "electrical system" ladder (1.5 V steps up to 6.0 V,
with LED brightness increasing) against a "water system" ladder (PSI
pressure increasing, water flow increasing, lamp brightness increasing) —
both stacks behave identically in principle.

![Electrical vs water system side by side](../assets/img/vi-electric-water.png)

## 3.2 AC vs DC

Two types of voltage/current exist:

- **DC (Direct Current):** defined by **amplitude** only.
- **AC (Alternating Current):** defined by **amplitude and frequency**.

### DC voltage

```
v(t) = V · u(t)
u(t) = 1  for t ≥ 0
u(t) = 0  for t < 0
```

(`u(t)` is the unit step function — a DC source switches on at t = 0 and
stays constant.)

### AC voltage

```
v(t) = Vm sin(ωt)
ω = 2πf        (ω = angular frequency, f = frequency)
T = 1/f        (T = time period)
```

![DC voltage and AC sine wave plots](../assets/img/vi-dc-ac-plots.png)

**Class note:** when categorising sensor outputs earlier, whether the
output was AC or DC wasn't specified — sensors will later be explicitly
classified as producing AC or DC outputs. Regardless, **the signal that
finally reaches the ECU is always DC.**

## 3.3 Ohm's Law

```
V = I · R
```

- V ∝ I (voltage is directly proportional to current, for a fixed
  resistance R).
- For **DC**: `V = IR` directly.
- For **AC**, if `v(t) = Vm sin(ωt)`, then `i(t) = Im sin(ωt)` too — voltage
  and current are **in phase** for a pure resistor (see waveform below).

## 3.4 Open circuit vs. short circuit — worked example

Circuit: source `Vin = 5V`, switch `S`, load, nodes A and B.

**Case 1 — Switch S open (open circuit):**
- Current `I = 0`
- Offers **infinite resistance**
- `V_A = 5V`, `V_B = 0V`
- `V_AB = V_A − V_B = 5V` (you would measure the full source voltage across
  the open switch)

**Case 2 — Switch S closed (short circuit through switch):**
- Current `I ≠ 0`
- Offers **zero resistance**
- `V_A = V_B = 5V`
- `V_AB = 0V` (both points are at the same potential — no drop across a
  zero-resistance closed switch, even though current is flowing)

This open/short-circuit reasoning is reused later to explain how a
**fully-charged inductor behaves like a short circuit** and a
**fully-charged capacitor behaves like an open circuit** (see notes 05 and
06).

## 3.5 Series vs parallel measurement rule

> **Voltage is always measured in parallel across a component.**
> **Current is always measured in series (in the current path).**

This is why, in practice, you cannot insert an ammeter into a live
high-current line without breaking the circuit — instead, **clamp meters**
(based on current-transformer / potential-transformer, ultimately
Hall-effect, principles) are used to measure current without cutting the
wire.
