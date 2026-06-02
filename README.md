# PCAA Reproducibility Artifact

This artifact recalculates the experimental results with an epoch-rotating balanced ring construction.

## Ring construction
Target ring size: 64. For each epoch, active staff are assigned to shared ring pools. Ring pools are refreshed per epoch and filled with graph neighbors before random active decoys. This replaces staff-local ego rings and reduces ring-identifier leakage.

## Data
- `raw_data/prime_ring_ehealth_access_log.csv`
- `raw_data/prime_ring_ehealth_staff_graph_edges.csv`

## Run all tables
```bash
python scripts/run_all.py
```
All outputs are written to `output/`.

## Run one table
```bash
python scripts/tables/table_01_dataset_summary.py
python scripts/tables/table_02_workloads.py
python scripts/tables/table_03_recovery_support.py
python scripts/tables/table_04_key_update.py
python scripts/tables/table_05_latency.py
python scripts/tables/table_06_sizes.py
python scripts/tables/table_07_recovery_latency.py
python scripts/tables/table_08_unlinkability.py
python scripts/tables/table_09_residual_sources.py
python scripts/tables/table_10_ablation.py
python scripts/tables/table_11_scalability.py
```
Each command writes its CSV and LaTeX table to `output/`.

## Algorithms executed
`pcaa_core.py` contains the trace-replay implementations of `Setup`, `IssuerKeyGen`, `Enroll`, `Issue`, `Aggregate`, `EpochUpdate`, `Show`, `Verify`, `Revoke`, and `Recover`. `algorithm_run_log.json` records call counts.

## Ring policy
Target ring size is `|R|=64`. Rings are epoch-rotating shared pools. Graph neighbors are used before active decoy fill. This avoids staff-local ego-ring leakage.

## Outputs
- `output/*.csv`: numeric tables
- `output/*.tex`: three-line LaTeX tables
- `output/all_tables.tex`: all LaTeX tables
- `output/table_index.csv`: output map
- `output/algorithm_run_log.json`: algorithm counts
- `output/MANIFEST.json`: input and output hashes
