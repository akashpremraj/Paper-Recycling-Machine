# Paper Recycling Machine — Final Year Project (BE Mechanical)

**Author:** Akash P Raj (USN: 4SN16ME012)  
**Guide:** Prof. Gangadhara Rao, Associate Professor, SIT Mangaluru  
**Duration:** 5 June – 8 July 2020 (≈ 1 month)

> **Provenance & Ethics:** This repository transparently reconstructs my BE final-year project. Content, steps and figures are derived from my original VTU/SIT report; some artefacts are recreated for portfolio clarity. No confidential data is included. :contentReference[oaicite:0]{index=0}
Commit message:

---

## 📖 Project Overview

A compact, low-cost **paper recycling machine** that integrates **pulping → forming → press rolling → drying** into a single bench-scale line. It’s designed for **schools, colleges, offices, and small units** where a full-scale mill isn’t viable, prioritising **safety, footprint, and ease of operation**.

**Why this matters**
- Diverts paper waste from bins; demonstrates **closed-loop recycling** on-site.
- Converts mixed office waste into **usable A5/A4 craft sheets** for teaching or prototyping.
- Shows practical integration of **mechanical design, fluid handling, heat transfer, and controls**.

**Scope & objectives**
- Build an integrated prototype with **continuous conveyor forming** and **heated drying**.
- Achieve **stable sheet formation**, reduce moisture via **press rolling**, and **dry to handle** state.
- Emphasise **operator safety** (guards, e-stop, thermal caution) and **simple maintenance** (belt tensioning, cleaning SOP).

**Out of scope**
- Industrial-grade calendaring/sizing, high-speed web control, or commercial grammage certification (the unit is for **demonstration and training**).

---

## ⚙️ Process Flow

1. **Pulping** → Shredded waste paper + water in a **hydropulper** to create slurry (target consistency ~2–3%).  
2. **Forming** → Slurry is deposited onto a **moving felt conveyor**; water drains by gravity/mesh to form a wet mat.  
3. **Press Rolling** → **Paired rollers** squeeze the web to expel free water and improve fibre bonding.  
4. **Drying** → **Heated cylinder** with assisted airflow dries the sheet to a handleable moisture level.

```mermaid
%%{init: {
  "theme":"base",
  "themeVariables": { "fontSize":"18px", "fontFamily":"Inter, Arial, sans-serif" },
  "flowchart": { "useMaxWidth": true, "nodeSpacing": 70, "rankSpacing": 80, "padding": 16 }
}}%%
flowchart TB
  A["Waste Paper\nShredder Bin"] --> B["Hydropulper\n(Water + Agitation)"]
  B --> C["Slurry Tank\nFlow Control"]
  C --> D["Forming Section\nFelt Conveyor + Mesh"]
  D --> E["Press Rolling\nPaired Rollers"]
  E --> F["Drying Section\nHeated Cylinder + Airflow"]
  F --> G["Take-up\nSheet Cutter"]

  subgraph Safety_and_Control ["Safety and Control"]
    H["E-Stop and Guards"]
    I["Motor / Heater Controls"]
  end

  H -. monitors .- D
  H -. monitors .- E
  H -. monitors .- F
  I -. regulates .- B
  I -. regulates .- F
```

<details>
  <summary>PNG fallback for printing / mobile</summary>

  ![Process Flow — Paper Recycling Machine](images/process-flow.png)
</details>
---

## 🔩 Major Components

| Subsystem | Key parts & specs | Purpose | Notes |
|---|---|---|---|
| **Feed & Pulping** | Hopper; **Hydropulper** vessel; Agitator/impeller | Convert shredded waste paper to slurry at ~2–3% consistency | Vessel & impeller sized for stable vortex without air entrainment |
| **Prime mover & Drive** | **AC motor 1 HP, 3-phase**; **Gearbox 42:1**; Pulley–belt | Provide low-speed, high-torque drive for rollers/conveyor | Guarded belts; align for minimal run-out |
| **Frame & Supports** | MS frame; housings; bearings | Structural support and alignment | Slotted holes for belt tensioning & roller nip adjustment |
| **Forming** | Felt conveyor; mesh support; feed tray | Form initial wet sheet by drainage on moving felt | Felt tension & cleaning SOP in docs |
| **Pressing** | **Press rollers** (paired) with bearings | Remove free water; improve bonding | Nip guard; drip tray; adjustable gap |
| **Drying** | **Heated cylinder** + assisted airflow | Reduce residual moisture to handleable level | Mark hot zones; thermostat & thermal cut-out |
| **Pneumatics** | **Pneumatic cylinder**; **compressor**; **solenoid valve** | Apply repeatable nip/pressure and small actuations | Pressure regulator with gauge; LOTO instructions |
| **Controls & Safety** | Basic control panel; motor starter; emergency stop; guards | Safe operation and quick isolation | E-stop reachable; IP-rated enclosures |

