# ORBIT-STD-003 — File Naming Standard

## Purpose

This standard defines how files and directories are named across Orbit Lab repositories.

The objective is to keep engineering artifacts predictable, searchable and easy to identify without opening them.

## General rules

File and directory names should:

* use lowercase letters;
* use hyphens between words;
* avoid spaces;
* avoid accented characters;
* avoid unnecessary abbreviations;
* include the artifact identifier when applicable;
* describe the content clearly;
* remain stable after publication.

Use:

```text
adr-obc-0001-select-main-controller.md
```

Avoid:

```text
ADR final.md
controllerDecisionNEW.md
document-2.md
final-final-v2.md
```

## Markdown documents

Controlled engineering documents must follow:

```text
identifier-short-title.md
```

Example:

```text
adr-obc-0001-select-rust.md
```

The identifier must follow `ORBIT-STD-002`.

Examples:

```text
req-obc-0001-watchdog-supervision.md
test-adcs-0003-wheel-speed-stability.md
exp-com-0001-radio-range-evaluation.md
if-obc-eps-0001-i2c-interface.md
part-str-0004-lower-corner-bracket.md
risk-sys-0001-component-unavailability.md
```

The filename identifier should be lowercase even though the identifier inside the document is uppercase.

Example:

```text
Filename:
adr-obc-0001-select-rust.md

Document ID:
ADR-OBC-0001
```

## Orbit Lab standards

Standards must follow:

```text
orbit-std-number-short-title.md
```

Examples:

```text
orbit-std-001-documentation-standard.md
orbit-std-002-identification-standard.md
orbit-std-003-file-naming-standard.md
orbit-std-004-revision-control.md
orbit-std-005-readme-standard.md
```

## Templates

Template filenames should describe the artifact they create.

Format:

```text
artifact-name-template.md
```

Examples:

```text
adr-template.md
requirement-template.md
verification-test-template.md
experiment-template.md
interface-template.md
engineering-log-template.md
```

Template filenames do not receive artifact identifiers because templates are not engineering records.

## Index files

A directory documented by MkDocs should normally contain:

```text
index.md
```

The `index.md` file introduces the section and links to its relevant contents.

Examples:

```text
docs/standards/index.md
docs/templates/index.md
docs/guides/index.md
```

Avoid names such as:

```text
standards-home.md
templates-main.md
folder-description.md
```

## Directory names

Directory names should use lowercase kebab-case.

Examples:

```text
development-log/
ground-station/
flight-software/
hardware-in-the-loop/
test-evidence/
```

Avoid:

```text
DevelopmentLog/
ground_station/
Flight Software/
HILFiles/
```

Short and widely recognized subsystem names may be used when their meaning is defined by `ORBIT-STD-002`.

Examples:

```text
obc/
adcs/
eps/
com/
```

## Source code files

Source code filenames should follow the conventions of their language and ecosystem.

Examples:

```text
Rust:
reaction_wheel.rs
fault_manager.rs

Python:
telemetry_decoder.py
risk_analysis.py

C:
watchdog_supervisor.c
watchdog_supervisor.h
```

This standard does not override language-specific naming conventions.

## CAD and mechanical files

Mechanical files must include:

* part or assembly identifier;
* revision;
* short descriptive title;
* file extension.

Format:

```text
identifier-rev-x-short-title.extension
```

Examples:

```text
part-str-0004-rev-a-lower-corner-bracket.step
part-str-0004-rev-a-lower-corner-bracket.stl
part-str-0004-rev-a-lower-corner-bracket.pdf
assy-adcs-0001-rev-b-reaction-wheel.step
```

The same revision must be used across equivalent exports generated from the same source model.

Example:

```text
part-str-0004-rev-b-lower-corner-bracket.step
part-str-0004-rev-b-lower-corner-bracket.stl
part-str-0004-rev-b-lower-corner-bracket.pdf
```

Do not use:

```text
corner-final.step
corner-fixed.stl
corner-new-final-v3.step
```

## Electronic design files

PCB and schematic outputs should include the board identifier and revision.

Examples:

```text
pcb-obc-0001-rev-a-main-board.kicad_pcb
pcb-obc-0001-rev-a-main-board.kicad_sch
pcb-obc-0001-rev-a-gerbers.zip
pcb-obc-0001-rev-a-bom.csv
pcb-obc-0001-rev-a-pick-and-place.csv
```

