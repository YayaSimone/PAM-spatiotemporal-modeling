# Mathematical Framework

**Independent Computational Biology Research | 2026–Present**

**Researcher:** Kenya S. Montagueo

**Repository:** [PAM-spatiotemporal-modeling](https://github.com/YayaSimone/PAM-spatiotemporal-modeling)

---

## 1. Research Objective

This project investigates theoretical interactions among pathogen burden, neural tissue viability, neuroinflammatory activity, cellular debris accumulation, and blood–brain barrier (BBB) integrity in a mathematical framework motivated by primary amebic meningoencephalitis (PAM).

The current implementation is a nonspatial system of coupled ordinary differential equations (ODEs).

The framework is hypothetical, empirically uncalibrated, and experimentally unvalidated. Mathematical behavior observed within the model should not be interpreted as an established biological mechanism or clinical prediction.

## 2. State Variables

| Symbol | State Variable | Interpretation |
| --- | --- | --- |
| $P(t)$ | Pathogen burden | Modeled pathogen abundance |
| $V(t)$ | Neural tissue viability | Remaining viable neural tissue |
| $I(t)$ | Neuroinflammatory activity | Composite inflammatory response |
| $D(t)$ | Cellular debris | Accumulated injury-associated material |
| $B(t)$ | BBB integrity | Dimensionless barrier integrity index |

The BBB integrity variable is intended to remain within:

$$
0 \leq B(t) \leq 1
$$

The remaining state variables are intended to remain nonnegative.

Operational biological units, normalization conventions, and experimentally calibrated state definitions remain to be established.

## 3. Governing Equations

The current nonspatial implementation consists of five coupled ordinary differential equations.

Define the state vector:

$$
\mathbf{y}(t) =
\begin{bmatrix}
P(t) \\
V(t) \\
I(t) \\
D(t) \\
B(t)
\end{bmatrix}
$$

The governing system has the autonomous form:

$$
\frac{d\mathbf{y}}{dt}
=
\mathbf{F}(\mathbf{y};\boldsymbol{\theta})
$$

where $\boldsymbol{\theta}$ denotes the model parameter vector.

The autonomous formulation does not explicitly depend on time.

The framework represents interactions among five coupled biological processes:

- Pathogen-associated dynamics.
- Loss of viable neural tissue.
- Inflammatory recruitment and resolution.
- Cellular debris accumulation and clearance.
- BBB injury and recovery.

The implemented formulation is available in [`src/nonspatial_model.py`](../src/nonspatial_model.py).

The original conceptual formulation is preserved separately in [`original-framework.md`](original-framework.md).

### 3.1 Modeling Assumptions

- Biological processes are represented through continuous state variables.
- The current implementation does not explicitly resolve spatial heterogeneity.
- Neuroinflammatory activity is represented as a composite variable rather than distinct immune-cell populations.
- Inflammation-associated injury represents an explicit modeling assumption.
- Parameter values are hypothetical and empirically uncalibrated.
- Time is expressed in model units rather than calibrated clinical time.
- BBB integrity is represented as a downstream model outcome.

## 4. Blood–Brain Barrier Formulation

### 4.1 Original Formulation

The original theoretical framework identified a mathematical consistency issue involving the intended BBB integrity interval.

The initial formulation did not guarantee that the BBB variable would remain between zero and one.

### 4.2 Revised Formulation

The revised implementation incorporates a state-dependent injury term and a recovery term.

At the lower boundary, the revised formulation permits recovery rather than continued movement into negative integrity values.

At the upper boundary, the formulation does not permit injury-associated terms to increase integrity beyond its intended maximum.

This provides mathematical support for interval preservation under the stated nonnegativity assumptions.

Numerical bounds checks provide additional evidence of consistency within the evaluated simulation scenarios.

### 4.3 Interpretation

The revised BBB formulation represents a mathematical consistency improvement, not an experimentally established biological mechanism.

BBB integrity currently does not explicitly feed back into the other state equations. Consequently, the model does not establish that BBB disruption accelerates pathogen progression or inflammatory injury.

The numerical verification workflow includes a negative-control comparison between the original and revised BBB formulations.

Under an evaluated stress scenario, the original formulation violated the intended lower integrity bound, whereas the revised formulation remained within the intended interval.

This comparison provides additional evidence supporting the mathematical consistency of the revision within the tested scenarios. It does not independently establish general interval invariance or biological validity.

## 5. Injury-Dominance Differential

The model distinguishes between pathogen-associated and inflammation-associated contributions to neural tissue injury.

For positive viable neural tissue, their relative contributions can be compared using the injury-dominance differential defined in the computational implementation.

Positive differential values indicate that the modeled inflammation-associated contribution exceeds the modeled pathogen-associated contribution.

Negative values indicate the reverse relationship.

At zero viable neural tissue, both modeled instantaneous injury contributions vanish.

The contribution of the host immune response to PAM severity remains unresolved in the supporting literature ([Chen and Moseman, 2022](https://doi.org/10.3389/fitd.2022.1082334)).

Accordingly, inflammation-associated injury represents an explicit modeling assumption rather than an experimentally established biological mechanism.

A crossover within this theoretical system is not evidence that an equivalent biological transition occurs in patients with PAM.

![Injury dominance near the hypothetical threshold](../results/pam_threshold_mechanism.png)

*Figure 1. Injury-dominance trajectories within the selected hypothetical model regime.*

## 6. Local Nonlinear Model Behavior

### 6.1 Finite-Time Grazing Interpretation

The numerical evidence is consistent with a local finite-time grazing tangency in the injury-dominance differential.

A nondegenerate quadratic tangency requires a zero function value, a stationary point, and nonzero local curvature. These conditions distinguish tangency from an ordinary zero crossing.

A negative second derivative at such a stationary point is consistent with a local maximum.

The numerical findings support a local mathematical interpretation rather than an exact analytical proof.

The identified behavior should not be classified as a dynamical-system bifurcation or generalized beyond the investigated theoretical model.

### 6.2 Asymptotic Square-Root Scaling

Near a nondegenerate quadratic tangency, a transient interval may exhibit square-root scaling with distance from a critical parameter value under appropriate mathematical assumptions.

In generic mathematical notation:

$$
T(\varepsilon) \sim C\sqrt{\varepsilon}
$$

where:

- $T$ represents the interval duration.
- $\varepsilon$ represents distance from a critical parameter value.
- $C$ represents a local asymptotic prefactor.

The theoretical leading-order scaling exponent is:

$$
p = \frac{1}{2}
$$

The numerical findings are consistent with this local mathematical interpretation.

The theoretical asymptotic prefactor and an empirical coefficient obtained from regression over a finite fitting interval are distinct quantities and should not be treated as interchangeable.

![Local grazing scaling](../results/pam_grazing_scaling.png)

*Figure 2. Comparison of numerical interval durations and the local square-root scaling prediction.*

### 6.3 Residual Analysis

Residual analysis evaluates differences between numerical observations and mathematical scaling predictions.

Analytical predictions and fitted regression curves are maintained separately because their residuals represent distinct comparisons.

Systematic residual patterns suggest departures from the leading-order approximation over a finite fitting interval.

However, residual patterns alone do not establish the form or magnitude of higher-order correction terms.

The numerical findings are consistent with the proposed local scaling interpretation but do not constitute an analytical proof or biological validation.

Supporting numerical datasets and research notes are maintained in the [results directory](../results/).

## 7. Numerical Verification

The computational workflow includes:

- Comparison of LSODA and DOP853 numerical integrators.
- Evaluation of numerical tolerance sensitivity.
- State-variable nonnegativity checks.
- BBB integrity bounds checks.
- Parameter sensitivity analysis.
- Local nonlinear scaling analysis.
- Regression testing.
- Dataset integrity review.

Numerical verification addresses computational consistency rather than empirical accuracy.

### 7.1 State Constraints

The intended state constraints are:

$$
P,V,I,D \geq 0
$$

$$
0 \leq B \leq 1
$$

Numerical sampling provides evidence that these constraints are respected within evaluated simulation scenarios.

Sampled numerical checks should not be interpreted as a general mathematical proof of invariance.

The analytical argument for BBB interval preservation and the numerical evidence for state nonnegativity represent different forms of mathematical support.

### 7.2 Reproducibility

The project distinguishes between dataset integrity, regression testing, and independent computational reproduction.

| Verification Category | Status |
| --- | --- |
| Archived dataset integrity | Previously reviewed using local archived files |
| Local regression testing | Previously passed in the local review environment |
| Final repository checksum verification | Pending upload and verification of the final GitHub revision |
| Final release regression testing | Pending |
| Independent computational reproduction | Not performed |
| Experimental validation | Not performed |

Local regression tests have previously passed in a Python 3.13.5 review environment.

Archived numerical datasets have undergone checksum and structural review.

The archived dataset review and final repository verification concern different verification targets. The earlier local review does not establish that files in the final GitHub revision are identical to the archived files.

Final repository verification and independent computational reproduction remain pending.

These procedures establish different aspects of computational consistency and do not constitute experimental or clinical validation.

### 7.3 Dataset Integrity and Provenance

Numerical datasets, figures, and associated research notes are maintained separately from the mathematical documentation.

The dataset integrity review distinguishes between:

- File-level checksum verification.
- Structural completeness.
- Numerical consistency.
- Independent computational reproduction.

A checksum establishes whether file contents match a recorded fingerprint. It does not establish the scientific correctness of the data or demonstrate that the results can be independently reproduced.

Archived datasets should be preserved without undocumented modifications.

Any intentional changes to dataset contents or column definitions must be documented and accompanied by an updated checksum manifest.

### 7.4 Computational Environment

The computational implementation uses Python and scientific computing libraries, including:

- NumPy.
- SciPy.
- pandas.
- Matplotlib.
- pytest.

The previously reviewed local environment used Python 3.13.5.

The final repository should document its dependency versions and execution instructions in the root README and requirements file.

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

The original conceptual framework includes a proposed reaction–diffusion extension.

The current computational implementation is nonspatial.

A future spatial framework would require explicit definitions of spatial coordinates, spatial domains, boundary conditions, transport assumptions, and biological justification.

Spatial coordinates would have dimensions of length but are not implemented in the current framework.

No completed spatial PDE implementation, spatial simulation results, or spatially validated predictions are claimed.

The original conceptual framework is maintained separately in [`original-framework.md`](original-framework.md).

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
| [Original framework](original-framework.md) | Initial conceptual formulation |
| [Research questions](research-questions.md) | Scientific motivation |
| [Source code](../src/) | Computational implementation |
| [Numerical results](../results/) | Datasets, figures, and research notes |
| [Model tests](../tests/) | Numerical verification |
| [References](../references/README.md) | Supporting scientific literature |

## 12. Citation

If referencing this repository, please cite:

> Montagueo, K. S. (2026). *Computational Modeling of Host–Pathogen Dynamics in Primary Amebic Meningoencephalitis (PAM).* Independent computational biology research.

**Repository:** https://github.com/YayaSimone/PAM-spatiotemporal-modeling

---

*Ongoing theoretical research; not peer reviewed or experimentally validated.*

*Ongoing theoretical research; not peer reviewed or experimentally validated.*
