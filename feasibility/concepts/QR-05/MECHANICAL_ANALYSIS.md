# QR-05 — Mechanical Analysis

| Property | Value |
|---|---|
| Document ID | KMECH-MECH-QR-05 |
| Repository | `KritvaOS/kritva-mechanical` |
| Document Type | Mechanical Feasibility Analysis |
| Status | PROPOSED |
| Owner | Dinesh |
| Assigned Intern | INTERN-02 |
| Version | 0.2.0 |
| Last Updated | 2026-11-25 |
| Authority | Preliminary paper analysis; subject to owner review |
| Related Documents | `README.md`, `REQUIREMENTS.md`, `ARCHITECTURE.md`, `ACTUATOR_ANALYSIS.md`, `MASS_BUDGET.md` |

All results are **ESTIMATES** from paper calculations (evidence C) on intern assumptions. Nothing is approved. Printed values are CONCEPT_TARGET.

## 1. Analysis Scope

Concept ID/name: QR-05 — Modular Quadruped (four interchangeable 2-DOF or 3-DOF leg modules on a rigid body)

Analysis objective: Check on paper whether the QR-05 arrangement is plausible: the modular interface, load paths and stiffness, joint loading, leg workspace and stability for both module types, mass, serviceability and safety, and identify what must be settled first.

Evidence basis:
- Sourced reference: `README.md` v0.3.0 (artwork, CONCEPT_TARGET, L0).
- Calculated (C): CALC-QR05-03 (to be filed), using CALC-QR05-01 (`ACTUATOR_ANALYSIS.md`) and CALC-QR05-02 (`MASS_BUDGET.md`).
- ESTIMATE: every assumption below.

### 1.1 Assumptions used here

| ID | Assumption |
|---|---|
| S1 | Leg geometry per `ACTUATOR_ANALYSIS.md` A3: thigh 160 mm, shank 180 mm, knee back, hip height 260 mm; hips at ±130 mm × ±150 mm |
| S2 | Interface bolt pattern 50 mm × 50 mm (4 × M5) with 2 dowels Ø5 mm; spacing not printed |
| S3 | Feet at ±250 mm × ±240 mm; the abduction axis (or the interface) sits at the body side, 120 mm from the foot |
| S4 | Thigh and shank as aluminium tube, 24 mm outer diameter, 2 mm wall, E = 69 GPa (illustrative) |
| S5 | Flat, rigid, dry floor; static analysis |
| S6 | Foot pad friction coefficient 0.5 (assumed) |
| S7 | Payload mounted on top at about 400 mm |
| S8 | Moving mass 11.35 kg (12 DOF) or 9.45 kg (8 DOF), including 1.0 kg payload |

## 2. Structure and Load Paths

- **Main structure and support configuration:** Rigid body chassis (1 mm aluminium shell assumed), four module interfaces, four leg modules, foot pads on the ground.
- **Representative load cases:** LC1 four-foot stand. LC2 two-foot support (bounding case, 55.7 N per foot at 12 DOF). LC3 three-foot crawl stance. LC4 sit-to-stand. LC5 touchdown (2× allowance). Not analysed: module swap, falls, jumping, rough terrain.
- **Load paths:** foot pad → shank → knee module → thigh → hip pitch module → (abduction module) → module interface (4 × M5 and 2 dowels) → body chassis.
- **Structural concerns:**
  1. *Module interface.* Per foot force of 55.7 N at a 120 mm lateral arm gives about 6.7 N·m about the longitudinal axis, plus about 3.3 N·m about the lateral axis with a 60 mm stride and 56 N shear. On a 50 mm pattern the bolt tension is about M ÷ d = 6.7 ÷ 0.05 = 134 N per side, about 67 N per bolt, and the dowel shear is about 28 N each. These are tiny against an M5 bolt (several kN), so strength is not the issue: stiffness, fit tolerance, fretting, thread pull-out in the chassis and the connector are.
  2. *Interface compliance.* Joint angle error from interface slack scales with the leg length of about 340 mm; for example 0.1 mm of slack at the bolt pattern gives about 0.7 mm at the foot (0.1 ÷ 50 × 340). Dowel fit and clamp preload are not defined.
  3. *Body torsion.* The chassis carries four hip reactions; torsional stiffness is not checked.
  4. *Link bending.* The shank carries up to the knee torque of 7.5 N·m near the knee: σ = M·c ÷ I = 7,520 N·mm × 12 mm ÷ 8,431 mm⁴ ≈ 10.7 MPa (about 21 MPa with the 2× allowance), comfortable for aluminium; margin for 3D-printed links is not known.
