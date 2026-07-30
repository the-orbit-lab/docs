# ORBIT-STD-004 — Revision Control Standard

## Purpose

This standard defines how Orbit Lab controls document versions, physical revisions, artifact status and replacement history.

Its purpose is to ensure that a reader can determine:

* which version is current;
* what changed;
* whether an artifact is approved;
* whether it was replaced;
* which version was used during a test or experiment.

## General principle

An artifact identifier represents the identity of an engineering item.

A revision represents a controlled change to that same item.

Example:

```text
PART-STR-0004 Rev A
PART-STR-0004 Rev B
```

Both revisions represent the same logical part.

A new identifier must be created when the item has a different purpose, responsibility or identity.

## Revision systems

Orbit Lab uses two primary revision systems:

| Artifact category               | Revision format       |
| ------------------------------- | --------------------- |
| Markdown documentation          | Semantic revision     |
| Mechanical parts and assemblies | Letter revision       |
| Electronic boards               | Letter revision       |
| Released software               | Semantic Versioning   |
| Raw experiment and test data    | Immutable run records |

## Document revisions

Controlled Markdown documents use:

```text
MAJOR.MINOR.PATCH
```

Example:

```text
0.1.0
```

### Major revision

Increment the major number when an accepted document receives a change that substantially alters its meaning, requirements or engineering direction.

Examples:

```text
1.0.0 → 2.0.0
```

Possible major changes:

* changing the identifier format;
* changing mandatory documentation rules;
* replacing the principal architecture;
* altering requirement meaning;
* introducing incompatible process rules.

### Minor revision

Increment the minor number when meaningful content is added or modified without completely replacing the document purpose.

Examples:

```text
0.1.0 → 0.2.0
1.0.0 → 1.1.0
```

Possible minor changes:

* adding a new artifact type;
* adding a new subsystem code;
* introducing a new mandatory section;
* expanding procedures;
* changing acceptance criteria.

### Patch revision

Increment the patch number for corrections that do not change the technical meaning.

Examples:

```text
1.0.0 → 1.0.1
```

Possible patch changes:

* correcting spelling;
* fixing broken links;
* correcting formatting;
* clarifying wording without changing intent;
* fixing an incorrect reference.

## Draft versions

Documents under development normally begin at:

```text
0.1.0
```

During drafting:

```text
0.1.0
0.2.0
0.3.0
```

The first accepted version should normally become:

```text
1.0.0
```

Example:

```text
Draft:     0.1.0
Reviewed:  0.3.0
Accepted:  1.0.0
```

## Physical revisions

Mechanical parts, assemblies and electronic boards use uppercase revision letters.

```text
Rev A
Rev B
Rev C
```

Examples:

```text
PART-STR-0004 Rev A
ASSY-ADCS-0001 Rev B
PCB-OBC-0001 Rev C
```

The first manufactured or formally released design should normally be `Rev A`.

Draft CAD iterations before formal release may remain under Git history without receiving a formal revision.

A formal revision should be created when the design is:

* manufactured;
* tested;
* assembled;
* released for integration;
* referenced by another controlled artifact.

## When to increment a physical revision

Increment the revision when the item keeps the same purpose and interface but its implementation changes.

Examples:

* changing wall thickness;
* adjusting a hole diameter;
* changing manufacturing tolerance;
* improving routing on a PCB;
* moving a connector without changing its function;
* reinforcing a bracket.

Example:

```text
PART-STR-0004 Rev A
↓ thicker wall and corrected hole position
PART-STR-0004 Rev B
```

## When to create a new identifier

Create a new identifier when the item is no longer the same logical artifact.

Examples:

* a bracket is replaced by a completely different mounting concept;
* a general-purpose OBC board becomes a dedicated ADCS board;
* an interface changes responsibility;
* a component serves a different system function;
* two versions cannot be treated as revisions of the same item.

Example:

```text
PART-STR-0004
Lower corner bracket

PART-STR-0011
Integrated rail and corner structure
```

The second item receives a new identifier because it represents a different design concept.

## Interchangeability rule

Physical revisions should state whether they are interchangeable.

Possible values:

```text
Fully interchangeable
Conditionally interchangeable
Not interchangeable
```

Example:

```text
Rev B is mechanically interchangeable with Rev A, but requires M3x6 screws instead of M3x5 screws.
```

A revision may keep the same identifier even when not fully interchangeable, but the incompatibility must be documented clearly.

If the design purpose or interfaces change substantially, prefer a new identifier.

## Document status

Controlled documents should use one of the following statuses.

### Draft

The document is being written and is not ready for formal review.

### Proposed

The document is sufficiently complete and is being presented for review.

### Under Review

The document is currently being evaluated.

### Accepted

The document has been approved as an official engineering record.

### Implemented

The decision or requirement described by the document has been implemented.

### Verified

The artifact has been successfully verified through the defined method.

### Rejected

The proposal was evaluated and not accepted.

### Superseded

A newer artifact formally replaces this artifact.

### Deprecated

The artifact remains valid for historical or compatibility purposes but should not be used for new work.

### Cancelled

The artifact was intentionally stopped before completion or implementation.

## Recommended status flows

### Standard or decision

```text
Draft
  ↓
Proposed
  ↓
Under Review
  ↓
Accepted
```

Possible alternative outcomes:

```text
Rejected
Superseded
Deprecated
```

### Requirement

```text
Draft
  ↓
Proposed
  ↓
Accepted
  ↓
Implemented
  ↓
Verified
```

### Test

```text
Draft
  ↓
Ready
  ↓
Executed
  ↓
Passed / Failed / Blocked / Inconclusive
```

Test execution result should normally be stored separately from document status when possible.

### Experiment

```text
Planned
  ↓
In Progress
  ↓
Completed
```

