# ORBIT-STD-001 — Documentation Standard

## Table of contents

1. [Purpose](#purpose)
2. [Scope](#scope)
3. [Documentation principles](#documentation-principles)
4. [Source of truth](#source-of-truth)
5. [Document organization](#document-organization)
6. [Engineering artifacts](#engineering-artifacts)
7. [Traceability](#traceability)
8. [Document lifecycle](#document-lifecycle)
9. [Minimum documentation](#minimum-documentation)
10. [Related standards](#related-standards)

## Purpose

This standard defines the general documentation rules for Orbit Lab.

Its purpose is to preserve the reasoning, configuration, results and evidence produced during the development of the CubeSat testbed and its subsystems.

The documentation should allow a future reader to understand:

* what was developed;
* why it was developed;
* which alternatives were considered;
* how it was tested;
* which configuration was used;
* what evidence supports the result;
* what changed between revisions.

## Scope

This standard applies to engineering documentation produced for:

* software;
* embedded systems;
* electronics;
* mechanical design;
* simulations;
* experiments;
* verification tests;
* system integration;
* mission and orbital analysis.

It applies both to the central `docs` repository and to documentation maintained inside subsystem repositories.

## Documentation principles

Orbit Lab documentation should follow these principles:

### Preserve reasoning

Important decisions must explain why an option was selected and which alternatives were considered.

### Preserve configuration

Experiments and tests must identify the software version, hardware revision, parameters and relevant environmental conditions.

### Preserve evidence

Results should reference logs, measurements, datasets, images, videos or other supporting evidence when applicable.

### Maintain traceability

Requirements, decisions, implementation, tests and evidence should reference one another.

### Remain proportional

Documentation effort should be proportional to the importance, complexity and risk of the work.

Small corrections do not require large reports. Important architectural or hardware decisions require stronger records.

### Remain understandable

Documentation should describe the system clearly without requiring the reader to reconstruct its purpose exclusively from source code or CAD files.

## Source of truth

GitHub is the official source of engineering documentation for Orbit Lab.

Official records include:

* standards;
* requirements;
* engineering decisions;
* architecture documents;
* interfaces;
* experiments;
* test procedures and results;
* component and part records;
* risks;
* reports;
* engineering evidence indexes.

Notion may be used for:

* planning;
* dashboards;
* temporary notes;
* meetings;
* early ideas;
* links to official records.

An important technical decision stored only in Notion is not considered an official engineering record.

## Document organization

General project documentation belongs in the central `docs` repository.

Documentation that depends directly on a subsystem implementation may remain inside the responsible repository.

Examples:

```text
docs repository
├── project-wide standards
├── system requirements
├── system architecture
└── interfaces between subsystems

obc repository
├── OBC requirements
├── kernel decisions
├── driver tests
└── OBC development logs
```

Documents should be linked from the published documentation whenever practical.

## Engineering artifacts

Orbit Lab uses different artifact types for different engineering purposes.

Examples include:

| Type     | Purpose                             |
| -------- | ----------------------------------- |
| `ADR`    | Record an engineering decision      |
| `REQ`    | Define a verifiable requirement     |
| `TEST`   | Verify a requirement                |
| `EXP`    | Investigate an engineering question |
| `IF`     | Define an interface                 |
| `PART`   | Document a designed physical part   |
| `COMP`   | Document a purchased component      |
| `PROC`   | Define a repeatable procedure       |
| `RISK`   | Record and manage a risk            |
| `LOG`    | Record a development session        |
| `REPORT` | Present analysis and conclusions    |

Artifact identifiers are defined by [`ORBIT-STD-002`](orbit-std-002-identification-standard.md).

## Traceability

Related engineering artifacts should reference one another.

Example:

```text
REQ-OBC-0004
    │
    ├── ADR-OBC-0002
    │   Selected implementation approach
    │
    ├── orbit-obc#18
    │   Development task
    │
    ├── TEST-OBC-0007
    │   Verification procedure
    │
    └── test evidence
        Logs and measurements
```

Traceability should make it possible to answer:

* Why does this implementation exist?
* Which requirement requested it?
* Which decision selected the approach?
* Which test verified it?
* Where is the evidence?

## Document lifecycle

Controlled documents should have a status and revision.

Typical lifecycle:

```text
Draft
  ↓
Proposed
  ↓
Under Review
  ↓
Accepted
```

Other possible states include:

* Rejected
* Implemented
* Verified
* Superseded
* Deprecated
* Cancelled

Accepted or obsolete documents should not be deleted simply to remove their history.

Revision and status rules are defined by [`ORBIT-STD-004`](orbit-std-004-revision-control.md).

## Minimum documentation

The required documentation depends on the type of work.

### Small correction

Usually requires:

* commit or pull request;
* explanation of the correction;
* validation when applicable.

### Important software feature

Usually requires:

* requirement or clear objective;
* issue;
* implementation;
* test;
* updated technical documentation.

An ADR is required when an important design decision is made.

### New hardware component

Usually requires:

* component record;
* selection rationale;
* interface information;
* relevant tests.

### New mechanical part

Usually requires:

* part record;
* CAD source;
* material and manufacturing information;
* revision;
* inspection or test.

### Experiment

Usually requires:

* research question;
* configuration;
* procedure;
* raw data;
* results;
* conclusion.

### Verification test

Usually requires:

* requirement under test;
* configuration;
* procedure;
* pass criteria;
* actual result;
* evidence.

## Completion rule

An engineering task should be considered complete when the required combination exists:

```text
work
+ documentation
+ verification
+ evidence
+ traceability
```

Not every task requires every artifact type. The required records depend on the importance and risk of the change.

## Related standards

* [`ORBIT-STD-002`](orbit-std-002-identification-standard.md) — Identification Standard
* [`ORBIT-STD-003`](orbit-std-003-file-naming-standard.md) — File Naming Standard
* [`ORBIT-STD-004`](orbit-std-004-revision-control.md) — Revision Control Standard
* [`ORBIT-STD-005`](orbit-std-005-readme-standard.md) — README Standard
