---

title: Engineering Artifact Types
status: Draft
revision: 0.1.0
created: 2026-07-29
updated: 2026-07-29
owner: Orbit Lab
----------------

# Engineering Artifact Types

## Purpose

This guide explains when each Orbit Lab engineering artifact should be created.

The identification, naming and revision rules for these artifacts are defined by the Orbit Lab documentation standards.

## Quick reference

| Type     | Artifact                | Main question                             |
| -------- | ----------------------- | ----------------------------------------- |
| `ADR`    | Decision Record         | Why was this option selected?             |
| `REQ`    | Requirement             | What must the system satisfy?             |
| `TEST`   | Verification Test       | Was a requirement satisfied?              |
| `EXP`    | Experiment              | What are we trying to discover?           |
| `IF`     | Interface Record        | How do two systems connect?               |
| `PART`   | Part Record             | What is this designed physical part?      |
| `ASSY`   | Assembly Record         | How are multiple parts assembled?         |
| `COMP`   | Component Record        | What is this purchased component?         |
| `PCB`    | Electronic Board Record | What is this board and revision?          |
| `PROC`   | Procedure               | How can an operation be repeated?         |
| `RISK`   | Risk Record             | What could go wrong?                      |
| `LOG`    | Engineering Log         | What happened during development?         |
| `REPORT` | Engineering Report      | What was concluded from the work?         |
| `MODEL`  | Engineering Model       | What system or phenomenon is represented? |
| `DATA`   | Dataset Record          | What data was collected?                  |

## ADR — Decision Record

Create an ADR when an important engineering choice is made.

Typical examples include:

* selecting a microcontroller;
* selecting Rust instead of another language;
* choosing a scheduling model;
* selecting a communication protocol;
* choosing a structural material;
* choosing a sensor or actuator;
* selecting a manufacturing process;
* defining a repository architecture.

An ADR should record:

* the problem;
* constraints and decision drivers;
* alternatives considered;
* the selected option;
* the rationale;
* positive and negative consequences;
* risks introduced;
* how the decision will be validated.

An ADR is not required for trivial or easily reversible changes.

Example:

```text
ADR-OBC-0001 — Select the initial OBC microcontroller
```

## REQ — Requirement

Create a requirement when the system must satisfy a clear and verifiable condition.

A requirement should be:

* necessary;
* specific;
* unambiguous;
* measurable;
* verifiable;
* connected to a mission, safety or engineering need.

Prefer:

> The OBC shall transmit housekeeping telemetry at least once every second while operating in Nominal Mode.

Avoid:

> The OBC should transmit telemetry frequently.

Each requirement should define:

* what must happen;
* why it is necessary;
* its source;
* priority;
* verification method;
* measurable acceptance criteria.

Example:

```text
REQ-OBC-0001 — Housekeeping telemetry frequency
```

## TEST — Verification Test

Create a test when a known requirement or acceptance criterion must be verified.

A test answers:

> Does the system satisfy the expected condition?

A test should record:

* requirements under test;
* exact hardware configuration;
* software commit or release;
* preconditions;
* procedure;
* expected result;
* pass criteria;
* actual result;
* measurements;
* anomalies;
* evidence.

Example:

```text
TEST-OBC-0001 — Housekeeping telemetry frequency verification
```

## EXP — Experiment

Create an experiment when information must be discovered before a requirement, design or decision can be finalized.

An experiment answers:

> What happens under these conditions?

Typical examples include:

* measuring motor speed stability;
* comparing structural materials;
* evaluating radio range;
* measuring thermal behavior;
* estimating vibration;
* comparing control parameters.

An experiment should include:

* research question;
* hypothesis;
* independent variables;
* dependent variables;
* controlled variables;
* equipment;
* configuration;
* procedure;
* raw data;
* results;
* uncertainty;
* conclusion;
* engineering impact.

The distinction is:

