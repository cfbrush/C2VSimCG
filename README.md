# C2VSimCG — tracked modifications

Git repository tracking proposed corrections and refinements to DWR's **C2VSimCG** IWFM model
(**C2VSimCG v2025**, WY1974-2015, IWFM 2025.0.1747; DWR public draft).

The base commit (tag `C2VSimCG_v2025`) is the unmodified DWR release. Every later commit is **exactly one
suggested change**, tagged `C2VSimCG_v2025+cbN`, so a reviewer can inspect each as a single diff and
accept or reject items individually. See **CHANGES.md** for the tag → change map and the review recipe.

## Layout

| path | contents |
|---|---|
| `C2VSimCG/` | the model (Preprocessor, Simulation, Budget, ZBudget, gis) — as released by DWR plus committed changes |
| `Log.txt` | DWR-style version log; one row per commit (`Version,Time,Date,IWFM_version,comment`) |
| `CHANGES.md` | tag → one-line description → files touched → depends-on → status |

Not tracked (see `.gitignore`): `C2VSimCG/bin/` (IWFM executables — obtain the version named in
Log.txt from DWR), `C2VSimCG/Excel/` (post-processing workbooks), `C2VSimCG/Results/`,
`*.out`, `*.hdf`, `*.bud` (model outputs). Copy the DWR release's `bin/` folder into
`C2VSimCG/bin/` to run the model.


## Running

From `C2VSimCG/`: `Run_Model.bat` (Preprocessor → Simulation → Budget → ZBudget), or `Simulation\RUN_SIMULATION_Parallel.bat` for the simulation only. A full run takes about 10 minutes (monthly time step). Outputs go to `Results/`.

## Conventions

- Version string: DWR version + `+cbN` (N = change number); the same string names the git tag
  (spaces replaced by `_`).
- Each change commit touches only the model files needed for that change plus `Log.txt` and
  `CHANGES.md`; commit body follows Issue / Resolution / Files & parameters / Result / Re-calibration.
- Every committed change was run to completion cumulatively on top of the previous commits.
- Line endings are never converted (`.gitattributes: * -text`) — IWFM inputs stay byte-exact.

Charles Brush, Hydrolytics LLC.
