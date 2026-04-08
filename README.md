# Alchemy (legacy shell placeholder release)

This repository packages the original **shell-script implementation** of the Alchemy workflow for archival and reference purposes.

Citation - Assessing Metal Ion Assignment Accuracy in Protein Data Bank Models via Elemental Spectroscopy - Edward H. Snell, Geoffrey W. Grime, Samuel M. Webb, Catia Costa, M. Elizabeth Snell, John F. Hunt, Liang Tong, Gaetano T. Montelione, Rachel Zigweid, Bart L. Staker, Peter J. Myler, and Elspeth F. Garman (2026)

Contact - esnell@buffalo.edu

## Status

**Important:** this repository is being deposited as a **placeholder release**.

- The code here reflects the original shell-script workflow used during early development.
- A newer **Python implementation is under active development** and is intended to supersede this version.
- The shell scripts are retained to document the historical workflow, expected inputs/outputs, and overall pipeline logic.
- This repository should therefore be treated as a **legacy prototype**, not as a polished production release.

## What is included

The repository contains four legacy shell scripts and one CCP4mg template file.

Assistant — downloads coordinate files from RCSB and MTZ files from PDB-REDO.
Alchemy — generates maps with CCP4 tools and runs `edstats`.
Analysis — extracts common metal-site statistics from Alchemy outputs.
Autoplot — prepares CCP4mg image-generation scripts and renders figures.
default.mgpic — CCP4mg picture template used by `Autoplot`.

## Intended use

This deposit is appropriate for:

- documenting the workflow used in the current study,
- preserving the original shell-based pipeline,
- providing a reference point for future Python development.

This deposit is **not** intended to imply that the shell implementation is feature-complete, fully portable, or actively maintained.

## External dependencies

The shell workflow expects several external tools to already be installed and available on the system path:

- `bash`
- `wget`
- `gunzip`
- CCP4 utilities, including at minimum:
  - `fft`
  - `edstats`
  - `mtzdump`
- `ccp4mg` (for `Autoplot`)
- `bc`
- standard Unix text utilities such as `grep`, `awk`, `sed`, `sort`, and `cut`

Internet access is only required for the `Assistant` download step. 

## Repository layout

```text
alchemy_github_repo/
├─ README.md
├─ LICENSE.md
├─ CITATION.cff
├─ CHANGELOG.md
├─ CONTRIBUTING.md
├─ .gitignore
├─ pyproject.toml
├─ docs/
│  ├─ user_guide.md
│  └─ development_status.md
├─ examples/
│  └─ file.list.example
├─ scripts/
│  └─ legacy_shell/
│     ├─ Assistant
│     ├─ Alchemy
│     ├─ Analysis
│     └─ Autoplot
└─ templates/
   └─ default.mgpic
```

## Quick start

Create a comma-separated file of PDB identifiers, for example:

```text
1abc,2def,3ghi
```

Then run the legacy scripts in sequence:

```bash
./scripts/Assistant -f examples/file.list.example
./scripts/Alchemy -f examples/file.list.example
./scripts/Analysis
./scripts/Autoplot -f Metal_data_difference_sorted
```

## Caveats

Because this repository is a placeholder deposit:

- command-line behavior is preserved as closely as possible to the original scripts,
- code style is intentionally conservative,
- known rough edges and historical assumptions are documented rather than fully rewritten,
- output parsing may depend on specific tool versions and file formatting,
- no warranty is made that the scripts will run unchanged on all systems.

## Recommended citation language

A suggested statement for methods or software availability sections:

> The original shell-script implementation of the Alchemy workflow has been archived in a public GitHub repository as a legacy placeholder release. A more robust Python implementation is under active development. Citation - Assessing Metal Ion Assignment Accuracy in Protein Data Bank Models via Elemental Spectroscopy - Edward H. Snell, Geoffrey W. Grime, Samuel M. Webb, Catia Costa, M. Elizabeth Snell, John F. Hunt, Liang Tong, Gaetano T. Montelione, Rachel Zigweid, Bart L. Staker, Peter J. Myler, and Elspeth F. Garman (2026)


## License

MIT licence

## Contact

For questions about scientific use, interpretation, or the migration to Python, please use the repository issue tracker or update the contact details in `CITATION.cff` before publication.
