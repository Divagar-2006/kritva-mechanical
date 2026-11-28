# QR-05 — Actuator Analysis

| Property | Value |
|---|---|
| Document ID | KMECH-ACT-QR-05 |
| Repository | `KritvaOS/kritva-mechanical` |
| Document Type | Joint and Actuator Feasibility Analysis |
| Status | PROPOSED |
| Owner | Dinesh |
| Assigned Intern | INTERN-02 |
| Version | 0.2.0 |
| Last Updated | 2026-11-25 |
| Authority | Preliminary paper analysis; subject to owner review |
| Related Documents | `README.md`, `REQUIREMENTS.md`, `ARCHITECTURE.md`, `feasibility/DESIGN_GUIDELINES.md` |

## 1. Scope and Assumptions

- Concept ID: QR-05 (Modular Quadruped)
- Supply direction: 24V DC investigation only
- Motor direction: BLDC/PMSM
- Actuator architecture: S/M/L (no joint mapped yet)
- Joints in scope: hip abduction (3-DOF module only), hip pitch and knee of each leg (symmetric, so one leg is analysed), for both 12-DOF and 8-DOF configurations. Evidence type C; all values are **estimates**, nothing approved.

### 1.1 Inputs from the README (CONCEPT_TARGET)

Target weight 4 – 6 kg (est., 12 DOF); payload 0.5 – 1.0 kg; body 420 × 260 × 250 mm; overall 560 × 520 mm.

### 1.2 Intern assumptions

| ID | Assumption |
|---|---|
| A1 | g = 9.81 m/s² |
| A2 | Moving mass: 12-DOF 11.35 kg (10.35 kg estimate plus 1.0 kg worst payload, weight 111 N); 8-DOF 9.45 kg (8.45 kg plus 1.0 kg, weight 93 N) |
| A3 | Planar leg: thigh 160 mm, shank 180 mm, knee backward; standing hip height 260 mm; stride foot offset ±60 mm; crouch height 140 mm; abduction axis at the body side with a 120 mm lateral arm to the foot (feet at ±250 mm) |
| A4 | Load cases: 4-leg stance F = W/4; two-foot support (trot or worst crawl) as a bounding case, F = W/2 |
| A5 | Dynamic allowance 2× on static torque for peak (no impact is modelled) |
| A6 | Planning factor 1.5 on peak (not a validated margin) |
| A7 | Peak joint speed 5 rad/s (about 48 rpm) |
| A8 | Module masses: abduction 0.35 kg, hip pitch 0.40 kg, knee 0.40 kg; thigh 0.09 kg, shank 0.07 kg, foot pad 0.03 kg |
| A9 | Average power 90 W (electronics 20 W, joints 70 W); battery 6S3P of 2.5 Ah cells, 7.5 Ah nominal 21.6 V (162 Wh; capacity not stated on the sheets); 80% usable |
| A10 | Foot support points ±250 mm × ±240 mm |

## 2. Per-Joint Assessment

Output-shaft torque, one leg, 12-DOF configuration unless noted. Static = bounding load case. Peak = 2 × static (A5).

| Joint | Load case | Peak torque | Continuous torque | Speed | Range | Duty assumptions | Calculation reference | S/M/L compatibility | Margin | Status |
|---|---|---|---|---|---|---|---|---|---|---|
| Hip abduction (3-DOF module) | Two-foot support, foot 120 mm outboard of the axis, F = 55.7 N | ≈ 13.4 N·m (6.7 static) | ≈ 3.3 N·m (4-leg stand) | 5 rad/s (A7) | TBD | TBD | CALC-QR05-01 §3 | TBD | TBD | ESTIMATE |
| Hip pitch | Two-foot support, foot 60 mm from the hip line | ≈ 6.7 N·m (3.3 static); 8-DOF ≈ 5.6 | ≈ 0 N·m standing (foot under hip) | 5 rad/s | TBD | TBD | CALC-QR05-01 §2 | TBD | TBD | ESTIMATE |
| Knee | Two-foot support, foot 60 mm forward, knee back; knee–foot distance 135 mm | ≈ 15.0 N·m (7.5 static); 8-DOF ≈ 12.5 | ≈ 3.0 N·m (4-leg stand; 8-DOF ≈ 2.5) | 5 rad/s | TBD | TBD | CALC-QR05-01 §1 | TBD | TBD | ESTIMATE |

### 2.1 Required with planning factor (A6, 1.5× on peak)

| Joint | 12-DOF peak × 1.5 | 8-DOF peak × 1.5 |
|---|---|---|
| Hip abduction | ≈ 20 N·m | n/a |
| Hip pitch | ≈ 10 N·m | ≈ 8.3 N·m |
| Knee | ≈ 22.6 N·m | ≈ 18.8 N·m |

### 2.2 Other cases