Project-specific source files may follow the conventions required by the EDA tool, but exported files must remain identifiable.

## Experiment data

Experiment files must include:

* date;
* experiment identifier;
* short description;
* optional run number.

Recommended format:

```text
yyyy-mm-dd-experiment-id-description-run-number.extension
```

Examples:

```text
2026-07-29-exp-adcs-0001-wheel-speed-run-01.csv
2026-07-29-exp-adcs-0001-wheel-speed-run-02.csv
2026-07-29-exp-com-0002-radio-range-run-01.json
```

The run number may be omitted when only one run exists.

## Test evidence

Test evidence must include:

* date;
* test identifier;
* evidence description.

Format:

```text
yyyy-mm-dd-test-id-description.extension
```

Examples:

```text
2026-07-29-test-obc-0001-first-boot-serial.log
2026-07-29-test-obc-0001-power-cycle-video.mp4
2026-07-29-test-adcs-0003-speed-response.csv
2026-07-29-test-eps-0002-current-measurement.png
```

## Engineering logs

Engineering log filenames must follow:

```text
log-subsystem-yyyy-mm-dd-short-title.md
```

Examples:

```text
log-obc-2026-07-29-first-uart-bring-up.md
log-adcs-2026-07-30-wheel-balancing.md
log-str-2026-08-02-corner-bracket-print.md
```

When multiple logs exist for the same subsystem and date, add a sequence:

```text
log-obc-2026-07-29-01-uart-configuration.md
log-obc-2026-07-29-02-timer-interrupt.md
```

## Reports

Reports must follow the controlled artifact format:

```text
report-subsystem-number-short-title.md
```

Examples:

```text
report-obc-0001-watchdog-verification.md
report-adcs-0002-reaction-wheel-analysis.md
report-sys-0001-prototype-integration.md
```

Exported report files should preserve the same basename:

```text
report-adcs-0002-reaction-wheel-analysis.md
report-adcs-0002-reaction-wheel-analysis.pdf
```

## Images and diagrams

Images should describe their contents and, when applicable, reference the related artifact.

Examples:

```text
obc-system-architecture.svg
adcs-control-loop.svg
if-obc-eps-0001-pinout.png
part-str-0004-rev-a-dimensions.png
test-obc-0001-reset-waveform.png
```

Avoid generic names:

```text
image1.png
screenshot.png
diagram-final.png
photo-new.jpg
```

## Dates

Dates in filenames must use ISO 8601 format:

```text
YYYY-MM-DD
```

Example:

```text
2026-07-29
```

Do not use:

```text
29-07-2026
07-29-2026
29-july-2026
```

## Sequence numbers

Artifact sequence numbers must use four digits:

```text
0001
0002
0003
```

Do not switch between:

```text
1
01
001
0001
```

The four-digit format keeps filenames naturally ordered and provides enough capacity for long-term development.

## File extensions

Use lowercase file extensions.

Prefer:

```text
.md
.csv
.json
.yaml
.png
.svg
.step
.stl
.pdf
```

Avoid:

```text
.MD
.CSV
.PNG
.STEP
```

## Renaming files

Published files should not be renamed without a clear reason because renaming may break:

* documentation links;
* references from issues;
* external links;
* MkDocs navigation;
* traceability records.

When renaming is necessary:

1. update all internal links;
2. update `mkdocs.yml`;
3. update related registers;
4. search the repository for the old path;
5. validate with `mkdocs build --strict`;
6. explain the reason in the pull request.

## Prohibited naming patterns

The following patterns should not be used:

```text
final
final-final
latest
new
old
copy
fixed
correct
version2
test123
document
untitled
```

Revision and status information must be managed according to `ORBIT-STD-004`, not through informal filename suffixes.

## Examples

### Decision

```text
adr-obc-0001-select-main-controller.md
```

### Requirement

```text
req-com-0004-telemetry-transmission-rate.md
```

### Verification test

```text
test-com-0007-telemetry-rate-verification.md
```

### Experiment

```text
exp-adcs-0003-flywheel-inertia-evaluation.md
```

### Interface

```text
if-obc-com-0001-uart-radio-interface.md
```

### Mechanical part

```text
part-str-0012-rev-b-upper-panel.step
```

### Test evidence

```text
2026-07-29-test-com-0007-telemetry-capture.csv
```

## Core principle

> A filename should identify the artifact before the file is opened.
