# Readme

This repository contains the R script and data used for the analysis reported in the paper "When Sen's slope is exactly zero: Mann–Kendall trend inference for zero-inflated series and a two-part alternative" (A. U. Tosun and F. Karaman).

## Data

The `data/` folder contains the lists of the 35 USGS streamflow gauges and 61 GHCN-Daily precipitation stations used in the paper, and their monthly series (`streamflow_monthly.csv`, `precipitation_monthly.csv`). These files are provided for reference. The script does not read them: on the first run it downloads the daily data itself from the USGS (with the *dataRetrieval* package) and from the NOAA GHCN-Daily server, and stores them in a local cache.

## Script

| Step | Purpose |
|---|---|
| Step 00 | Numerical check of Theorem 1 (5000 simulated series) |
| Step 01 | Baseline simulation: share of zero Sen slopes, efficiency of MK, size of the exact and mid-p two-part tests |
| Step 02 | Comparison with six competing tests (size and size-adjusted power) and accuracy of the expected-value trend estimators |
| Step 03 | Real data: downloads and analyses the USGS streamflow and GHCN-Daily precipitation series |
| Step 04 | Serial dependence (n = 64): naive, Hamed–Rao and block-permutation versions of the tests |
| Step 05 | Dependence-robust (block-permutation) tests for the real series |
| Step 06 | Draws all figures |
| Step 07 | Streamflow data audit and sensitivity analyses (record gaps, rounding, dam-regulated gauges) |
| Step 08 | Effect sizes with 95% intervals for the real series, and Tables 1–3 |
| Step 09 | Serial dependence at n = 30 and n = 120 |
| Step 10 | Summary of relative power, sites by state and region, and the files in `data/` |

## Figures

The `figures/` folder contains all figures as PDF files.

## Notes

- Required packages: parallel, survival, ggplot2, scales and dataRetrieval.
- The script uses fixed random seeds, so results are exactly reproducible.
- Steps 01, 02, 04, 05 and 09 are the most computationally expensive (hours, depending on hardware). They use caching and checkpointing: if interrupted, simply re-run the script and it will resume from the last completed cell. On later runs only the tables and figures are rebuilt.
