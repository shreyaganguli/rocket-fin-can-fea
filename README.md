# Rocket Fin Can — SolidWorks FEA Structural Analysis

**Tools:** SolidWorks 2025 · SolidWorks Simulation (FEA) · Python  
**Skills:** CAD Modeling · Finite Element Analysis · Structural Optimization · Design Iteration

---

## Overview

Designed and structurally analyzed a 54mm rocket fin can in SolidWorks, simulating aerodynamic and thrust loads using static FEA. The goal was to identify stress concentrations, validate the design against material failure criteria, and iterate geometry to improve the safety factor while minimizing mass.

This project was built as part of a self-directed summer engineering portfolio in preparation for applying to competitive university engineering organizations (TREL, LHR) at UT Austin.

---

## Design Specifications

| Parameter | Value |
|-----------|-------|
| Body tube outer diameter | 54 mm |
| Wall thickness | 3 mm |
| Tube length | 100 mm |
| Number of fins | 4 (90° spacing) |
| Fin root chord | 80 mm |
| Fin tip chord | 40 mm |
| Fin span | 50 mm |
| Fin thickness | 3 mm |
| Root fillet radius | 2 mm (baseline) |
| Material | Nylon 6/10 (Yield Strength: 60 MPa) |

---

## Loading Conditions

| Load | Value | Justification |
|------|-------|---------------|
| Aerodynamic pressure (fin faces) | 6,125 Pa | Dynamic pressure at 100 m/s (q = ½ρv²) |
| Thrust load (axial) | 20 N | Typical Estes model rocket motor |
| Fixture | Fixed — top face of tube | Simulates connection to rocket body above |

---

## Study 1 — Baseline Design (3mm fillet, 3mm fin thickness)

### Results

| Metric | Value |
|--------|-------|
| Max Von Mises Stress | 0.33 MPa |
| Safety Factor | 180 |
| Max Displacement | 0.00725 mm |
| Mass | 21.11 g |

### Stress Distribution
![Study 1 Stress Plot](results/study1_stress.png)

### Displacement
![Study 1 Displacement](results/study1_displacement.png)

**Key finding:** Baseline design shows a safety factor of 180 under flight loads — the structure is significantly overbuilt relative to aerodynamic and thrust loads on a model rocket. Iterations will focus on mass reduction while maintaining FOS above 3.

---

## Design Iteration Results

| Metric | Study 1 — Baseline (2mm fillet, 25mm span) | Study 2 — Larger fillet (5mm fillet, 25mm span) | Study 3 — Reduced span (5mm fillet, 18mm span) |
|--------|------|------|------|
| Max Von Mises Stress | 0.33 MPa | 0.28 MPa | 0.29 MPa |
| Min Factor of Safety | 180 | 210 | 210 |
| Max Displacement | 0.00725 mm | 0.00682 mm | 0.00710 mm |
| Mass | 21.11 g | 22.02 g | 19.20 g |

**Outcome:** Increasing the fin root fillet from 2mm to 5mm reduced max stress by 15% and raised FOS from 180 to 210. Subsequently reducing the fin span by 28% (25mm → 18mm) saved 2.82g of mass while maintaining the same FOS — resulting in a lighter, stronger design than the baseline.

---

## Repository Structure

```
rocket-fin-can-fea/
│
├── CAD/
│   ├── fin_can_body.SLDPRT        # SolidWorks part file
│   └── fin_can_assembly.SLDASM   # Full assembly (optional)
│
├── results/
│   ├── study1_stress.png          # Von Mises stress plot
│   ├── study1_displacement.png    # Displacement plot
│   └── study1_safety_factor.png  # Factor of safety plot
│
├── docs/
│   └── analysis_report.pdf       # Full simulation report (export from SW)
│
└── README.md
```

---

## What I Learned

- How to set up a complete static FEA study in SolidWorks Simulation including fixtures, pressure loads, and axial force loads
- How to apply aerodynamic pressure loads derived from fluid dynamics (dynamic pressure equation)
- How stress concentrations form at geometric discontinuities and how fillet geometry affects them
- How to interpret Von Mises stress plots, displacement results, and factor of safety plots
- The engineering tradeoff between structural performance and mass

---

## Next Steps

- [x] Complete design iterations (Study 2 and Study 3)
- [ ] Add CFD analysis using SolidWorks Flow Simulation to get actual aerodynamic pressure distribution rather than hand-calculated estimate
- [ ] Feed CFD pressure results into FEA as loads (coupled simulation workflow)
- [ ] 3D print optimized design and physically validate
- [ ] Extend to a curved body panel design relevant to Formula SAE bodywork

---

## About

Rising sophomore in Mechanical Engineering at The University of Texas at Austin. Interested in aerospace structures, biomechanical devices, and computational simulation. Currently conducting undergraduate research in Dr. Richard Neptune's Neuromuscular Biomechanics Lab.

[LinkedIn](https://linkedin.com/in/YOUR-LINK) · [Email](mailto:shreyaganguli000@gmail.com)
