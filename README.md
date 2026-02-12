# Configs Submodule

This folder is a Git submodule that stores generated outputs and input CSVs for
AXOS variable configuration runs.

## Structure

Typical structure:

```
configs/
  TRLY2501/
    csvs/        # source CSV files
    configs/     # generated JSON per plcVariableName
    processed_variables.csv
    mb_handler_summary.txt
```

## How To Generate

From the repository root:

```powershell
python process_csv.py --input configs/TRLY2501/csvs/<input.csv> --outdir configs/TRLY2501/DEVICE
```

This will create:
- `configs/TRLY2501/DEVICE/processed_variables.csv`
- `configs/TRLY2501/DEVICE/mb_handler_summary.txt`
- `configs/TRLY2501/DEVICE/configs/*.json`

## Validation

```powershell
python validate_outputs.py --base-dir configs --max-mbhandler 30
```

## Notes

- This submodule is intended to version the generated outputs and input CSVs.
- Do not commit `.tmp`, `.pip-cache`, `.pip-tmp`, or local venvs; they are ignored
  by the parent repository.
