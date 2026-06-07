# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Single-file Python CLI tool (`xlsxtotxt`) that converts `.xlsx` files to tab-separated `.txt` files. No build system, no tests, no package manager config — just a standalone executable script with a `#!/usr/bin/env python3` shebang.

**Dependency:** `openpyxl` (install via `pip install openpyxl`).

## Running

```bash
./xlsxtotxt file.xlsx              # writes file.txt
./xlsxtotxt file.xlsx --stdout     # writes to stdout
./xlsxtotxt file.xlsx -o out.txt   # custom output path
./xlsxtotxt *.xlsx                 # batch convert
```

## Architecture

Everything lives in the single `xlsxtotxt` file (no `.py` extension — it's meant to be run directly):

- `format_cell()` — value-to-string conversion: handles None, datetime types, whole-number floats, and in-cell newline flattening.
- `convert()` — reads workbook with openpyxl in `read_only`/`data_only` mode, iterates all sheets, writes tab-separated output.
- `main()` — argparse CLI entry point.
