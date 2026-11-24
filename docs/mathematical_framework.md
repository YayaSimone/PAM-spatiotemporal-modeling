# Mathematical Framework

**Independent Computational Biology Research | 2026–Present**

**Researcher:** Kenya S. Montagueo

**Repository:** [PAM-spatiotemporal-modeling](https://github.com/YayaSimone/PAM-spatiotemporal-modeling)

## 1. Research Objective

This project investigates theoretical interactions among pathogen burden, neural tissue viability, neuroinflammatory activity, cellular debris accumulation, and blood–brain barrier (BBB) integrity in a mathematical framework motivated by primary amebic meningoencephalitis (PAM).

The current implementation is a nonspatial system of coupled ordinary differential equations (ODEs).

The framework is hypothetical, empirically uncalibrated, and experimentally unvalidated. Mathematical behavior observed within the model should not be interpreted as an established biological mechanism or clinical prediction.

## 2. State Variables

| Symbol | State Variable | Interpretation |
|---|---|---|
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

Operational biological units and experimentally calibrated state definitions remain to be established.

## 3. Governing Equations

The current nonspatial implementation consists of five coupled ordinary differential equations.

Define the state vector:

$$
\mathbf{y}(t)=
\begin{bmatrix}
P(t)\\
V(t)\\
I(t)\\
D(t)\\
B(t)
\end{bmatrix}
$$

The governing system has the general form:

$$
\frac{d\mathbf{y}}{dt}
=
\mathbf{F}(\mathbf{y};\boldsymbol{\theta})
$$

where $\boldsymbol{\theta}$ denotes the model parameter vector.

The framework represents interactions among five coupled biological processes:

- Pathogen-associated dynamics.
- Loss of viable neural tissue.
- Inflammatory recruitment and resolution.
- Cellular debris accumulation and clearance.
- BBB injury and recovery.

The implemented formulation is available in:

[`src/nonspatial_model.py`](../src/nonspatial_model.py)

The original conceptual formulation is preserved separately:

[Original theoretical framework](original-framework.md)

### 3.1 Modeling Assumptions

- Biological processes are represented through continuous state variables.
- The current implementation does not explicitly resolve spatial heterogeneity.
- Neuroinflammatory activity is represented as a composite variable rather than distinct immune-cell populations.
- Parameter values are hypothetical.
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

## 5. Injury-Dominance Differential

The model distinguishes between pathogen-associated and inflammation-associated contributions to neural tissue injury.

For positive viable neural tissue, their relative contributions can be compared through an injury-dominance differential.

Positive differential values indicate that the modeled inflammation-associated contribution exceeds the modeled pathogen-associated contribution.

Negative values indicate the reverse relationship.

At zero viable neural tissue, both modeled instantaneous injury contributions vanish.

A crossover within this theoretical system is not evidence that an equivalent biological transition occurs in patients with PAM.

![Injury dominance near the hypothetical threshold](../results/pam_threshold_mechanism.png)

*Figure 1. Injury-dominance trajectories within the selected hypothetical model regime.*

## 6. Local Nonlinear Model Behavior

### 6.1 Grazing Transition

Numerical analysis identifies a local grazing transition in the injury-dominance differential.

At a grazing tangency, the differential reaches zero at a stationary point.

A nondegenerate local maximum is characterized by a negative second time derivative.

This mathematical structure provides a framework for interpreting the appearance or disappearance of a transient positive interval.

The identified transition is local to the investigated theoretical parameter regime and should not be generalized to all possible model configurations.

### 6.2 Square-Root Scaling

Near a nondegenerate quadratic grazing tangency, the duration of a transient interval may exhibit square-root scaling with distance from the critical parameter value.

In generic mathematical notation:

$$
T(\varepsilon)\sim C\sqrt{\varepsilon}
$$

where:

- $T$ represents the interval duration.
- $\varepsilon$ represents distance from a critical parameter value.
- $C$ represents a local proportionality constant.

The theoretical scaling exponent is:

$$
p=\frac{1}{2}
$$

The numerical analysis investigates whether the model exhibits behavior consistent with this local mathematical relationship.

![Local grazing scaling](../results/pam_grazing_scaling.png)

*Figure 2. Comparison of numerical interval durations and the local square-root scaling prediction.*

### 6.3 Residual Analysis

Residual analysis evaluates differences between numerical interval durations and mathematical scaling predictions.

Analytical predictions and fitted regression curves should be distinguished because their residuals represent different comparisons.

Supporting numerical datasets and research notes are maintained in the [results directory](../results/).

The analysis characterizes mathematical behavior within the theoretical model and does not establish biological validity.

## 7. Numerical Verification

The computational workflow includes:

- Comparison of LSODA and DOP853 numerical integrators.
- Evaluation of numerical tolerance sensitivity.
- State-variable nonnegativity checks.
- BBB integrity bounds checks.
- Parameter sensitivity analysis.
- Local nonlinear scaling analysis.

Numerical verification addresses computational consistency rather than empirical accuracy.

### 7.1 State Constraints

The intended state constraints are:

$$
P,V,I,D\geq 0
$$

$$
0\leq B\leq 1
$$

Numerical sampling provides evidence that these constraints are respected within evaluated simulation scenarios.

Sampled numerical checks should not be interpreted as a general mathematical proof of invariance.

### 7.2 Reproducibility

The repository maintains separate directories for:

- [Python implementation](../src/)
- [Numerical datasets and figures](../results/)
- [Model tests](../tests/)

The root `requirements.txt` file specifies the external Python dependencies.

Independent reproduction, environment verification, and script runtime documentation remain important reproducibility checkpoints.

## 8. Dimensional Consistency

The framework requires consistent units across all state variables and mathematical terms.

| Quantity | Intended Dimension |
|---|---|
| Time | Model time |
| Spatial coordinate | Length, for proposed spatial extensions |
| Pathogen burden | Pathogen abundance units |
| Neural viability | Tissue viability units |
| Inflammatory activity | Inflammatory activity units |
| Cellular debris | Debris abundance units |
| BBB integrity | Dimensionless |

If neural tissue loss and cellular debris are represented using different operational units, appropriate conversion factors would be required.

Biologically meaningful parameter units and calibrated parameter ranges remain unresolved.

## 9. Proposed Spatial Extension

The original conceptual framework includes a proposed reaction–diffusion extension.

The current computational implementation is nonspatial.

A future spatial framework would require explicit definitions of spatial domains, boundary conditions, transport assumptions, and biological justification.

No completed spatial PDE implementation, spatial simulation results, or spatially validated predictions are claimed.

The original conceptual framework remains available in:

[Original theoretical framework](original-framework.md)

## 10. Scientific Limitations

- Model parameters are hypothetical and empirically uncalibrated.
- Composite state variables simplify complex biological processes.
- Numerical results depend on the mathematical assumptions.
- Identified nonlinear transitions describe local model behavior.
- Numerical consistency does not establish biological validity.
- BBB feedback is not explicitly represented.
- Spatial extensions remain proposed.
- The framework has not been experimentally validated or peer reviewed.

The proposed model regimes should not be interpreted as established clinical stages of PAM.

No therapeutic recommendations or validated disease predictions are claimed.

## 11. Supporting Documentation

| Resource | Description |
|---|---|
| [Project README](../README.md) | Research overview |
| [Original framework](original-framework.md) | Initial conceptual formulation |
| [Research questions](research-questions.md) | Scientific motivation |
| [Source code](../src/) | Computational implementation |
| [Numerical results](../results/) | Datasets, figures, and research notes |
| [Model tests](../tests/) | Numerical verification |
| [References](../references/) | Supporting scientific literature |

## 12. Citation

If referencing this repository, please cite:

Montagueo, K. S. (2026). *Computational Modeling of Host–Pathogen Dynamics in Primary Amebic Meningoencephalitis (PAM).* Independent computational biology research.

**Repository:** [github.com/YayaSimone/PAM-spatiotemporal-modeling](https://github.com/YayaSimone/PAM-spatiotemporal-modeling)

*Ongoing theoretical research; not peer reviewed or experimentally validated.*

