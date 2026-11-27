# Computational Results

## Overview

This directory documents computational research associated with the Phase I theoretical nonspatial mathematical framework.

## Datasets

| File | Contents |
| --- | --- |
| `pam_sweep.csv` | 20 simulations over δ ∈ [0.2, 1.5] × λ ∈ [0.2, 1.2]: peak inflammation, crossover onset and duration, pre-clearance window, bound checks. |
| `pam_threshold_mechanism.csv` | Seven λ values at δ = 0.2, tracing the injury-difference maximum toward the grazing point. |
| `pam_clearance_recruitment_grid.csv` | Crossover duration across 176 (δ, λ) pairs. |
| `pam_clearance_recruitment_thresholds.csv` | Root λ*, plus first and second time-derivatives at the root, for δ = 0.15, 0.20, 0.25. |
| `pam_grazing_scaling.csv`, `pam_scaling_extended.csv`, `pam_small_gap_verification.csv` | Near-threshold crossover duration versus distance to λ*, including the twelve-point fit set. |
| `pam_scaling_fit_residuals.csv` | Through-origin fit of duration against √(λ* − λ): predicted values, residuals, relative residuals. |
| `pam_solver_comparison.csv` | LSODA versus DOP853 across solver tolerance settings. |
| `pam_grazing_verification.csv` | Verification runs at the grazing point. |

Scientific figures and research notes are held in the local research archive.

## Scientific Interpretation

The computational observations are conditional on the mathematical assumptions and hypothetical model parameters.

They do not constitute experimental findings, validated biological predictions, or clinical evidence.

## Reproducibility Status

SHA-256 checksums for every dataset above are recorded in [`SHA256SUMS.txt`](SHA256SUMS.txt), so a file obtained from the author can be confirmed as the file that produced the reported results.

File integrity verification does not establish computational reproducibility or scientific validity.

Publication review and final repository-level verification remain outstanding. Independent computational reproduction has not been established.

## Supporting Documentation

- [Mathematical framework](../docs/mathematical-framework.md)
- [Research questions](../docs/research-questions.md)
- [Numerical verification](../tests/README.md)
- [Project overview](../README.md)

---

*Independent computational biology research by Kenya S. Montagueo.*

*Theoretical research; not peer reviewed or experimentally validated.*