> Detailed parts and costs live in **`docs/bom_costs.csv`**. Procedures in **`docs/sop_operations.md`**; hazards & mitigations in **`docs/safety-and-risks.md`**.

---

## 📐 Design Data & Calculations

### Hydropulper (cylindrical vessel)

**Given (from report draft):** wall thickness `t = 0.022 cm`, radius `r = 0.95 cm`, height `h = 50 cm`, volume `V = 62,930 cm³ (≈ 62.9 L)`.

**Sanity-check:** For a right cylinder, \( V = \pi r^2 h \).

- If `h = 50 cm` and `V = 62,930 cm³`, then  
  \( r = \sqrt{V / (\pi h)} ≈ \sqrt{62,930 / (3.1416 × 50)} ≈ 20.0 cm \).

> ⚠️ This shows the stated **`r = 0.95 cm`** is a unit/typo error.  
> To match your volume and height, use **`r ≈ 20.0 cm` (diameter ≈ 40 cm)**.

#### Finalised hydropulper parameters (used for calcs)

| Parameter | Symbol | Value | Notes |
|---|:---:|:---:|---|
| Wall thickness | `t` | 0.022 cm (0.22 mm) | From vessel spec |
| **Radius (corrected)** | `r` | **20.0 cm** | Matches `V` and `h` |
| Height | `h` | 50 cm | Cylindrical shell height |
| **Volume** | `V` | **62,930 cm³ (≈ 62.9 L)** | \( \pi r^2 h \) |

**Batch sizing & consistency (rule-of-thumb):**
- At **2.5% consistency**, paper solids per batch ≈ `0.025 × 62.9 L ≈ 1.57 kg` wet-basis equivalent.
- Useful for planning **press load** and **dryer time** targets downstream.

> If you prefer to keep the originally printed radius, adjust the height to keep the same volume, or update the volume to match the printed dimensions. Keeping **volume** fixed is most practical because downstream timings were likely derived from it.

---

### Conveyor Felt

| Attribute | Value | Notes |
|---:|---|---|
| **Length** | 3.9–4.0 m | Provides drainage **dwell length** before the press nip. |
| **Width** | 13 in (≈ **330 mm**) | Matches target sheet width and roller span. |
| **Material** | Nylon / PVC felt (porous) | Promotes drainage; compatible with wet end chemistry. |
| **Thickness** | 2–4 mm (typ.) | Stiff enough to track; compliant enough for nip. |
| **Speed (line)** | **v** = 0.2–0.5 m/s (demo mode) | Tune to balance drainage vs throughput. |
| **Tension** | 150–300 N total (bench) | Set to avoid slip; check bearing load. |
| **Tracking** | Crowned roller or edge guides | Prevents walk-off; add alignment marks. |
| **Cleaning** | Squeegee + low-pressure spray | Reduces fibre carry-over and blinding. |

**Useful relations**
- **Drainage dwell time:** \( t_{\text{dwell}} = \dfrac{L_{\text{felt}}}{v} \).  
  *Example:* \( L=4.0\,\text{m},\ v=0.3\,\text{m·s}^{-1} \Rightarrow t \approx 13.3\,\text{s} \).
- **Felt speed = line speed:** keep drive ratios 1:1 (no shear).

> See **docs/sop_operations.md** for belt tensioning and tracking, and **docs/safety-and-risks.md** for wet-floor and rotating-machinery hazards.

---

### Dryer Cylinder

| Parameter | Symbol | Value | Notes |
|---|:---:|:---:|---|
| **Radius** | \( r \) | **7 cm** | Bench-scale heated drum. |
| **Circumference** | \( C = 2\pi r \) | **≈ 43.98 cm** | Using \( \pi \approx 3.1416 \). |
| **Heated length** | \( L \) | **50 cm** | Effective contact width. |
| **Wrap angle** | \( \theta \) | 120–180° (typ.) | With idler to increase dwell. |
| **Surface temperature** | \( T_s \) | 80–110 °C (demo) | Adjust for paper grammage & safety. |

