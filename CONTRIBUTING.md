# Contributing

Thanks for contributing to **Active Multiple**.

## Scope

This project contains KiCad 9 source files for a Eurorack active buffered multiple.
Contributions are welcome for:
- Schematic improvements
- PCB/layout fixes
- Footprint and library cleanup
- Manufacturing output sanity checks
- Documentation updates

## Requirements

- Use **KiCad 9** for edits.
- Keep generated outputs and source changes clearly separated in commits.
- Prefer small, focused pull requests.

## Repository Layout

- `kicad/` - KiCad project sources (`.kicad_pro`, `.kicad_sch`, `.kicad_pcb`)
- `lib/` - local libraries used by the project
- `Outputs/` - fabrication/export artifacts

## Recommended Workflow

1. Create a branch from `main`.
2. Make your change in KiCad 9.
3. Run ERC/DRC and fix or document any remaining warnings.
4. Regenerate affected outputs (if your change impacts fabrication files).
5. Open a pull request with clear notes and screenshots when relevant.

## Design Rules

- Preserve Eurorack power conventions (+12 V / -12 V / GND, 10-pin header orientation).
- Preserve net naming consistency for channels A/B.
- For footprint changes, verify drill sizes, courtyard clearances, and panel/jack alignment.
- Avoid unrelated refactors in the same PR.

## Commit Guidance

Use descriptive commit messages, for example:
- `sch: fix channel B output label`
- `pcb: increase clearance around power header`
- `docs: update BOM and assembly note`

## Pull Request Checklist

Please include:
- What changed and why
- KiCad version used
- ERC status (pass/warnings with explanation)
- DRC status (pass/warnings with explanation)
- Whether `Outputs/` changed
- Screenshots for visible schematic/PCB changes

## Reporting Issues

When filing an issue, include:
- Problem description
- Steps to reproduce
- KiCad version
- Relevant screenshots or logs

## License

By contributing, you agree your contributions are provided under the repository MIT license.