- **Stiffness and deflection considerations:**
  - Shank bending: about 41.8 N perpendicular load at 180 mm gives δ ≈ 0.14 mm.
  - Joint compliance, interface slack, pad compliance and body torsion will dominate; data TBD.
  - 3-DOF modules carry the abduction axis outboard, adding a long moment arm; its compliance is not assessed.

## 3. Joint and Mechanism Analysis

Torques are per joint, worst case (12 DOF), from CALC-QR05-01; all are estimates.

| Joint / mechanism | Load case | Required motion | Calculation reference | Result |
|---|---|---|---|---|
| Hip abduction (3-DOF) | LC2, 120 mm lateral arm | Abduction, range TBD | CALC-QR05-01 §3 | ≈ 6.7 N·m static, ≈ 13.4 N·m with 2× allowance; ≈ 3.3 N·m standing |
| Hip pitch | LC2, foot 60 mm from the hip line | Flexion / extension, stride ±60 mm | CALC-QR05-01 §2 | ≈ 3.3 N·m static, ≈ 6.7 N·m with allowance; swing leg ≈ 1.0 N·m |
| Knee | LC2, knee back | Flexion / extension; range TBD | CALC-QR05-01 §1 | ≈ 7.5 N·m static, ≈ 15 N·m with allowance; ≈ 3.0 N·m standing; sit-to-stand ≈ 4.3 N·m |
| Module interface and connector | LC2 | Static plus repeated mating | CALC-QR05-03 §1 | Bolt tension ≈ 67 N each; stiffness and connector life TBD |
| Foot pad, damper, force sensor | Touchdown | Passive | none | Not analysed: TBD |

The elbow reference values are not used.

## 4. Dual-Arm Add-on Analysis

Not applicable. QR-05 has no arms or manipulators.

## 5. Legged Add-on Analysis

- **Leg configuration and joint arrangement:** Four identical leg modules. A 2-DOF module has hip pitch and knee in a vertical plane; a 3-DOF module adds an abduction axis along the body. Link lengths are assumed (S1). Both module types use the same interface (S2).
- **Support polygon and representative support configurations:**
  - Four feet: rectangle about 500 mm (lateral) × 480 mm (fore-aft).
  - Three feet (one leg lifted): a triangle; with the centre of mass at the body centre it lies exactly on the diagonal between the two opposite feet, so the margin is **zero** unless the body is shifted.
- **Ground contact and foot assumptions:** Rubber pad with friction 0.5 (S6) on a flat rigid dry floor. Outdoor ground, the optional damper and the force sensor are not assessed.
- **Static stability considerations:**
  - Standing: with the centre of mass at 240 mm (payload on top), the static tipping angle is about 45° (fore-aft) and 46° (lateral). The friction slip angle (atan 0.5) is about 27°, so foot slip limits slopes.
  - Crawl gait: the diagonal runs 500 mm × 480 mm. Margin = 0.721 × fore-aft shift (2-DOF legs, which cannot shift sideways): a 30 mm margin needs about 42 mm, 20 mm needs about 28 mm. With 3-DOF legs the body can also shift sideways, so the shortest shift for a 30 mm margin is 30 mm perpendicular to the diagonal, about 28% less.
  - Trot (two-foot support) is not statically stable; not assessed.
