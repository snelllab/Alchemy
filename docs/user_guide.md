# User guide

## Purpose of this repository

This repository preserves the original shell-based Alchemy workflow in a form suitable for GitHub deposition. It is best understood as a documented historical implementation rather than a finished software product.

## Workflow overview

The original notes describe four main steps: downloading files, running map/statistics generation, extracting metal-centered information, and generating CCP4mg visualizations. fileciteturn0file0

### 1. Assistant

`Assistant` downloads:

- compressed PDB coordinate files from RCSB,
- compressed `_0cyc.mtz` files from PDB-REDO,
- and then uncompresses them into the working directory.

Example:

```bash
./scripts/legacy_shell/Assistant -f my_ids.list
```

The input file should contain a comma-separated list of 4-character PDB identifiers.

### 2. Alchemy

`Alchemy` uses CCP4 tools to:

- inspect the MTZ file,
- calculate observed and difference maps,
- optionally calculate an anomalous map,
- run `edstats`,
- write RSZD-annotated PDB output and statistics files.

Example:

```bash
./scripts/legacy_shell/Alchemy -f my_ids.list
```

### 3. Analysis

`Analysis` scans `*_stats.out` files and writes grouped outputs for common metals and selected uncommon metals.

Example:

```bash
./scripts/legacy_shell/Analysis
```

### 4. Autoplot

`Autoplot` reads an analysis output file and uses `default.mgpic` to generate CCP4mg rendering scripts and image files.

Example:

```bash
./scripts/legacy_shell/Autoplot -f Metal_data_difference_sorted
```

## Known assumptions

The shell scripts assume:

- execution from a working directory containing all expected inputs,
- fixed file naming conventions,
- standard CCP4 command-line behavior,
- output formatting compatible with the original parsing logic,
- a Unix-like environment.

## Recommended framing for public release

Suggested wording:

> This repository archives the original shell-script version of Alchemy. It is retained to document the early workflow used in the study and to provide continuity while the actively developed Python implementation matures.
