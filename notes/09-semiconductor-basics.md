# 9. Semiconductor Fundamentals

## 9.1 Classification of materials by electrical resistance

Materials span a huge resistance range from very low (conductors) to very
high (insulators), with semiconductors in between:

```
Low resistance (10⁻¹⁰) ──────────────────────────► High resistance (10¹⁸)
   Conductors            Semiconductors              Insulators
Gold, Silver,            Silicon, Germanium,        Glass, Rubber, Oil,
Copper, Iron,            Selenium, Gallium          Plastic, Diamond, etc.
Aluminum, etc.           arsenide, etc.
```

![Classification of materials by resistance](/assets/img/material-classification-1.png)

### Band-gap (energy-band) view

- **Conductor:** conduction band and valence band **overlap** — no band
  gap — electrons move freely.
- **Semiconductor:** a narrow band gap (~1 eV for silicon) separates
  valence and conduction bands — electrons can cross it with modest energy
  (heat, light, doping), leaving behind **holes**.
- **Insulator:** a wide band gap (~5 eV or more) — electrons essentially
  cannot cross into the conduction band under normal conditions.

![Energy band diagrams: conductor, semiconductor, insulator](/assets/img/material-classification-2.png)

## 9.2 Conductor vs Insulator — atomic view

- **Copper atom** (good conductor): only **one electron** in the outermost
  orbit — very loosely bound, easily donated to conduction.
- **Neon atom** (poor conductor/insulator gas): **eight electrons** in the
  outermost orbit — a full/stable shell, strongly bound, nothing to spare
  for conduction.

![Copper vs Neon atomic structure](/assets/img/conductor-insulator.png)

## 9.3 Silicon — the semiconductor atom

A silicon atom has **4 valence electrons**. In a silicon crystal, each
silicon atom is surrounded by **4 other silicon atoms**, and adjacent atoms
**share one electron each** — this is **covalent bonding**.

At room temperature, some valence electrons gain enough thermal energy to
leave their covalent bond/orbit. Where an electron leaves, it creates a
**hole** (an effective positive charge) — this is called **electron-hole
pair generation**.

![Silicon atom and crystal lattice](/assets/img/semiconductor-atom.png)

## 9.4 Doping — creating N-type and P-type semiconductors

Pure ("intrinsic") silicon is a poor conductor at room temperature.
**Doping** deliberately introduces impurity atoms to increase conductivity
in a controlled way.

### N-type: Pentavalent doping

- **Pentavalent atoms** (5 valence electrons) — e.g. **Arsenic, Antimony,
  Phosphorus**.
- Only 4 of the 5 electrons are needed for covalent bonding with
  neighbouring silicon atoms — the **5th electron is free**.
- Because these atoms *donate* an extra electron to the crystal, they are
  called **donor impurities**.
- Majority charge carriers: **electrons (e⁻)**.

### P-type: Trivalent doping

- **Trivalent atoms** (3 valence electrons) — e.g. **Aluminum, Boron,
  Gallium**.
- Only 3 electrons are available for the 4 required covalent bonds — one
  bond is left with a **missing electron**, i.e. a **hole**.
- Since these atoms create an excess of holes, they're called (implicitly)
  **acceptor impurities**.
- Majority charge carriers: **holes**.

```
N-type  →  majority carriers = electrons (e⁻)
P-type  →  majority carriers = holes
```

> **Note from class:** electrons have **higher mobility** than holes — an
> important reason NPN transistors are generally faster/preferred over PNP
> in many designs (discussed further in the transistor module).

![Pentavalent/trivalent doping, donor/acceptor atoms](/assets/img/doping-basics.png)
![N-type and P-type semiconductor structure](/assets/img/doping-np.png)

## 9.5 The P–N Junction

When P-type and N-type materials are joined, a **depletion layer** forms
at the junction — a region depleted of free carriers, because electrons
near the junction diffuse across and recombine with nearby holes, leaving
behind fixed (immobile) ion charges: negative ions on the P-side, positive
ions on the N-side of the junction.

![P-N junction: ions and depletion layer](/assets/img/pn-junction-1.png)
![P-N junction structure](/assets/img/pn-junction-2.png)

### Forward bias

- External voltage: **+ terminal to P-side, − terminal to N-side.**
- This *opposes/narrows* the depletion layer.
- **Switch is effectively ON**: majority carriers (holes from P, electrons
  from N) are pushed toward the junction, recombine, and current flows
  freely once `V ≥ ~0.7V` (silicon "knee" voltage).
- Depletion layer: **narrow**.
- Current flow: **large forward current** if `V_S > 0.7V`.

### Reverse bias

- External voltage: **− terminal to P-side, + terminal to N-side.**
- This *widens* the depletion layer.
- **Switch is effectively OFF**: the junction has no majority carriers
  available to cross, so (ideally) no current flows — only a tiny leakage
  current.
- Depletion layer: **wide**.
- Current flow: **small reverse (saturation/leakage) current**, unless
  breakdown voltage is exceeded.

| | Forward Bias | Reverse Bias |
|---|---|---|
| V_S polarity | (+) to P, (−) to N | (−) to P, (+) to N |
| Current flow | Large forward current if `V_S > 0.7V` | Small reverse (saturation + leakage) current |
| Depletion layer | Narrow | Wide |

![Forward vs reverse bias comparison table](/assets/img/pn-junction-bias-diagram.png)

### Physical/intuitive explanation (from class discussion)

- **Forward bias:** P's majority carriers are holes, N's majority carriers
  are electrons. Under forward bias, holes and electrons are pushed toward
  the junction; they **recombine**, and this recombination sustains current
  flow across the junction.
- **Reverse bias:** the junction has no majority carriers left near it (they've
  been pulled away from the junction by the reverse field), so essentially
  no current flows — only a small **leakage current**.

![Forward/reverse bias physical explanation with hand annotation](/assets/img/pn-junction-bias.png)

### Simple switch analogy

- **Switch (diode) ON** (forward biased) → voltage drop across the switch
  ≈ 0 → nearly all the source voltage appears across the load.
- **Switch (diode) OFF** (reverse biased) → the switch blocks the full
  source voltage (e.g. 12V) across itself; no current reaches the load.

## 9.6 Measuring a diode with a multimeter/curve tracer

A bench demo with a power supply, curve tracer, and multimeter is used to
show the diode's I–V characteristic directly (forward-bias knee,
reverse-bias leakage/breakdown regions).

![Diode curve-tracer/multimeter bench setup](/assets/img/pn-junction-bench.png)
