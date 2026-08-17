# 6. Inductors & Magnetism

## 6.1 Inductor basics

**Any current-carrying conductor produces a magnetic field.** An inductor
is an **N-turn coil wound on a core**, giving it both an electrical and a
magnetic aspect. Used as filters, in motors, transformers, etc.

> An inductor opposes the rate of change of current flowing through it due
> to the build-up of self-induced energy within its magnetic field.

```
V_L(t) = dΦ/dt = L·(di/dt)         (Ohm's-law analogue for an inductor)
```

- `Φ` = magnetic flux (Weber)
- `L` = inductance (Henry)
- `i` = current (Ampere)
- `V` = voltage

![Inductor symbol, coil, and equations](../assets/img/inductor-basics.png)

### Two key behavioural facts

1. **Current through an inductor cannot change instantaneously** (because
   of the `di/dt` term).
2. **A fully-charged inductor acts as a short circuit** — once fully
   "charged" (current has stabilised), there is no further change in
   current, so the induced back-EMF is zero and the inductor presents zero
   resistance to steady current, exactly like the closed-switch case in
   note 03 §3.4.
3. A **fully-charged inductor also acts as a current source** (it will
   try to maintain its established current if the circuit changes
   suddenly).

### Time constant

```
i(t) = I₀ · e^(−R/L · t)
```

`L/R` is the **time constant** — it determines how fast the inductor
charges or discharges (this is the RL analogue of the RC time constant).

## 6.2 Inductors as sensors

A changing flux `dΦ/dt` induces a voltage (EMF) — this is the basis for
using coils as **speed/position sensors** (e.g. inductive crankshaft
sensors): a rotating toothed wheel near a coil changes the flux linking the
coil as it turns, inducing a voltage pulse per tooth.

![Inductor used as a sensor — flux change induces EMF](../assets/img/inductor-sensor.png)

## 6.3 Right-hand rule & magnetic flux lines

Point the thumb in the direction of conventional current flow; the curled
fingers show the direction of the magnetic field/flux lines around the
conductor. Wrapping a wire into a coil concentrates and aligns these flux
lines. Wrapping the coil around a **ferromagnetic core** further
concentrates the flux lines *inside* the core (air alone has no
concentrating medium, so flux in air spreads out and cannot be as tightly
directed).

![Right-hand rule and coil](../assets/img/right-hand-rule.png)
![Magnetic field around current-carrying wire; bar magnet field](../assets/img/magnetic-field-basics.png)

## 6.4 Faraday's Law and mutual induction (Transformer principle)

```
e = −N · dΦ/dt
```

- `N` = number of turns
- `e` = induced EMF
- Sign convention: `e₁ = −N₁ dΦ/dt` in the primary, and the same changing
  flux, linking the secondary coil `N₂`, induces `e₂ = −N₂ dΦ/dt` in the
  secondary.

### How a transformer works (from the four-panel animation)

1. **Switch open, no current flowing** — no field, no induced voltage.
2. **Switch closed, current building up** — magnetic field builds up,
   voltage is induced into the secondary (transient).
3. **Switch closed, current flow constant** — magnetic field steady, **no
   voltage induced into secondary** (a constant flux induces nothing).
4. **Switch open, current flow stops** — magnetic field collapses, a
   (reverse-polarity) voltage is again induced into the secondary.

![Four-stage transformer flux animation](../assets/img/magnetic-field-transformer.png)

**This is exactly why a transformer only works on AC, never DC**: DC would
settle to a constant flux (step 3), inducing zero secondary voltage — "the
core will saturate" and stop producing any change once current is steady.
AC continuously changes, so it continuously induces a secondary voltage.

### Formal transformer relations

```
Primary:    v₁ → i₁ → Φ₁ → e₁ = −N₁ dΦ/dt
Secondary:  e₂ = −N₂ dΦ/dt → i₂ → v₂

If N₁ = N₂  ⇒  isolation transformer (voltage ratio 1:1, used for
                electrical isolation / protection, not for stepping voltage)
```

![Transformer principle, primary/secondary](../assets/img/transformer-principle.png)

### Coupled-coil arrangement (physical demo referenced in class)

Two separate coils (Coil-1 driven by a switch+battery, Coil-2 connected to
a galvanometer) demonstrate mutual induction without a shared core —
flux from Coil-1 links Coil-2 and induces a measurable current there when
Coil-1's current changes.

![Inductor coil arrangement / coupled coils demo](../assets/img/inductor-arrangement.png)

## 6.5 Four basic magnetic-electric relationships (from slide "Magnetic field")

1. A current-carrying wire produces a magnetic field around it.
2. A time-changing magnetic field induces a voltage in a coil linked by it.
   *(basis of transformer action)*
3. A current-carrying wire in the presence of a magnetic field experiences
   a force. *(basis of motor action)*
4. A moving wire in the presence of a magnetic field has a voltage induced
   in it. *(basis of generator action)*

## 6.6 DC Motor (Actuator)

A coil (armature) carrying current sits inside a magnetic field between
poles N and S. The force on the current-carrying coil (fact #3 above)
produces a turning effect. A **split-ring commutator** with **brushes**
reverses the current direction in the coil every half-turn, so the torque
keeps acting in the same rotational sense, producing continuous rotation.

![DC motor coil-in-field demo with commutator/brushes](../assets/img/dc-motor.png)

The motor's turning effect: current flowing through the coil in a magnetic
field experiences a force (`F`) on each side of the loop in opposite
directions, creating a torque. As the coil rotates through the field, the
force weakens near the pole faces and strengthens elsewhere (visualised via
the flux-density diagram).

![DC motor operation — turning effect of a coil in a magnetic field](../assets/img/dc-motor-detail.png)

## 6.7 Symbol / formula quick reference

| Quantity | Symbol | Unit |
|---|---|---|
| Magnetic flux | Φ | Weber (Wb) |
| Inductance | L | Henry (H) |
| Current | i | Ampere (A) |
| Induced EMF | e | Volt (V) |
| Number of turns | N | — |