**Kinematics**
- **Surface speed:** \( v_s = \omega r \) → **match** to conveyor line speed \( v \) (no slip).
- **Thermal dwell (on drum):** \( t_{\text{drum}} \approx \dfrac{\theta\,r}{v} \) (θ in radians).  
  *Example:* \( \theta = \pi \), \( r=0.07\,\text{m} \), \( v=0.3\,\text{m·s}^{-1} \Rightarrow t \approx 0.73\,\text{s} \).

**Heat-of-drying (rule-of-thumb placeholders)**
- **Load to heat web:** \( \dot Q_{\text{sens}} \approx \dot m_{\text{web}} c_p \Delta T \).  
- **Load to evaporate water:** \( \dot Q_{\text{lat}} \approx \dot m_{\text{water}} h_{fg} \).  
  Use these to choose heater rating; start low and step up under guarded conditions.

**Safety & controls**
- Guard hot surfaces; mark **HOT** zones.  
- Fit thermostat + thermal cut-out; verify earth/insulation.  
- Use a **nip guard** at the drum/idler contact.

> Add a photo or sketch of the **wrap/idler arrangement** to `images/` and reference it here for clarity.


---

## ⚙️ Drive & Speed Calculations

- **Motor:** 1 HP, AC, 3-phase, **900 rpm**
- **Gearbox:** **42:1** → output ≈ **21.43 rpm**
- **Pulley step-up:** **1:2** on the gearbox output → roller ≈ **42.86 rpm**  
  > (Driver pulley ≈ 2× the driven pulley to double speed.)
- **Dryer circumference:** **C ≈ 2πr = 2π·0.07 m ≈ 0.4399 m**

**Linear web speed**

\[
v \;=\; \text{rpm} \times C
\;=\; 42.86 \times 0.4399\;\text{m·min}^{-1}
\;\approx\; \mathbf{18.85\;m·min^{-1}} \;(\mathbf{0.314\;m·s^{-1}})
\]

> Keep the **drum surface speed** matched to the conveyor to avoid shear/slip.

---

## 🔧 Press Nip Pressure (estimated)

**Definitions**

