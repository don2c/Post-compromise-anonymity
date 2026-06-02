# PCAA Reproducibility Artifact

This artifact recalculates the experimental results with an epoch-rotating balanced ring construction.

## Ring construction
Target ring size: 64. For each epoch, active staff are assigned to shared ring pools. Ring pools are refreshed per epoch and filled with graph neighbors before random active decoys. This replaces staff-local ego rings and reduces ring-identifier leakage.

## Reproduction
```bash
python scripts/run_pcaa_ring_recalc.py
```

## Outputs
- results/tables.tex: LaTeX booktabs tables.
- results/*.csv: numerical tables.
- results/experimental_results_section.tex: compact result text.
- MANIFEST.json: input hashes, seed, and model notes.

Cryptographic timings use the deterministic cost model stated in MANIFEST.json. Replace with measured library timings for final deployment claims.
