# QR-01 — Open Questions and Dependencies

| Property | Value |
|---|---|
| Document ID | KMECH-OQ-QR-01 |
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

Track missing inputs, unresolved assumptions, dependencies and owner decisions for QR-01 (Compact Quadruped). Nothing here approves a value. Risk register IDs are `RISK-TBD` until the register is checked.

## 2. Open Questions

| ID | Question / missing input | Category | Status | Impact | Required action / dependency | Owner |
|---|---|---|---|---|---|---|
| OQ-001 | Weight and payload targets (D4): printed 2.5 – 4 kg and 0.3 – 0.8 kg appear on the concept sheet only, with no stated basis. The estimate is about 6.3 kg. | Data | UNKNOWN | High | Owner decision (CREQ-005, CREQ-009) | Dinesh |
| OQ-002 | `kritva-actuator` source, revision and maturity, and the hip and knee S/M/L mapping. | Data | BLOCKED | High | Owner to supply traceable data (CREQ-007) | Dinesh |
| OQ-003 | Leg link lengths, hip height, joint ranges and stride (all assumed). | Technical | TBD | High | Owner input or confirmation of intern proposal (CREQ-006) | Dinesh / INTERN-02 |
| OQ-004 | Battery capacity, placement (not drawn), protection and charging. | Data | UNKNOWN | High | Owner decision (CREQ-010, CREQ-011) | Dinesh |
| OQ-005 | Gait and turning expectations: planar legs give no side-stepping and turning needs foot slip. Is this acceptable for the demonstration? | Technical | TBD | High | Owner decision (CREQ-008) | Dinesh |
| OQ-006 | Safety approach: emergency stop (not shown), collapse on power loss, falls, battery. | Safety | TBD | High | Owner decision (CREQ-014) | Dinesh |
| OQ-007 | D6 sensor baseline (IMU, LiDAR, camera) and whether foot force sensing is included. | Technical | OPEN | Medium | Owner decision (CREQ-002, CREQ-003) | Dinesh |
| OQ-008 | Hip mount geometry that gives the 400 mm overall width on a 250 mm body, and the 420 mm overall length. | Technical | TBD | Medium | Owner to confirm; intern to sketch (CREQ-004) | Dinesh / INTERN-02 |
| OQ-009 | Cooling and thermal limits at standing; interface list, Kritva Edge dimensions, EtherCAT provisions, and whether S/M/L modules integrate drivers. | Technical / data | UNKNOWN | Medium | Create `INTERFACES.md`; owner to supply data (CREQ-011) | Dinesh / INTERN-02 |
| OQ-010 | Cost basis for Kritva Edge, actuators and battery. | Cost / data | UNKNOWN | Medium | Owner to supply basis | Dinesh |
| OQ-011 | Housekeeping: stale README wording on hip abduction and 3 DOF (D1 resolved to 2 DOF); duplicated risk item; `FREQ`/`U`/`RISK` IDs; filing CALC-QR01-01 to -03. | Documentation | TBD | Low | Owner confirms wording; intern updates IDs and files calculations | Dinesh / INTERN-02 |

## 3. Assumptions Requiring Confirmation

- Payload: UNKNOWN (calculations use 0.8 kg worst case)
- Reach: not applicable as arm reach; leg workspace TBD
- Target mass: UNKNOWN (estimate about 6.3 kg, not a target)
- Joint torque and speed: TBD (knee about 3.9 N·m and hip about 2.1 N·m static worst case)
- Actuator S/M/L mapping: TBD
- Dimensions and interfaces: TBD (thigh 130 mm, shank 150 mm, hip height 220 mm, leg planes ±190 mm, feet ±190 × ±180 mm)
- Cost and component availability: UNKNOWN
- Other assumptions: friction 0.5; stride ±60 mm; 2× dynamic allowance; battery 5 Ah

## 4. Owner Decisions Required

| Decision | Reason | Related requirement / risk | Status |
|---|---|---|---|
| Set weight and payload values | UNKNOWN in the register; estimate far above the printed weight | OQ-001; CREQ-005, CREQ-009; RISK-TBD | OWNER DECISION REQUIRED |
| Supply actuator source data and S/M/L approach | Blocks actuator compatibility | OQ-002; CREQ-007 | OWNER DECISION REQUIRED |
| Confirm leg geometry, ranges and gait expectations | Assumed values drive stability and torque | OQ-003, OQ-005; CREQ-006, CREQ-008 | OWNER DECISION REQUIRED |
| Battery and safety approach | Li-ion, falls and collapse on power loss | OQ-004, OQ-006; CREQ-010, CREQ-014; RISK-TBD | OWNER DECISION REQUIRED |
| Resolve D6 sensor baseline | Open on the artwork | OQ-007; CREQ-003 | OWNER DECISION REQUIRED |

## 5. Disposition

| Item | Disposition | Evidence | Date |
|---|---|---|---|
| D1 DOF per leg | RESOLVED: both sheets show 2 DOF per leg, 8 actuators | `README.md` §10 | 2026-10-31 |
| D2, D3, D5 (body size, overall extents, titles) | RESOLVED: sheets agree after regeneration | `README.md` §10 | 2026-10-31 |
| D4 weight and payload | OPEN: see OQ-001 | `README.md` §10 | n/a |
| D6 sensors | OPEN: see OQ-007 | `README.md` §10 | n/a |

## 6. HOLD D-003

Open questions tracking does not authorize CAD, final BOM, quotations, procurement, fabrication, assembly or physical testing. All remain NOT STARTED pending explicit owner decision under HOLD D-003.
