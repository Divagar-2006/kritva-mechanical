# DA-03 — Mobile Dual-Arm

| Property | Value |
|---|---|
| Document ID | KMECH-CONCEPT-DA-03 |
| Repository | `KritvaOS/kritva-mechanical` |
| Document Type | Concept Overview |
| Status | PROPOSED |
| Owner | Dinesh |
| Assigned Intern | INTERN-02 |
| Version | 0.4.0 |
| Last Updated | 2026-11-25 |
| Authority | Feasibility study; subject to owner review |
| Related Documents | `feasibility/STUDY_PLAN.md`, `REQUIREMENTS.md`, `ARCHITECTURE.md`, `MECHANICAL_ANALYSIS.md`, `ACTUATOR_ANALYSIS.md`, `MASS_BUDGET.md`, `COST_MODEL.md`, `OPEN_QUESTIONS.md`, `docs/images/ARTWORK_MANIFEST.json` |

This overview records the concept as printed on the two artwork sheets and the state of the preliminary paper work. Printed values are CONCEPT_TARGET (indicative, unapproved). Calculated values are ESTIMATES. Nothing here approves any value.

## 1. Concept Identification

- Concept ID: DA-03
- Concept name: Mobile Dual-Arm
- Family: Dual-arm
- Complexity: High (relative engineering category, not a validated assessment)
- Assigned intern: INTERN-02
- Assessment revision: Draft 1 (preliminary paper analysis, owner review pending)

## 2. Concept Summary

- **Intended configuration:** Differential-drive base with four wheels (left pair and right pair, one drive channel per side, owner decision 2026-10-31) carrying a fixed torso with two symmetric 3-DOF arms (shoulder yaw, elbow pitch, wrist pitch). 8 actuators in total (6 arm + 2 base); grippers not counted. 24 V Li-ion battery in the base. Optional camera and sensor mast. Sheets: `docs/images/KMECH-CONCEPT-DA-03.png`, `docs/images/KMECH-CROSS-SECTION-DA-03.png`.
- **Primary demonstration objective:** Kritva platform demonstration (compact tabletop-height mobile manipulation, pick-and-place, inspection, teleoperation).
- **Key capabilities (as printed, CONCEPT_TARGET):** 350 mm reach per arm; 0.1 – 0.2 kg payload per arm (est.); 12 – 18 kg (est.); 400 mm × 450 mm base; 650 mm height with mast; 800 mm overall width; indoor flat terrain, uneven terrain as a future extension.
- **Major assumptions:** Listed in `ACTUATOR_ANALYSIS.md` (A1 – A13, W1 – W9), `MASS_BUDGET.md` (M1 – M12) and `MECHANICAL_ANALYSIS.md` (S1 – S7). Key ones: link split 175 / 100 / 75 mm; upper arm rigid and horizontal (no shoulder pitch joint); shoulders on the torso sides, 400 mm above ground; 100 mm wheels; contact points at ±190 mm × ±150 mm; battery 6S, 10 Ah (capacity is not stated on the sheets).
- **Known limitations:** Three DOF per arm gives gripper position only, with no independent orientation or roll. The assumed workspace does not reach the floor (lowest gripper height about 225 mm). Not to scale, not CAD. No joint ranges, torque, speed, battery capacity or camera data are printed. No S/M/L mapping.

## 3. Folder Contents

Drafted (preliminary, PROPOSED): `REQUIREMENTS.md`, `ARCHITECTURE.md`, `MECHANICAL_ANALYSIS.md`, `ACTUATOR_ANALYSIS.md`, `MASS_BUDGET.md`, `COST_MODEL.md` (categories and scope only, no cost values), `OPEN_QUESTIONS.md`.

Not yet created: `INTERFACES.md`, `calculations/` (CALC-DA03-01, -02, -03 are referenced and still to be filed), `references/`, `reviews/`, `sketches/`. No `cad/` folder while HOLD D-003 is active.

## 4. Current Assessment

- Overall status: PROPOSED. Preliminary paper drafts exist; owner review pending.
- Requirements completeness: INCOMPLETE. Payload, reach, weight and runtime remain UNKNOWN until the owner resolves them.
- Architecture assessment: Preliminary draft complete; base packaging, battery and cable routing for a moving base not yet assessed in detail.
- Engineering assessment (estimates):
  - Elbow about 0.8 N·m holding and wrist about 0.2 N·m (0.2 kg payload); the yaw output bearing carries about 2.6 N·m moment because there is no shoulder pitch joint.
  - Wheel drive per channel: about 0.6 N·m at the wheel for straight driving on a 5° slope; about 2.5 N·m for turning in place (scrub), so turning sets the sizing.
  - Static tipping margins are comfortable (about 4.4 – 4.6 against a 20 N disturbance) and tipping angle about 30° forward.
  - Estimated mass about 15.7 kg, inside the printed 12 – 18 kg, range about 9.2 – 22.2 kg.
- Actuator compatibility: NOT ASSESSED. No `kritva-actuator` data supplied.
- Cost assessment: Categories and scope listed only. No cost values estimated.
- Major risks: no gripper orientation control (3 DOF); working height range versus tabletop use; turning scrub and wheel drive sizing; battery capacity, protection and charging unknown; cable strain on a moving base; moving-base collision and pinch hazards; printed targets without basis.
- Evidence gaps: S/M/L data, battery capacity, joint ranges, wheel and tyre data, floor friction, shoulder height and shoulder spacing, interface list, collision envelopes.

## 5. Checkpoint Progress

| Checkpoint | Status | Review reference |
|---|---|---|
| CP2 | TBD | `reviews/` |
| CP3 | TBD | `reviews/` |
| CP4 | TBD | `reviews/` |

## 6. Open Decisions

1. **D5 (NOT VERIFIABLE):** 350 mm reach, 800 mm overall width and 800 mm total reach cannot be reconciled with a 300 mm torso (shoulders at the torso sides would give about 1,000 mm with arms extended sideways). Owner to clarify.
2. **D3 (OPEN):** wrist labelled rotation / pitch on the concept sheet, pitch elsewhere.
3. **D4 (OPEN):** whether LiDAR is in the baseline sensor set.
4. **D6 (OPEN):** whether the 300 mm torso width and the height-adjustable mast are kept.
5. Payload, reach, weight and runtime targets: UNKNOWN. BLOCKED on owner.
6. Joint and wheel-drive S/M/L mapping and `kritva-actuator` source data: BLOCKED.
7. Working height the robot must serve ("tabletop-height") and shoulder height: TBD.
8. Battery capacity, protection and charging: TBD. Powered grippers: TBD.

## 7. HOLD D-003

Paper feasibility work only. CAD, final BOM, quotations, procurement, fabrication, assembly and physical testing remain NOT STARTED and require explicit owner decision. This template does not authorize implementation.