```text
Experiment:
How stable is this motor at 3000 RPM?

Test:
Does this motor remain within the required ±2% tolerance?
```

## IF — Interface Record

Create an interface record whenever two systems, subsystems or components exchange:

* electrical power;
* signals;
* commands;
* telemetry;
* mechanical loads;
* thermal energy;
* data;
* physical alignment or mounting.

Typical examples include:

```text
OBC ↔ EPS
OBC ↔ radio
OBC ↔ IMU
flight software ↔ ground station
structure ↔ reaction wheel assembly
```

An interface record may define:

* connector and pinout;
* voltage and logic levels;
* protocol;
* addresses;
* message formats;
* units;
* timing;
* direction;
* startup behavior;
* timeout behavior;
* error handling;
* mechanical dimensions;
* verification tests.

Example:

```text
IF-OBC-EPS-0001 — OBC to EPS I²C interface
```

## PART — Part Record

Create a part record for a physical item designed or manufactured by Orbit Lab.

Examples include:

* structural rail;
* corner bracket;
* mounting plate;
* reaction wheel disk;
* sensor bracket;
* enclosure.

A part record should document:

* function;
* design rationale;
* material;
* dimensions;
* tolerances;
* estimated and measured mass;
* manufacturing process;
* CAD and drawing files;
* connected parts;
* fasteners;
* risks;
* inspections and tests;
* revision history.

Example:

```text
PART-STR-0001 — Lower corner bracket
```

## ASSY — Assembly Record

Create an assembly record when multiple parts are combined into a controlled physical unit.

Examples include:

* reaction wheel assembly;
* CubeSat structural assembly;
* OBC mounting assembly;
* testbed support assembly.

An assembly record should define:

* function;
* included parts and revisions;
* assembly order;
* required tools;
* fasteners and torque;
* wiring;
* alignment requirements;
* final mass;
* interfaces;
* inspection and testing.

Example:

```text
ASSY-ADCS-0001 — Reaction wheel assembly
```

## COMP — Component Record

Create a component record for an important purchased item.

Examples include:

* microcontroller;
* development board;
* motor;
* IMU;
* battery cell;
* radio module;
* connector;
* voltage regulator.

A component record should include:

* function in the system;
* manufacturer;
* part number;
* supplier;
* important specifications;
* datasheets;
* alternatives considered;
* selection rationale;
* known limitations;
* electrical and mechanical interfaces;
* related decisions and tests.

Small generic items such as ordinary resistors do not need individual component records unless they are critical or unusual.

Example:

```text
COMP-OBC-0001 — Initial OBC development board
```

## PCB — Electronic Board Record

Create a PCB record for each controlled electronic board designed by Orbit Lab.

It should identify:

* board function;
* revision;
* block diagram;
* main components;
* power architecture;
* communication interfaces;
* connectors;
* test points;
* design constraints;
* schematic;
* PCB layout;
* Gerbers;
* bill of materials;
* assembly files;
* bring-up procedure;
* known issues;
* verification tests.

Example:

```text
PCB-OBC-0001 — Main OBC board
```

## PROC — Procedure

Create a procedure when an operation must be performed consistently and repeatedly.

Examples include:

* flashing the OBC firmware;
* assembling a reaction wheel;
* calibrating the IMU;
* performing a power test;
* preparing a thermal experiment;
* manufacturing a mechanical part.

A procedure should include:

* purpose;
* scope;
* required equipment;
* safety precautions;
* preconditions;
* ordered steps;
* expected result;
* troubleshooting;
* records generated.

Example:

```text
PROC-OBC-0001 — Flash the OBC firmware
```

## RISK — Risk Record

Create a risk record when an uncertain event could negatively affect the project or system.

Examples include:

* unavailable components;
* excessive structural mass;
* battery overheating;
* insufficient radio range;
* uncontrolled task blocking;
* sensor saturation;
* delayed manufacturing.

A risk should document:

