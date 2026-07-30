# Engineering Templates

These templates provide reusable structures for Orbit Lab engineering records.

Before creating an artifact:

1. select the appropriate template;
2. copy it to the correct documentation directory;
3. assign the next available identifier;
4. rename the file according to the File Naming Standard;
5. replace all placeholder content;
6. update the corresponding register;
7. validate the documentation;
8. open a pull request.

Do not edit a template to record real engineering work. Always create a copy.

## Available templates

| Template                                                    | Use                                      |
| ----------------------------------------------------------- | ---------------------------------------- |
| [ADR Template](adr-template.md)                             | Record an important engineering decision |
| [Requirement Template](requirement-template.md)             | Define a verifiable system condition     |
| [Verification Test Template](verification-test-template.md) | Verify one or more requirements          |
| [Experiment Template](experiment-template.md)               | Investigate an engineering question      |
| [Interface Template](interface-template.md)                 | Define interaction between systems       |
| [Engineering Log Template](engineering-log-template.md)     | Record a meaningful development session  |

## Example

To create an OBC decision:

```bash
cp docs/templates/adr-template.md \
  docs/decisions/adr-obc-0001-select-main-controller.md
```

Then replace:

```text
ADR-SUBSYSTEM-0000
```

with:

```text
ADR-OBC-0001
```

## Related documentation

* [Engineering Artifact Types](../guides/engineering-artifact-types.md)
* [Identification Standard](../standards/orbit-std-002-identification-standard.md)
* [File Naming Standard](../standards/orbit-std-003-file-naming-standard.md)
* [Revision Control Standard](../standards/orbit-std-004-revision-control.md)
