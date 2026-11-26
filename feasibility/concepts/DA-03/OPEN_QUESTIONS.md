# DA-03 — Open Questions and Dependencies

| Property | Value |
|---|---|
| Document ID | KMECH-OQ-DA-03 |
| Repository | `KritvaOS/kritva-mechanical` |
| Document Type | Open Questions Register |
| Status | PROPOSED |
| Owner | Dinesh |
| Assigned Intern | INTERN-02 |
| Version | 0.2.0 |
| Last Updated | 2026-11-25 |
| Authority | Feasibility tracking; subject to owner review |
| Related Documents | `README.md`, `REQUIREMENTS.md`, `ARCHITECTURE.md`, `feasibility/REQUIREMENTS_REGISTER.md`, `feasibility/RISK_REGISTER.md` |

## 1. Purpose

Track missing inputs, unresolved assumptions, dependencies and owner decisions for DA-03 (Mobile Dual-Arm). Nothing here approves a value. Risk register IDs are `RISK-TBD` until the register is checked.

## 2. Open Questions

| ID | Question / missing input | Category | Status | Impact | Required action / dependency | Owner |
|---|---|---|---|---|---|---|
| OQ-001 | D5: 350 mm reach, 800 mm overall width and 800 mm total reach cannot be reconciled with a 300 mm torso. What do the widths refer to, and what is the shoulder spacing? | Technical | INCOMPLETE | High | Owner to clarify | Dinesh |
| OQ-002 | Required payload, reach, weight and runtime. Printed values are CONCEPT_TARGET with no stated basis. | Data | UNKNOWN | High | Owner decision (CREQ-008, CREQ-009, CREQ-013) | Dinesh |
| OQ-003 | What work surface height must the robot serve ("tabletop-height")? The assumed gripper range is about 225 – 575 mm with no floor reach, and shoulder height is an assumption. | Technical | TBD | High | Owner decision (CREQ-007) | Dinesh |
| OQ-004 | `kritva-actuator` source, revision and maturity, and the S/M/L mapping of arm joints and wheel drives. | Data | BLOCKED | High | Owner to supply traceable data (CREQ-010, CREQ-011) | Dinesh |
| OQ-005 | Battery capacity, protection, charging and battery safety approach. Capacity is not stated on the sheets. | Data / safety | UNKNOWN | High | Owner decision (CREQ-013, CREQ-016) | Dinesh |
| OQ-006 | Wheel, tyre, gear ratio, floor friction, speed and slope targets, and the turning strategy (turning in place sets the drive size). | Technical | TBD | High | Owner input (CREQ-011) | Dinesh / INTERN-02 |
| OQ-007 | Safety approach: emergency stop (red button unlabelled), pinch and base collision protection, arm droop and roll-away on power loss. | Safety | TBD | High | Owner decision (CREQ-016) | Dinesh |
| OQ-008 | D3 wrist terminology (rotation or pitch), D4 LiDAR in the baseline, D6 torso width and adjustable mast. | Technical | OPEN | Medium | Owner decision (CREQ-004, CREQ-005) | Dinesh |
| OQ-009 | Interface list, Kritva Edge dimensions, EtherCAT provisions, and whether S/M/L modules integrate drivers. | Technical / data | UNKNOWN | Medium | Create `INTERFACES.md`; owner to supply data (CREQ-014) | Dinesh / INTERN-02 |
| OQ-010 | Powered or passive grippers; joint ranges and duty; cost basis for Kritva Edge, actuators and battery. | Technical / cost | TBD | Medium | Owner decision or input | Dinesh |
| OQ-011 | Housekeeping: `FREQ`/`U`/`RISK` IDs; filing CALC-DA03-01 to -03. | Documentation | TBD | Low | Intern updates IDs and files calculations | INTERN-02 |

## 3. Assumptions Requiring Confirmation

- Payload: UNKNOWN (calculations use 0.2 kg worst case)
- Reach: UNKNOWN (printed 350 mm; link split 175 / 100 / 75 mm assumed)
- Target mass: UNKNOWN (estimate about 15.7 kg, not a target)
- Joint torque and speed: TBD (elbow about 0.8 N·m, wrist about 0.2 N·m, wheel turning about 2.5 N·m per channel)
- Actuator S/M/L mapping: TBD
- Dimensions and interfaces: TBD (shoulders at ±150 mm and 400 mm height; torso 250 mm deep and 300 mm tall; wheel contacts ±190 mm × ±150 mm)
- Cost and component availability: UNKNOWN
- Other assumptions: upper arm rigid and horizontal; 100 mm wheels; friction 0.5; 20 N accidental load; battery 10 Ah

## 4. Owner Decisions Required

| Decision | Reason | Related requirement / risk | Status |
|---|---|---|---|
| Clarify widths and shoulder spacing (D5) | Affects mounts, overlap and stability | OQ-001; CREQ-006, CREQ-007; RISK-TBD | OWNER DECISION REQUIRED |
| Set payload, reach, weight, runtime and work surface height | UNKNOWN in the register | OQ-002, OQ-003; CREQ-007 to CREQ-009, CREQ-013 | OWNER DECISION REQUIRED |
| Supply actuator source data and S/M/L approach | Blocks actuator compatibility | OQ-004; CREQ-010, CREQ-011 | OWNER DECISION REQUIRED |
| Battery and safety approach | Li-ion and moving-base hazards | OQ-005, OQ-007; CREQ-013, CREQ-016; RISK-TBD | OWNER DECISION REQUIRED |
| Resolve D3, D4 and D6 | Wrist, LiDAR, torso and mast definition | OQ-008; CREQ-004, CREQ-005 | OWNER DECISION REQUIRED |

## 5. Disposition

| Item | Disposition | Evidence | Date |
|---|---|---|---|
| D1 (no dimension or DOF disagreement) | NONE FOUND | `README.md` §10 | 2026-10-31 |
| D2 wheel arrangement | RESOLVED by owner: four wheels as two driven pairs, 2 base actuators | `README.md` §10 | 2026-10-31 |
| D3, D4, D6 | OPEN: see OQ-008 | `README.md` §10 | n/a |
| D5 reach and width | OPEN: see OQ-001 | `README.md` §10 | n/a |

## 6. HOLD D-003

Open questions tracking does not authorize CAD, final BOM, quotations, procurement, fabrication, assembly or physical testing. All remain NOT STARTED pending explicit owner decision under HOLD D-003.