- Low payload (0.5 kg, 12 DOF): knee ≈ 7.2 N·m, abduction ≈ 6.4 N·m, hip pitch ≈ 3.2 N·m static.
- Sit-to-stand (crouch 140 mm, four feet, 12 DOF): knee ≈ 4.3 N·m static (knee–foot distance 153 mm).
- Swing leg held horizontal: hip pitch ≈ 0.97 N·m, knee ≈ 0.12 N·m.
- Sensitivity: every +0.1 kg on each of the 12 modules adds 1.2 kg (about 11%) and raises torques by about the same share. Sizing the modules to the planning torques would need heavier units (assumed about 0.2 kg heavier on average), adding about 2.4 kg and raising torques about 21%. The abduction torque scales with the lateral arm: a stance 30 mm narrower (arm 90 mm) lowers it by 25%.

### 2.3 Hand calculation (CALC-QR05-01 summary)

- **Geometry (§1):** foot below the hip at h = 260 mm: knee y = (L2² − L1² − h²) ÷ (2h) = (32,400 − 25,600 − 67,600) ÷ 520 = −116.9 mm; knee offset x = √(160² − 116.9²) = 109 mm. Foot forward 60 mm: D = √(60² + 260²) = 266.8 mm; α = acos[(160² + 266.8² − 180²) ÷ (2 × 160 × 266.8)] = 41.0°; thigh angle from vertical = 13.0° − 41.0° = −28.0°; knee x = −75 mm; knee–foot horizontal distance = 60 + 75 = **135 mm**.
- **Knee (§1):** T = 55.7 × 0.135 ≈ **7.5 N·m**; standing 4-leg: 27.8 × 0.109 ≈ **3.0 N·m**.
- **Hip pitch (§2):** T = 55.7 × 0.060 ≈ **3.3 N·m**.
- **Hip abduction (§3):** T = 55.7 × 0.120 ≈ **6.7 N·m**; 4-leg 27.8 × 0.120 ≈ 3.3 N·m.
- **Swing leg (§4):** hip Σ m·d = 0.09(0.080) + 0.40(0.160) + 0.07(0.250) + 0.03(0.340) = 0.0989 kg·m, T = **0.97 N·m**.
- **Power (§5):** knee 7.5 N·m × 5 rad/s ≈ 38 W, abduction ≈ 33 W, hip pitch ≈ 17 W per joint (not simultaneous peaks).

### 2.4 Energy and runtime (paper estimate)

Assumed 90 W average (A9). Battery 162 Wh nominal; 80% usable gives 130 Wh and about **1.4 h**. At 150 W the runtime falls to about 0.9 h. Battery capacity is UNKNOWN on the sheets, so runtime is TBD; protection and charging are not assessed.

## 3. Reference Limitations

The elbow discussion reference of 24V, 10 N·m continuous and 20 N·m peak is not a universal specification. It is **not** used here. Each joint is derived independently from the QR-05 leg geometry and the stated assumptions.

## 4. Actuator Source Traceability

No input from `kritva-actuator` has been supplied for QR-05.

- Source repository and path: TBD (none supplied)
- Revision / commit: TBD
- Source document or specification: TBD
- Maturity: UNKNOWN
- Verification status and limitations: None. The concept sheet calls the actuators Kritva S/M/L compatible, but no joint has been mapped. Preliminary repository values, when received, must not be treated as validated specifications.

## 5. Findings and Open Items

- **Torque/speed feasibility:** Not assessable without S/M/L data. The knee is the most loaded joint (about 7.5 N·m static, about 22.6 N·m with allowance and factor), followed by the hip abduction. Whether the assumed modules (0.35 – 0.40 kg) can deliver that is open, and the answer feeds back into the mass.
- **S/M/L mapping rationale:** NOT STARTED. Abduction, hip pitch and knee loads differ by a factor of two or more, so a single size for all three may be wasteful; this is an observation, not a mapping. The interface must also accept both module types.
- **Margin interpretation:** TBD. Margin = rating ÷ required torque (Section 2.1) once ratings are supplied.
- **Missing inputs and risks:**
  1. Link lengths, hip height, joint ranges, stance width, module and body masses are assumed.
  2. Touchdown impact is only covered by the 2× allowance.
  3. Walking RMS torque and thermal limits at standing are not assessed.
  4. Battery capacity, peak current at 24 V and discharge limit are UNKNOWN.
  5. Gearbox type and backdrive (power-off collapse) not selected.
- **Next steps (paper only):** get S/M/L data with traceability; iterate mass and torque; confirm stance width; add joint ranges and a gait cycle; file CALC-QR05-01.

## 6. HOLD D-003

Paper calculations and compatibility assessment only. No actuator purchase, detailed CAD, final BOM, fabrication, assembly or physical testing. All require explicit owner decision under HOLD D-003.
