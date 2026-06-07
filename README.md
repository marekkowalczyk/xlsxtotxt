# xlsxtotxt

Convert `.xlsx` files (all sheets) to readable tab-separated `.txt` files.

## Why

Spreadsheets are opaque to plain-text tools (`grep`, `diff`, `git`). This script dumps every sheet into a single `.txt` file you can search, pipe, and version-control.

## Requirements

- Python 3
- [openpyxl](https://pypi.org/project/openpyxl/) (`pip install openpyxl`)

## Usage

```
xlsxtotxt file.xlsx              # writes file.txt next to the source
xlsxtotxt file.xlsx -o out.txt   # custom output path
xlsxtotxt --stdout file.xlsx     # pipe to terminal
xlsxtotxt *.xlsx                 # batch convert
```

## Output format

- One section per sheet, headed by `=== Sheet: <name> ===`
- Tab-separated columns, one row per line
- In-cell newlines flattened to literal `\n`
- Whole-number floats rendered as integers (`1` not `1.0`)
- Dates rendered as ISO 8601

## License

MIT
