# Eco Paper Recycler — Final Year Project

**Author:** Akash P Raj  
**Duration:** June 5 – July 8, 2020 (1 Month)  

---

## 📖 Project Overview
This is my **final year project**: the design and fabrication of a **compact paper recycling machine**.  
The machine integrates **pulping, forming, press rolling, and drying** into one unit.  
It is aimed at schools, colleges, offices, and small industries where a large-scale plant is not feasible.

---

## 🛠 Workflow Diagram

![Workflow](assets/page1_img1.jpeg)

---

## 🏗 Machine Design (CAD Views)

### Front View
![Front View](assets/page13_img1.jpeg)

### Isometric View
![Isometric View](assets/page15_img1.jpeg)

### Top View
![Top View](assets/page16_img1.jpeg)

### Side View
![Side View](assets/page16_img2.jpeg)

---

## ⚙️ Process Flow

1. **Pulping** — Shredded waste paper is mixed with water in the hydropulper.  
2. **Forming** — Slurry drains on a felt conveyor to form a wet sheet.  
3. **Press Rolling** — Rollers squeeze out water and compact the sheet.  
4. **Drying** — Heated cylinder and airflow dry the paper.

---

## 🔩 Major Components

- Hopper  
- Pulley & belt drive  
- AC motor (1 HP, 3-phase) with gearbox (42:1 reduction)  
- MS frame with bearings  
- Pneumatic cylinder & compressor  
- Felt conveyor with idler and press rollers  
- Solenoid valve + basic control unit  

---

## 📐 Design Data & Calculations

### Hydropulper (Design Data)

| Parameter            | Symbol | Value  | Notes                     |
|---------------------|:------:|:------:|---------------------------|
| Wall thickness      |  t     | 0.022 cm | As per vessel spec        |
| Radius              |  r     | 0.95 cm  | Representative from report|
| Total height        |  h     | 50 cm    | Open-top cylindrical tank |
| Impeller/agitator   |  —     | —        | For slurry circulation    |

> Purpose: blend shredded waste paper + water (+ additives) into a uniform fiber slurry.

---

### Conveyor Felt

| Attribute | Value         | Notes                                                                 |
|----------:|---------------|-----------------------------------------------------------------------|
| Length    | 3.9–4.0 m     | Provides travel/dwell for drainage                                   |
| Width     | 13 in (~330 mm)| Sized to sheet width and roller span                                 |
| Material  | Nylon/PVC      | Porous, provides void volume and supports water removal               |

**Design roles**
1. Convey sheet through forming → pressing → drying  
2. Porous medium for effective water removal  
3. Textured cushion to pass moist sheet without crushing/marking

---

### Dryer Cylinder (Geometry)

| Parameter          | Symbol | Value   |
|-------------------|:------:|:-------:|
| Radius            |  r     | 7 cm    |
| Circumference     |  C     | 43.99 cm (C = 2πr) |

> Use circumference with rpm to estimate web (felt) linear speed and drying dwell distance.

---

### Drive & Speed Calculations

- Motor: 1 HP, AC, 3-phase, **900 rpm**  
- Gearbox: **42:1** reduction → output rpm = 900 / 42 = **21.43 rpm**  
- Belt & pulleys: speed **increase 1:2** → roller rpm ≈ 21.43 × 2 = **42.86 rpm**  
- Dryer cylinder circumference **C = 43.99 cm**

**Linear web speed**  
v = rpm × C = 42.86 × 43.99 cm/min = **≈ 1,885 cm/min = 18.85 m/min**

| Stage          | Value                  |
|----------------|------------------------|
| Motor speed    | 900 rpm                |
| Gearbox output | 21.43 rpm              |
| Roller speed   | 42.86 rpm              |
| Web speed      | ~18.85 m/min           |

> Adjust if you change pulley diameters/ratios or cylinder size.

---

### Press Nip (Placeholder — update with test values)

| Parameter                         | Symbol | Value      | Notes                                 |
|----------------------------------|:------:|:----------:|---------------------------------------|
| Pneumatic line pressure          |   P    | — bar      | From regulator gauge                  |
| Effective press width            |   w    | — m        | Width of sheet contact                |
| Nip contact length (approx.)     |   a    | — mm       | From roller hardness/deflection       |
| Line load (per unit width)       |   N/w  | — N/m      | From cylinder force & geometry        |
| Estimated nip pressure           |   p    | — kPa      | p ≈ (N / (w·a))                       |

> Record actual readings during tuning to replace placeholders.

---

### Cost Analysis (Indicative)

| Equipment             | Material     | Cost   |
|-----------------------|--------------|-------:|
| Conveyor belt         | PVC coated   |  ₹ 800 |
| Pulley belts (×2)     | Rubber (B)   |  ₹ 200 |
| Conveyor rollers (×2) | Mild steel   |  ₹ 700 |
| Bearings (×2)         | Mild steel   | ₹ 1,000|
| AC Motor              | Aluminium    | ₹ 3,500|
| Frame                 | Mild steel   | ₹ 1,900|
| Misc. (bolts, etc.)   | —            | ₹ 1,600|
| **Total**             |              | **₹ 11,700** |

---

## 🧪 Prototype & Fabrication

![Prototype](assets/page18_img1.jpeg)

---

## 📅 Timeline (One Month)

- **Week 1 (June 5–11):** Problem definition, requirements, initial CAD sketches  
- **Week 2 (June 12–18):** Frame design, roller/bearing selection, conveyor research  
- **Week 3 (June 19–25):** Fabrication (frame welding, roller alignment), dry-run test  
- **Week 4 (June 26–July 2):** Process tuning, test sheets, draft report  
- **Week 5 (July 3–8):** Final report writing, images/diagrams, polished README  

---

## 🌱 Applications

- Schools and colleges  
- Offices and small industries  
- Laboratory demonstrations  
- Research and awareness on recycling  

---

## ⚠️ Safety Notes

- Guard all rotating parts (rollers, belts, pulleys)  
- Use PPE around hot surfaces and chemicals  
- Depressurize pneumatic systems before maintenance  

---

## 📂 Repository Structure

