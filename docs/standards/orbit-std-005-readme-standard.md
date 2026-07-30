# ORBIT-STD-002 — README Standard

## Purpose

This standard defines the recommended structure and content of README files across Orbit Lab repositories.

A README should introduce the project, explain its purpose and direct the reader to the appropriate technical documentation.

It should not replace the complete engineering documentation.

## Required sections

### Title

Use the official project name.

```md
# Orbit Tools
```

### Description

Write one or two sentences explaining what the project does and its role inside Orbit Lab.

```md
Orbit Tools is a Rust toolkit for orbital, communication and mission analysis used by the Orbit Lab CubeSat testbed.
```

### Purpose

Explain the problem solved by the project and its main responsibility.

### Status

State the current development phase.

Recommended values:

* Planning
* Research
* Prototype
* Active development
* Experimental
* Stable
* Archived

### Usage

Include only the commands or steps required to build, run, test or inspect the project.

### Documentation

Link to the published documentation and relevant documentation directories.

### License

State the applicable license and link to the license file.

## Optional sections

Optional sections should only be included when they help the reader understand or use the project.

### Theory and Mathematics

Use this section when the project depends on mathematical, physical or engineering models.

It may include:

* equations;
* variable definitions;
* measurement units;
* assumptions;
* model limitations;
* physical interpretation.

The README should include only the mathematics required to understand the project.

Long derivations, validation results and complete mathematical models should remain in the technical documentation.

### How It Works

Use this section to explain the main logical flow of the system.

It may include:

* processing steps;
* data flow;
* state transitions;
* algorithm overview;
* simplified diagrams;
* relationships between inputs and outputs.

This section should explain the system conceptually without describing every source file.

### Architecture

Use this section when the repository contains multiple important modules or services.

Provide only a short overview and link to the complete architecture documentation.

### Example

Use this section when a short input and output example helps explain the project.

### Hardware

Use this section when the repository depends on physical components, boards, instruments or manufacturing equipment.

### Development

Use this section for contributor-specific commands such as formatting, linting and testing.

### Roadmap

Use this section only for a short summary of the next major milestones.

The full roadmap should remain in the technical documentation or GitHub Projects.

### Contributing

Link to the organization contribution guide instead of duplicating all contribution rules.

## Recommended order

A README may follow this order:

```text
Title
Description
Purpose
Status
Theory and Mathematics
How It Works
Usage
Example
Documentation
Development
Contributing
License
```

Optional sections may be omitted or reordered when another structure makes the project easier to understand.

## Content rules

A README should:

* explain what the project does;
* explain why the project exists;
* show how to use or inspect it;
* explain essential mathematics and logic when relevant;
* link to deeper documentation;
* remain understandable without requiring the reader to inspect the source code first.

A README should not:

* reproduce the complete project documentation;
* list every file and directory without a clear reason;
* include every requirement or decision;
* contain complete experiment or test reports;
* include long mathematical derivations;
* describe unfinished functionality as implemented;
* show commands or links that do not work.

## Core principle

> The README introduces the project, explains its essential logic and directs the reader to deeper documentation.