Possible outcomes may include:

```text
Cancelled
Inconclusive
```

### Physical part

```text
Concept
  ↓
Prototype
  ↓
Under Test
  ↓
Approved
```

Possible later states:

```text
Superseded
Deprecated
Rejected
```

## Superseding artifacts

An accepted artifact must not be silently rewritten when a later decision reverses it.

The old artifact should be marked:

```yaml
status: Superseded
superseded_by: ADR-OBC-0011
```

The replacement should reference the previous artifact:

```yaml
supersedes:
  - ADR-OBC-0002
```

Example:

```text
ADR-OBC-0002
Use an ESP32-C3 as the first OBC controller
Status: Superseded
Superseded by: ADR-OBC-0011
```

The old file remains available to preserve the engineering history.

## Rejected artifacts

Rejected proposals must not be deleted solely because they were rejected.

A rejected ADR can explain why an apparently reasonable option was not selected.

Example:

```yaml
status: Rejected
```

The document should include the rejection reason and, when applicable, link to the accepted alternative.

## Deprecated artifacts

Use `Deprecated` when an artifact is still present but should no longer be used for new work.

Examples:

* legacy protocol documentation;
* old development procedure;
* supported but discouraged component;
* compatibility interface.

Deprecated artifacts should indicate:

* why they are deprecated;
* the recommended replacement;
* the expected removal or review condition.

## Cancelled artifacts

Use `Cancelled` when planned work is intentionally stopped before completion.

A cancelled artifact should record:

* why it was cancelled;
* whether any results remain useful;
* which work replaces it;
* whether its identifier remains reserved.

Identifiers from cancelled artifacts must not be reused.

## Revision history section

Accepted documents should include a revision history when meaningful changes begin accumulating.

Template:

```md
## Revision history

| Revision | Date | Status | Description |
|---|---|---|---|
| 0.1.0 | YYYY-MM-DD | Draft | Initial draft |
| 0.2.0 | YYYY-MM-DD | Proposed | Added subsystem rules |
| 1.0.0 | YYYY-MM-DD | Accepted | First accepted release |
```

Minor spelling corrections do not need a detailed revision-history entry when Git already records them, unless the document is externally released.

## Physical revision history

Part, assembly and PCB records should include:

```md
## Revision history

| Revision | Date | Description | Interchangeability |
|---|---|---|---|
| A | YYYY-MM-DD | Initial prototype | — |
| B | YYYY-MM-DD | Increased wall thickness | Fully interchangeable |
```

## Tests and configuration references

Every executed test must record the exact configuration used.

For software:

```text
Repository
Commit hash
Release
Branch, when relevant
Configuration
```

For hardware:

```text
Part identifier
Part revision
PCB identifier
PCB revision
Component model
Assembly revision
```

Example:

```text
Firmware commit: 8d31a3f
OBC board: PCB-OBC-0001 Rev A
Structure: ASSY-STR-0001 Rev B
Reaction wheel: ASSY-ADCS-0002 Rev A
```

A test result is not considered fully reproducible when its tested revisions are unknown.

## Experiments and immutable runs

Raw experiment data should not be edited after collection.

Corrections or processing should produce new files.

Example:

```text
Raw:
2026-07-29-exp-adcs-0001-wheel-speed-run-01.csv

Processed:
2026-07-29-exp-adcs-0001-wheel-speed-run-01-processed.csv
```

The processing procedure or script must be recorded.

Do not replace raw measurements with cleaned data under the same filename.

## Software releases

Released software should use Semantic Versioning when practical:

```text
MAJOR.MINOR.PATCH
```

Example:

```text
v0.1.0
v0.2.0
v1.0.0
```

Recommended interpretation:

* `MAJOR`: incompatible behavior or interface change;
* `MINOR`: backward-compatible feature;
* `PATCH`: backward-compatible correction.

Early experimental software may remain in `0.x.y`.

A software release version is separate from a documentation revision.

Example:

```text
Software release: v0.3.0
Test document revision: 1.1.0
```

## Git and revision control

Git preserves change history but does not replace formal engineering revisions.

Git commits answer:

```text
What changed in the repository?
```

Formal revisions answer:

```text
Which version of this controlled artifact was released, tested or approved?
```

Use both together.

## Pull request requirements

A pull request that changes an accepted controlled artifact should explain:

* what changed;
* why it changed;
* whether the revision must be incremented;
* whether related artifacts are affected;
* whether previous test results remain valid;
* whether the change breaks compatibility.

## Change impact

Before changing an accepted artifact, evaluate its impact on:

* requirements;
* interfaces;
* tests;
* procedures;
* CAD or PCB files;
* software;
* documentation links;
* manufacturing;
* existing hardware;
* previous evidence.

A revision should not be approved until affected records are identified.

## Baselines

A baseline is an approved set of compatible artifact revisions.

Example:

```text
Orbit Lab Prototype Baseline 0.1

OBC firmware: v0.2.0
PCB-OBC-0001: Rev A
ASSY-STR-0001: Rev B
ASSY-ADCS-0001: Rev A
IF-OBC-EPS-0001: revision 1.0.0
```

Baselines are useful before:

* integration tests;
* public demonstrations;
* long-duration tests;
* manufacturing;
* major project reports.

A baseline should not be changed after testing. A new baseline should be created instead.

## Core rules

1. Artifact identifiers must never be reused.
2. Accepted or rejected history must not be silently deleted.
3. A revision must represent the same logical artifact.
4. A new engineering identity requires a new identifier.
5. Tests must record the exact revisions used.
6. Raw test and experiment data must remain immutable.
7. Superseded artifacts must point to their replacements.
8. Revision changes must be proportional to their technical impact.

## Core principle

> Git records every change; formal revisions identify the exact engineering configuration that was designed, built or tested.
