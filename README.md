# Orbit Lab Documentation

Official engineering documentation for **Orbit Lab**, a CubeSat testbed project focused on embedded systems, flight software, attitude control, communications and mission analysis.

The documentation records the requirements, decisions, interfaces, experiments, tests and results produced throughout the project.

## Documentation

* [Standards](docs/standards/) — Project documentation and identification rules
* [Guides](docs/guides/) — Instructions for creating and maintaining records
* [Templates](docs/templates/) — Templates for decisions, tests, experiments and other artifacts
* [Registers](docs/registers/) — Indexes of controlled engineering documents
* [Requirements](docs/requirements/) — System and subsystem requirements
* [Architecture](docs/architecture/) — System structure and technical design
* [Decisions](docs/decisions/) — Engineering and architecture decisions
* [Interfaces](docs/interfaces/) — Connections between systems and components
* [Experiments](docs/experiments/) — Engineering investigations and collected results
* [Tests](docs/tests/) — Verification procedures and test results
* [Risks](docs/risks/) — Identified technical and project risks
* [Reports](docs/reports/) — Analyses, conclusions and engineering reports

## Website

The published documentation is available at:

**https://orbit-lab.github.io/docs/**

## Local development

Install the dependencies:

```bash
python3 -m pip install -r requirements.txt
```

Start the local documentation server:

```bash
mkdocs serve
```

Open `http://127.0.0.1:8000`.

Before submitting changes, validate the documentation:

```bash
mkdocs build --strict
```

## License

The original documentation, diagrams and templates in this repository are licensed under the **Creative Commons Attribution 4.0 International License**.

See [`LICENSE.md`](LICENSE.md) for more information.
