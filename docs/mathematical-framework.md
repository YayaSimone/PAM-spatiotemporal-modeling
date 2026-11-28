# Mathematical Framework

**Independent Computational Biology Research | 2026–Present**

**Researcher:** Kenya S. Montagueo

**Repository:** [PAM-spatiotemporal-modeling](https://github.com/YayaSimone/PAM-spatiotemporal-modeling)

---

## 1. Research Objective

This project investigates theoretical mathematical modeling in the context of primary amebic meningoencephalitis (PAM).

The current implementation is a nonspatial system of coupled ordinary differential equations (ODEs).

The framework is hypothetical, empirically uncalibrated, and experimentally unvalidated. Mathematical behavior observed within the model should not be interpreted as an established biological mechanism or clinical prediction.

## 2. State Variables

The theoretical framework incorporates five conceptual state variables representing biological processes.

The intended state constraints include nonnegativity and interval preservation for normalized quantities.

Operational biological units, normalization conventions, and experimentally calibrated state definitions remain to be established.

## 3. Governing Equations

The current nonspatial implementation consists of five coupled ordinary differential equations.

The governing system has the autonomous form:

$$\frac{d\mathbf{y}}{dt} = \mathbf{F}(\mathbf{y};\boldsymbol{\theta})$$

where $\mathbf{y}$ denotes the state vector and $\boldsymbol{\theta}$ denotes the model parameter vector.

The autonomous formulation does not explicitly depend on time.

This document presents the general mathematical structure and methodological interpretation of the framework. The complete implemented formulation and computational source materials are preserved in the local research archive pending further methodological assessment and faculty guidance.

Public computational source documentation is available in [src/README.md](../src/README.md).

The original conceptual formulation is documented separately in [original-framework.md](original-framework.md).

### 3.1 Modeling Assumptions

- Biological processes are represented through continuous state variables.
- The current implementation does not explicitly resolve spatial heterogeneity.
- Composite state variables simplify complex biological processes.
- Parameter values are hypothetical and empirically uncalibrated.
- Time is expressed in model units rather than calibrated clinical time.
- Biological relationships represented within the framework remain modeling assumptions.

## 4. Blood–Brain Barrier Formulation

### 4.1 Original Formulation

The original theoretical framework identified a mathematical consistency issue involving the intended blood–brain barrier (BBB) integrity interval.

The initial formulation did not guarantee that the integrity variable would remain within its intended bounds.

### 4.2 Revised Formulation

A revised mathematical formulation was developed to address the identified consistency issue.

Numerical bounds checks provide additional evidence of consistency within the evaluated simulation scenarios.

### 4.3 Interpretation

The revised formulation represents a mathematical consistency improvement, not an experimentally established biological mechanism.

The numerical verification workflow includes a negative-control comparison between the original and revised formulations.

Under an evaluated stress scenario, the original formulation violated the intended lower integrity bound, whereas the revised formulation remained within the intended interval.

This comparison provides additional evidence supporting the mathematical consistency of the revision within the tested scenarios. It does not independently establish general interval invariance or biological validity.

## 5. Injury-Dominance Differential

The theoretical framework considers distinct modeled contributions to tissue injury.

The computational investigation examines their relative mathematical behavior under hypothetical assumptions.

The contribution of the host immune response to PAM severity remains unresolved in the supporting literature ([Chen and Moseman, 2023](https://doi.org/10.3389/fitd.2022.1082334)).

Accordingly, inflammation-associated injury represents an explicit modeling assumption rather than an experimentally established biological mechanism.

A crossover within this theoretical system is not evidence that an equivalent biological transition occurs in patients with PAM.

The supporting scientific figure is preserved in the local research archive and is not currently published in the public repository.

## 6. Local Nonlinear Model Behavior

### 6.1 Finite-Time Grazing Interpretation

The numerical evidence is consistent with a local finite-time grazing tangency within the theoretical framework.

In general mathematical analysis, a nondegenerate quadratic tangency is distinguished from an ordinary zero crossing by its local behavior.

The numerical findings support a local mathematical interpretation rather than an exact analytical proof.

The identified behavior should not be classified as a dynamical-system bifurcation or generalized beyond the investigated theoretical model.

### 6.2 Asymptotic Square-Root Scaling

Square-root scaling is a recognized mathematical behavior associated with certain nondegenerate quadratic tangencies under appropriate assumptions.

In generic mathematical notation:

$$T(\varepsilon) \sim C\sqrt{\varepsilon}$$

where:

- $T$ represents an interval duration.
- $\varepsilon$ represents distance from a critical parameter value.
- $C$ represents a local asymptotic prefactor.

The theoretical leading-order scaling exponent is:

$$p = \frac{1}{2}$$

The theoretical asymptotic prefactor and an empirical coefficient obtained from regression over a finite fitting interval are distinct quantities and should not be treated as interchangeable.

The supporting scientific figure is preserved in the local research archive and is not currently published in the public repository.

### 6.3 Residual Analysis

Residual analysis evaluates differences between numerical observations and mathematical predictions.

Analytical predictions and fitted regression curves are maintained separately because their residuals represent distinct comparisons.

Residual patterns alone do not establish the form or magnitude of higher-order correction terms.

Numerical observations do not constitute an analytical proof or biological validation.

Supporting numerical datasets and research notes are preserved in the local research archive. Public computational results documentation is available in [results/README.md](../results/README.md).

## 7. Numerical Verification

The computational workflow includes:

- Numerical integrator comparisons.
- Evaluation of numerical tolerance sensitivity.
- State-variable nonnegativity checks.
- Integrity bounds checks.
- Computational sensitivity studies.
- Local nonlinear mathematical analysis.
- Regression testing.
- Dataset integrity review.

Numerical verification addresses computational consistency rather than empirical accuracy.

### 7.1 State Constraints

The theoretical framework incorporates intended nonnegativity and interval constraints.

Numerical sampling provides evidence that these constraints are respected within evaluated simulation scenarios.

Sampled numerical checks should not be interpreted as a general mathematical proof of invariance.

Analytical arguments and sampled numerical evidence represent different forms of mathematical support.

### 7.2 Reproducibility

The project distinguishes between dataset integrity, regression testing, and independent computational reproduction.

| Verification Category | Status |
| --- | --- |
| Archived dataset integrity | Previously reviewed using local archived files |
| Local regression testing | Previously passed in the local review environment |
| Repository-level verification | Outstanding |
| Independent computational reproduction | Not performed |
| Experimental validation | Not performed |

Local regression tests have previously passed in a Python 3.13.5 review environment.

Archived numerical datasets have undergone checksum and structural review. The checksum manifest is preserved in the local research archive.

The public repository currently provides research documentation rather than an executable computational implementation.

Repository-level verification and independent computational reproduction remain outstanding.

These procedures address different aspects of computational consistency and do not constitute experimental or clinical validation.

### 7.3 Dataset Integrity and Provenance

Numerical datasets, figures, and associated research notes are preserved in the local research archive.

The dataset integrity review distinguishes between:

- File-level checksum verification.
- Structural completeness.
- Numerical consistency.
- Independent computational reproduction.

A checksum establishes whether file contents match a recorded fingerprint. It does not independently establish computational reproducibility, data provenance, or scientific validity.

Archived datasets should be preserved without undocumented modifications.

Any intentional changes to dataset contents or column definitions must be documented and accompanied by an updated checksum manifest.

### 7.4 Computational Environment

The computational implementation uses Python and scientific computing libraries, including:

- NumPy
- SciPy
- pandas
- Matplotlib
- pytest

The previously reviewed local environment used Python 3.13.5.

Documented dependency versions are available in [requirements.txt](../requirements.txt).

The dependency file is provided as computational environment documentation. Its availability does not establish that the public repository contains an executable implementation or an independently reproduced computational environment.

Compatibility with other Python versions and operating environments has not been established.

### 7.5 Verification Limitations

Agreement between numerical integrators supports numerical consistency but does not establish a rigorous numerical error bound.

Passing regression tests provides evidence that specified implementation requirements are satisfied within the tested scenarios.

Neither numerical agreement nor regression testing establishes biological validity, clinical predictive accuracy, or experimental reproducibility.

## 8. Dimensional Consistency

The current nonspatial framework requires consistent units across all implemented state variables and mathematical terms.

| Quantity | Intended Dimension | Calibration Status |
| --- | --- | --- |
| Time | Model time | Uncalibrated |
| Pathogen burden | Modeled abundance | Operational units unresolved |
| Neural tissue viability | Modeled tissue viability | Operational units unresolved |
| Inflammatory activity | Modeled inflammatory activity | Operational units unresolved |
| Cellular debris | Modeled debris abundance | Operational units unresolved |
| BBB integrity | Dimensionless | Normalized model index |

The current descriptions represent conceptual model quantities rather than experimentally established measurement units.

Specific interpretations as counts, concentrations, densities, or normalized fractions require additional documentation and justification.

If state variables use different operational units, appropriate conversion factors may be required.

Biologically meaningful parameter units and calibrated parameter ranges remain unresolved.

No experimentally established parameter ranges are claimed.

All reported times are expressed in model time units, not hours or days.

## 9. Proposed Spatial Extension

The original conceptual framework includes a proposed spatial extension.

The current computational implementation is nonspatial.

Further methodological assessment, biological justification, and scientific development remain pending faculty guidance.

No completed spatial PDE implementation, spatial simulation results, or spatially validated predictions are claimed.

The original conceptual framework is documented separately in [original-framework.md](original-framework.md).

## 10. Scientific Limitations

- Model parameters are hypothetical and empirically uncalibrated.
- Operational biological units remain unresolved.
- Composite state variables simplify complex biological processes.
- Inflammation-associated injury represents an explicit modeling assumption rather than an established biological mechanism.
- The contribution of the host immune response to PAM severity remains unresolved.
- Numerical results depend on the mathematical assumptions, initial conditions, and parameter values.
- Identified nonlinear transitions describe local model behavior.
- Numerical consistency does not establish biological validity.
- Sampled numerical bounds checks do not constitute a general mathematical proof.
- BBB feedback is not explicitly represented.
- Spatial extensions remain proposed.
- Independent reproduction of the complete numerical study has not been performed.
- The framework has not been experimentally validated or peer reviewed.
- Proposed model regimes should not be interpreted as established clinical stages of PAM.

No therapeutic recommendations, validated disease predictions, or clinical conclusions are claimed.

## 11. Supporting Documentation

| Resource | Description |
| --- | --- |
| [Project README](../README.md) | Research overview |
| [Original Framework](original-framework.md) | Initial conceptual formulation |
| [Research Questions](research-questions.md) | Scientific motivation |
| [Computational Source Documentation](../src/README.md) | Implementation documentation |
| [Computational Results](../results/README.md) | Archived research materials documentation |
| [Numerical Verification](../tests/README.md) | Verification and regression test documentation |
| [Scientific References](../references/README.md) | Supporting scientific literature |

## 12. Citation

If referencing this repository, please cite:

Montagueo, K. S. (2026). *Computational Modeling of Spatiotemporal Host–Pathogen Dynamics in Primary Amebic Meningoencephalitis (PAM).* Independent computational biology research.

**Repository:** https://github.com/YayaSimone/PAM-spatiotemporal-modeling

### Version-Specific Citation

When referencing a specific revision of this documentation, include the corresponding Git commit identifier or documentation release tag, when available, together with the access date.

A versioned documentation snapshot identifies a particular repository state. It does not constitute a validated computational software release, independent computational reproduction, or scientific peer review.

---

*Ongoing theoretical research; not peer reviewed or experimentally validated.*