- **Line load (per unit width):** \(N'\) \([N·m^{-1}]\) — what paper engineers typically quote.
- **Average nip pressure:** \(p\) \([Pa]\) — approx. average across the contact patch.  
- **Geometry:** effective width \(w\), nip contact length \(a\) (in the machine direction).

**From measured/assumed line load**

\[
p \;\approx\; \frac{N'}{a}
\qquad\text{and}\qquad
N \;=\; N' \cdot w,
\]
\[
\text{with area of contact } A \approx w \cdot a \;\Rightarrow\; p \approx \frac{N}{A}.
\]

**Your stated example**  
\(w = 0.33\,\text{m},\; a = 5\,\text{mm} = 0.005\,\text{m},\; N' \approx 16{,}500\,\text{N·m}^{-1}\)

- Total line force: \(N = N' \cdot w \approx 16{,}500 \times 0.33 \approx 5{,}445\,\text{N}\)
- Contact area: \(A = w \cdot a \approx 0.33 \times 0.005 = 0.00165\,\text{m}^2\)
- **Estimated pressure:**  
  \[
  p \approx \frac{5{,}445}{0.00165} \approx \mathbf{3.3\;MPa}
  \]
> Your previous 9.9 MPa appears to be a 3× arithmetic slip. For the given \(N'\) and \(a\), the consistent estimate is **≈ 3.3 MPa**.

#### Moisture after Press (bench-scale heuristics)

Let:
- N′ = line load (N·m⁻¹)
- a  = nip contact length (m)
- v  = line speed (m·s⁻¹)
- M_in = inlet moisture (kg water / kg dry fibre)
- M_out ≈ moisture after press

1) Dwell index (dimensionless):  DI = a / v
2) Pressure index (kPa):         PI ≈ (N′ / a) / 1000     (since p ≈ N′/a)

Rule-of-thumb bands (felt in good condition, thin web):
- Light press:    PI 1–2 MPa,  DI ~0.01–0.02 s → M_out ≈ 1.6–2.0
- Medium press:   PI 2–3 MPa,  DI ~0.02–0.04 s → M_out ≈ 1.2–1.6
- Firm press:     PI 3–4 MPa,  DI ~0.04–0.07 s → M_out ≈ 0.9–1.2

Use these as **starting points** only; verify by weighing test strips before/after the press.


#### Press Tuning Checklist

- ✔️ **Match speeds**: drum and felt surface speeds equal (no visible shear).
- ✔️ **Set N′**: start with target line load; verify regulator pressure and gauge.
- ✔️ **Check nip contact**: uniform stripe across 330 mm width (carbon paper test).
- ✔️ **Adjust DI**: increase contact length a (softer covers) or reduce v for more dewatering.
- ✔️ **Felt condition**: clean, unworn; squeegee and low-pressure spray enabled.
- ✔️ **Measure moisture**: weigh 5 samples pre/post press (grams), track mean & σ.
- ✔️ **Thermal follow-on**: if dryer struggles, revisit press settings first.
- ⚠️ **Safety**: guards in place, e-stop tested, LOTO before adjustments.


---


### Press Line Load — quick reference
At 5 bar with two cylinders across a 330 mm width, an ~**83 mm bore** pair gives
**N′ ≈ 16,500 N·m⁻¹** and an average nip pressure **p ≈ N′/a** (e.g., ≈3.3 MPa for a = 5 mm).

→ Full derivation, cylinder sizing table, and safety notes: see **docs/press-calcs.md**.


---

### Cost Analysis

| Equipment             | Material     | Cost   |
|-----------------------|--------------|-------:|
| Mixing Grinder        | Stainless Steel | ₹ 3,000 |
| AC Motor (1 HP)       | Aluminium    | ₹ 3,500 |
| Conveyor Belt         | PVC coated   | ₹ 800  |
| Pulley Belts (×2)     | Rubber (B)   | ₹ 200  |
| Conveyor Rollers (×2) | Mild Steel   | ₹ 700  |
| Press Rollers (×2)    | Mild Steel   | ₹ 500  |
| Bearings (×2)         | Mild Steel   | ₹ 1,000|
| Nuts & Bolts          | Mild Steel   | ₹ 150  |
| Frame                 | Mild Steel   | ₹ 1,900|
| **Total**             |              | **₹ 11,700** |

---

## 📅 Timeline (One Month)

- **Week 1 (June 5–11):** Problem definition, requirements, initial CAD sketches  
- **Week 2 (June 12–18):** Frame design, roller/bearing selection, conveyor research  
- **Week 3 (June 19–25):** Fabrication (frame welding, roller alignment), dry-run test  
- **Week 4 (June 26–July 2):** Process tuning, test sheets, draft report  
- **Week 5 (July 3–8):** Final report writing, images/diagrams, polished README  

---

## ⚠️ Safety Notes

- Guard all rotating parts (rollers, belts, pulleys)  
- Use PPE around hot surfaces and chemicals  
- Depressurize pneumatic systems before maintenance  

---
## ✅ Advantages

- Compact design suitable for small-scale use  
- Low-cost construction with readily available materials  
- Energy-efficient operation (1 HP motor with gearbox)  
- Easy to maintain and operate  
- Reduces environmental waste by recycling used paper  
- Quick turnaround — sheets produced in minutes  

---

## ⚠️ Disadvantages

- Limited production capacity (small batch size only)  
- Not suitable for industrial-scale recycling  
- Requires manual feeding and supervision  
- Drying section efficiency depends on local conditions (temperature, humidity)  
- Paper quality may not match commercial-grade standards  

---

## 🔭 Scope for Future Work

- Automating slurry feeding and sheet cutting  
- Increasing production capacity with wider conveyor and larger rollers  
- Integration of temperature-controlled dryer for consistent sheet quality  
- Addition of sensors and PLC for semi-automatic operation  
- Developing portable/mobile versions for schools and community centers  
- Using renewable energy (solar power) to improve sustainability  


## ✍️ Author’s Note

I, **Akash P Raj**, carried out this project work as part of my **final year Bachelor of Engineering in Mechanical Engineering** at **Srinivas Institute of Technology, Mangaluru**, under the guidance of **Prof. Gangadhara Rao**.  

This project was completed within **one month (June–July 2020)**, covering design, fabrication, testing, and documentation.  

I sincerely thank my guide, coordinators, faculty, and my project teammates for their contributions and encouragement.

---

## 📚 References

1. Ajay Takur & Swash Monore (2017). *Design and fabrication of compact paper recycling machine*. Paper Technology, 139:250–261.  
2. Ajith Ghosh (2011). *Fundamentals of paper drying theory and applications from industrial perspective*. Paper Recycling Technology, 178:65–71.  
3. Jiang C. & Ma J. (2000). *Deinking of waste paper flotation*. Enzymatic Deinking Technologies, 1–2.  
4. Final Report: *Design and Fabrication of Paper Recycling Machine*, Srinivas Institute of Technology, 2020.  


