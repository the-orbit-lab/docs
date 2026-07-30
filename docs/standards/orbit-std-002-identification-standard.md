# ORBIT-STD-002 — Engineering Artifact Identification Standard

## Purpose

This standard defines how Orbit Lab engineering artifacts are identified and named.

The objective is to make each requirement, decision, test, experiment, interface and physical item easy to recognize, reference and trace.

## Identifier format

The standard identifier format is:

```text
TYPE-SUBSYSTEM-NUMBER
```

Example:

```text
TEST-OBC-0001
```

Where:

* `TEST` identifies the artifact type;
* `OBC` identifies the responsible subsystem;
* `0001` is a sequential number.

Identifiers must be unique and must never be reused.

## Project-wide artifacts

Artifacts that apply to the entire Orbit Lab project may use `SYS` as the subsystem:

```text
ADR-SYS-0001
REQ-SYS-0001
RISK-SYS-0001
```

Orbit Lab standards use a separate format:

```text
ORBIT-STD-001
ORBIT-STD-002
```

## Artifact types

| Code     | Artifact            | Main question                             |
| -------- | ------------------- | ----------------------------------------- |
| `ADR`    | Decision Record     | Why was this solution selected?           |
| `REQ`    | Requirement         | What must the system satisfy?             |
| `TEST`   | Verification Test   | Was a requirement satisfied?              |
| `EXP`    | Experiment          | What are we trying to discover?           |
| `IF`     | Interface Record    | How do two systems connect?               |
| `PART`   | Designed Part       | What is this manufactured part?           |
| `ASSY`   | Assembly Record     | Which parts form this assembly?           |
| `COMP`   | Purchased Component | What is this selected component?          |
| `PCB`    | Electronic Board    | What is this board and its revision?      |
| `PROC`   | Procedure           | How is an operation repeated?             |
| `RISK`   | Risk Record         | What can go wrong?                        |
| `LOG`    | Engineering Log     | What happened during development?         |
| `REPORT` | Engineering Report  | What was concluded?                       |
| `MODEL`  | Engineering Model   | What system or phenomenon is represented? |
| `DATA`   | Dataset             | What measurements are contained here?     |

## Subsystem codes

| Code   | Subsystem                                 |
| ------ | ----------------------------------------- |
| `SYS`  | Complete Orbit Lab system                 |
| `OBC`  | On-Board Computer                         |
| `FSW`  | Flight Software                           |
| `ADCS` | Attitude Determination and Control System |
| `EPS`  | Electrical Power System                   |
| `COM`  | Communications                            |
| `GS`   | Ground Station                            |
| `PAY`  | Payload                                   |
| `STR`  | Mechanical Structure                      |
| `THM`  | Thermal System                            |
| `SIM`  | Simulation                                |
| `HIL`  | Hardware-in-the-Loop                      |
| `GSE`  | Ground Support Equipment                  |
| `ORB`  | Orbital Analysis                          |
| `DOC`  | Documentation Infrastructure              |

New subsystem codes must be documented before regular use.

## Examples

```text
ADR-OBC-0001
REQ-EPS-0002
TEST-ADCS-0003
EXP-COM-0001
IF-OBC-EPS-0001
PART-STR-0004
COMP-OBC-0002
RISK-SYS-0001
```

## Interface identifiers

Interface records may contain both connected systems:

```text
IF-OBC-EPS-0001
IF-OBC-COM-0001
IF-FSW-GS-0001
```

The order should follow the primary direction of responsibility or data flow.

## File naming

Markdown filenames must use lowercase kebab-case.

Format:

```text
identifier-short-title.md
```

Examples:

```text
adr-obc-0001-select-rust.md
req-obc-0001-watchdog-supervision.md
test-adcs-0003-wheel-speed-stability.md
if-obc-eps-0001-i2c-interface.md
part-str-0004-lower-corner-bracket.md
```

Avoid filenames such as:

```text
final-document.md
new-test.md
motor-good-version.md
test-2.md
final-final.step
```

## Physical revisions

Mechanical parts, assemblies and electronic boards use revision letters:

```text
PART-STR-0004 Rev A
PART-STR-0004 Rev B
PCB-OBC-0001 Rev A
```

A revision is used when the artifact remains the same logical item but its design changes.

A new identifier is required when the new item is not interchangeable with the previous one or serves a different function.

## Document revisions

Markdown documents use semantic document revisions:

```text
0.1.0
0.2.0
1.0.0
```

Recommended interpretation:

* `0.1.0`: initial draft;
* `0.x.0`: significant draft update;
* `1.0.0`: first accepted version;
* `1.0.x`: corrections that do not change meaning;
* `1.x.0`: meaningful content changes.

## Status values

Recommended document statuses:

* Draft
* Proposed
* Under Review
* Accepted
* Implemented
* Verified
* Rejected
* Superseded
* Deprecated
* Cancelled

Completed or obsolete artifacts must not be deleted solely to hide their history.

## Common metadata

Controlled Markdown documents should begin with front matter:

```yaml
---
id: TYPE-SUBSYSTEM-0000
title: Document title
status: Draft
revision: 0.1.0
created: YYYY-MM-DD
updated: YYYY-MM-DD
owner: Orbit Lab
related_requirements: []
related_decisions: []
related_tests: []
related_issues: []
---
```

Fields that do not apply may be omitted when allowed by the corresponding template.

## Registers

The documentation repository should maintain registers for controlled artifacts.

Examples:

```text
docs/registers/adr-register.md
docs/registers/requirement-register.md
docs/registers/test-register.md
docs/registers/interface-register.md
```

A register should contain at least:

| ID | Title | Subsystem | Status | Revision |
| -- | ----- | --------- | ------ | -------- |

Registers prevent duplicated identifiers and provide a central index of existing records.

## Traceability

Artifacts should reference related records whenever relevant.

Example:

```text
REQ-OBC-0004
    ├── ADR-OBC-0002
    ├── TEST-OBC-0007
    ├── orbit-obc#18
    └── REPORT-OBC-0001
```

This should allow a reader to answer:

* Why was this implemented?
* Which requirement requested it?
* Which decision selected the approach?
* Which test verified it?
* Where is the supporting evidence?
