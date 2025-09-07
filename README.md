# Eco Paper Recycler — Final Year Project

**Author:** Akash P Raj (USN: 4SN16ME012)  
**Guide:** Prof. Gangadhara Rao, Associate Professor, SIT Mangalore  
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

### Hydropulper

| Parameter            | Symbol | Value   | Notes                     |
|---------------------|:------:|:-------:|---------------------------|
| Wall thickness      |  t     | 0.022 cm | As per vessel spec        |
| Radius              |  r     | 0.95 cm  | From report data          |
| Total height        |  h     | 50 cm    | Cylindrical vessel height |
| Impeller/agitator   |  —     | Yes      | Circulates slurry         |

**Volume calculation:**  
Total Volume, Vr = 62,930 cm³ (≈ 62.9 L)

---

### Conveyor Felt

| Attribute | Value          | Notes                                                                 |
|----------:|----------------|-----------------------------------------------------------------------|
| Length    | 3.9–4.0 m      | Provides travel/dwell for drainage                                   |
| Width     | 13 in (~330 mm)| Matches sheet width and roller span                                  |
| Material  | Nylon/PVC      | Porous medium for effective water removal                           |

---

### Dryer Cylinder

| Parameter          | Symbol | Value   |
|-------------------|:------:|:-------:|
| Radius            |  r     | 7 cm    |
| Circumference     |  C     | 43.99 cm |
| Length (heated)   |   L    | 50 cm   |

---

### Drive & Speed Calculations

- Motor: 1 HP, AC, 3-phase, **900 rpm**  
- Gearbox: **42:1** → output ≈ 21.43 rpm  
- Pulley ratio: **1:2** → roller ≈ 42.86 rpm  
- Dryer circumference: **43.99 cm**

**Linear web speed**  
v = rpm × C = 42.86 × 43.99 cm/min = **18.85 m/min**

---

### Press Nip Pressure (Estimated)

| Parameter                         | Symbol | Value        |
|----------------------------------|:------:|:------------:|
| Pneumatic line pressure          |   P    | 5 bar        |
| Effective press width            |   w    | 0.33 m       |
| Nip contact length (approx.)     |   a    | 5 mm         |
| Line load (per unit width)       |   N/w  | ≈ 16,500 N/m |
| Estimated nip pressure           |   p    | ≈ 9.9 MPa    |

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

## ⚠️ Safety Notes

- Guard all rotating parts (rollers, belts, pulleys)  
- Use PPE around hot surfaces and chemicals  
- Depressurize pneumatic systems before maintenance  

---

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


