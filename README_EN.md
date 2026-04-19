# ⚙ ClampForce v1.0

A browser-based engineering calculation tool for verifying bolted flange connections in pressure vessels and piping systems against **VDI 2230** and **EN 1591** standards.

> No installation. No internet connection required. Single `.html` file — open and run.

---

## 🚀 Usage

Download `ClampForce v1.0.html` and open it in any modern browser. That's it.

---

## 🔍 What It Checks

| Check | Criterion |
|---|---|
| **[1] Bolt Stress** | σ = F_bolt / A_s ≤ proof / SF |
| **[2] Joint Separation** | n × F_pre > SF × F_p |
| **[3] Gasket Seating** | p_gasket ≥ p_min (optional) |
| **[4] Bolt Spacing** | Pitch ≥ factor × d (DESIGN mode) |

---

## ⚡ Two Operating Modes

**CHECK** — Verify an existing design. You provide the bolt count; the tool runs all checks against your inputs.

**DESIGN** — Size a new joint. Enter the bolt circle diameter (BCD) and the tool calculates the minimum number of bolts required.

---

## 📐 Input Parameters

### Pressure & Geometry
- Internal pressure (MPa), gasket inner/outer diameter (mm)
- CHECK: bolt count n — DESIGN: BCD (mm)

### Bolt Properties
- Size: M6 – M20 | Grade: 4.6 / 5.8 / 8.8 / 10.9 / 12.9
- Tightening factor k and preload loss factor

### Safety Factors
- SF_separation (default 1.5), SF_stress (default 1.2)

### Optional Modules (Toggle)
| Module | Dependency | Additional Inputs |
|---|---|---|
| VDI φ Stiffness | — | E_bolt, E_joint, L_eff |
| Thermal Loading | VDI φ must be active | ΔT, L_joint, α_bolt, α_joint |
| Gasket Seating | — | Min. gasket stress (MPa) |

---

## 📊 Output

Once the analysis runs, the right panel displays:

- ✅ / ❌ Overall acceptance status
- 6 metric cards: A_eff, F_p, F_pre, F_bolt, stiffness ratio, bolt count
- OK / NOK badge with detailed values for each check
- Visual stress utilisation bar for bolt stress check (green < 65% · amber 65–85% · red > 85%)

---

## 🔩 Built-in Database

| Size | A_s (mm²) | | Grade | Proof (MPa) | Re (MPa) | Rm (MPa) |
|---|---|---|---|---|---|---|
| M6 | 20.1 | | 4.6 | 225 | 240 | 400 |
| M8 | 36.6 | | 5.8 | 380 | 400 | 500 |
| M10 | 58.0 | | 8.8 | 580 | 640 | 800 |
| M12 | 84.3 | | 10.9 | 830 | 900 | 1000 |
| M14 | 115.0 | | 12.9 | 970 | 1080 | 1200 |
| M16 | 157.0 | | | | | |
| M18 | 192.0 | | | | | |
| M20 | 245.0 | | | | | |

---

## 📋 User Manual

For full parameter descriptions, worked examples, and formula derivations, refer to `ClampForce v1.0 User Manual.pdf`.

---

## Validation Report

ClampForce v1.0 has been verified against hand-calculated analytical reference values per VDI 2230 and EN 1591-1:2013 standards. Three independent scenarios were tested; all results showed full agreement.

| # | Scenario | Mode | Feature | Result | Match |
|---|---|---|---|---|---|
| 1 | Basic Flange | CHECK | Fixed C, n=8 | ACCEPTABLE | ✓ FULL |
| 2 | Steel/Al. Flange | CHECK | VDI φ + Thermal | NOT ACCEPTABLE | ✓ FULL |
| 3 | High-Pressure Flange | DESIGN | Sealing + Spacing | ACCEPTABLE, n=4 | ✓ FULL |

> The NOT ACCEPTABLE result in Scenario 2 is intentional: it demonstrates how thermally induced preload increase can critically compromise joint integrity. For the full report, refer to `ClampForce v1.0 Validation Report.pdf`.

---

## ⚠ Limitations

- Supported bolt range: M6–M20, cylindrical symmetry assumed throughout.
- Thermal analysis requires the VDI φ stiffness module to be active.
- The stiffness model follows the simplified VDI 2230 approach; for non-standard flange geometries, FEM is recommended.

---

*VDI 2230 · EN 1591 · v1.0*