- **Leg-joint loading and clearance:** See Section 3. Ground clearance under the body is about 135 mm (hip height 260 mm minus half of the 250 mm body height, assumed). Knee and thigh swing clearance against the body and the interface, and foot swing height, are TBD. The abduction joint of a 3-DOF module sweeps the leg outward and needs clearance to the body side and to neighbouring legs, TBD.
- **Locomotion workspace limitations:**
  - Foot workspace per leg: an annulus of about 20 – 340 mm around the hip, limited by joint ranges (TBD); ground reach about 219 mm fore and aft at full extension (singular). Practical stride about ±60 mm (assumed), giving 120 mm per stride.
  - 2-DOF legs: no side-stepping or lateral balance correction; turning needs foot slip (a 60 mm stride difference over a 500 mm track gives only about 7° of yaw per cycle).
  - 3-DOF legs: abduction allows side-steps, turning by stepping and lateral balance correction; range of abduction TBD.
  - Overall size check: feet at ±250 mm give the printed 520 mm width including pads; the 560 mm length printed on the concept sheet is about 60 mm longer than the assumed stance, which would need a longer stride or stance.

## 6. Mass, Serviceability and Safety

- **Preliminary mass breakdown (from `MASS_BUDGET.md`, ESTIMATE):** about 10.4 kg for 12 DOF (actuators 4.6, body 1.5, battery 1.15, legs 1.0, Edge and drivers 0.63, harness 0.52, interfaces 0.48, other 0.35, power board 0.12) and about 8.5 kg for 8 DOF. The printed 4 – 6 kg is at or below the bottom of the estimate range.
- **Service access and maintenance:** The point of the concept is easy swap, but the swap procedure, tool access to the bolts, connector access, battery access (not drawn) and foot pad replacement are not shown. Module swap with a live 24 V connector needs a safe power-down procedure.
- **Pinch/crush and structural hazards:**
  1. Pinch points at hip, knee and abduction joints and at the module interface.
  2. Falls and tipping of a 9 – 11 kg robot.
  3. Collapse on power loss: knee holding about 3 N·m standing; without backdrive resistance or a brake the legs fold.
  4. A connector that loosens or a module that is not fully seated could drop out under load.
  5. Li-ion battery hazards; no battery safety assessment is made in this study.
  6. Heat in the motors holding the standing pose (cooling not drawn).
- **Safeguards and unresolved safety questions:** emergency stop (not shown), interface locking and interlock, torque and speed limits, safe sit-down on power loss, battery protection. None is defined or selected.

## 7. Conclusions and Open Items

- **Findings:**
  1. Worst-case static joint loads are moderate (knee about 7.5 N·m, abduction about 6.7 N·m, hip pitch about 3.3 N·m at 12 DOF), about double with the allowance, and mass and torque feed each other.
  2. The estimated mass (about 10.4 kg at 12 DOF, about 8.5 kg at 8 DOF) is well above the printed 4 – 6 kg.
  3. The interface adds only about 0.32 kg and its bolt loads are small; stiffness, fit and the connector are the real open questions, and the interface is undefined (D6).
  4. 3-DOF modules cost about 1.9 kg more but allow side-stepping, turning by stepping and a shorter body shift (about 30 mm vs about 42 mm) in a crawl.
  5. Standing is stable (tipping about 45°) and friction limits slopes to about 27°.
  6. Link bending is negligible for aluminium; the abduction joint carries a long lateral arm.
- **Limitations:** link lengths, hip height, stance width, interface pattern, friction and component masses are assumptions. No joint ranges, stiffness or impact data. Static or simple dynamic loads only. No finite-element or CAD work (HOLD D-003).
- **Required follow-up calculations:** interface concept with stiffness and connector; gait cycle with torque history for both module types; touchdown impact; stance width trade against abduction torque; battery placement and centre of mass; thermal limits; power-off collapse; swap procedure.
- **Open items and dependencies:** D6; interface definition; baseline module type; link lengths and joint ranges; battery capacity and placement; S/M/L mapping; safety requirements; owner-supplied weight and payload values.

## 8. HOLD D-003

Paper calculations and conceptual analysis only. CAD, final BOM, quotations, procurement, fabrication, assembly and physical testing remain NOT STARTED and require explicit owner decision. This template does not authorize implementation.