* description;
* cause;
* consequence;
* probability;
* impact;
* risk level;
* mitigation;
* contingency;
* trigger;
* owner;
* status.

Example:

```text
RISK-OBC-0001 — Unsupported microcontroller toolchain
```

## LOG — Engineering Log

Create an engineering log for a meaningful development, manufacturing or investigation session.

A log is useful when the session contains:

* a technical discovery;
* a failure;
* multiple attempts;
* measurements;
* debugging;
* design changes;
* decisions;
* unresolved questions.

A log should record:

* objective;
* initial state;
* work performed;
* problems;
* hypotheses;
* attempts;
* results;
* evidence;
* related commits and issues;
* next steps.

A log does not need to document every line of code written.

Example:

```text
LOG-OBC-2026-07-29 — First UART bring-up
```

## REPORT — Engineering Report

Create a report when results from multiple tests, experiments or analyses must be consolidated.

Typical reports include:

* reaction wheel evaluation;
* OBC reliability report;
* power budget analysis;
* subsystem integration report;
* thermal test campaign;
* prototype validation report.

A report should contain:

* executive summary;
* objective;
* background;
* methodology;
* configuration;
* results;
* analysis;
* limitations;
* conclusions;
* recommendations;
* related evidence.

Example:

```text
REPORT-ADCS-0001 — Reaction wheel motor evaluation
```

## MODEL — Engineering Model

Create a model record for an important mathematical, physical or computational representation.

Examples include:

* orbital propagation model;
* CubeSat rotational dynamics;
* power consumption model;
* thermal model;
* radio link-budget model;
* reaction wheel model.

A model record should explain:

* purpose;
* equations;
* variables and units;
* assumptions;
* inputs;
* outputs;
* validity range;
* limitations;
* implementation;
* validation;
* references.

Example:

```text
MODEL-ORB-0001 — Circular orbit model
```

## DATA — Dataset Record

Create a dataset record when collected data must be preserved, understood and reused.

It should document:

* source;
* collection date;
* related experiment or test;
* equipment;
* sampling frequency;
* variables;
* units;
* file format;
* missing or invalid values;
* processing performed;
* license and access restrictions;
* checksum or integrity information when needed.

Raw data should remain immutable.

Example:

```text
DATA-ADCS-0001 — Reaction wheel speed measurements
```

## Choosing the correct artifact

Use this decision flow:

```text
Is it something the system must satisfy?
→ REQ

Was an important option selected?
→ ADR

Are we discovering unknown information?
→ EXP

Are we checking a requirement?
→ TEST

Are two systems connecting or exchanging something?
→ IF

Was a physical item designed?
→ PART or ASSY

Was an important item purchased?
→ COMP

Was an electronic board designed?
→ PCB

Must an operation be repeated consistently?
→ PROC

Could something negatively affect the project?
→ RISK

Are we recording a development session?
→ LOG

Are multiple results being consolidated?
→ REPORT

Is a physical or mathematical system being represented?
→ MODEL

Does collected data need to be preserved and understood?
→ DATA
```

## Combining artifacts

A single engineering task may create several related artifacts.

Example:

```text
EXP-ADCS-0001
Evaluate candidate reaction wheel motors
        ↓
ADR-ADCS-0002
Select the motor
        ↓
REQ-ADCS-0004
Define required speed stability
        ↓
TEST-ADCS-0005
Verify the selected motor
        ↓
REPORT-ADCS-0001
Consolidate the results
```

Do not create every possible document automatically.

Create only the artifacts needed to preserve reasoning, configuration, verification and evidence.

## Related standards

* [Documentation Standard](../standards/orbit-std-001-documentation-standard.md)
* [Identification Standard](../standards/orbit-std-002-identification-standard.md)
* [File Naming Standard](../standards/orbit-std-003-file-naming-standard.md)
* [Revision Control Standard](../standards/orbit-std-004-revision-control.md)
* [README Standard](../standards/orbit-std-005-readme-standard.md)
