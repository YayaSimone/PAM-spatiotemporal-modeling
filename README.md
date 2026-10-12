# Computational Modeling of Spatiotemporal Host–Pathogen Dynamics in Primary Amebic Meningoencephalitis (PAM)

**Independent Computational Biology Research | 2026–Present**

**Researcher:** Kenya Montagueo  
**Status:** Theoretical framework development — not experimentally validated

## Project Overview

Primary amebic meningoencephalitis (PAM) is a rare, rapidly progressive infection of the central nervous system caused by *Naegleria fowleri*.

This independent research project explores the spatial and temporal interactions among pathogen dissemination, neuroinflammatory signaling, neural tissue injury, and blood–brain barrier dysfunction during acute PAM progression.

The proposed framework integrates systems biology, mathematical modeling, and reaction–diffusion equations to investigate potential mechanisms of disease progression.

The goal is to generate biologically testable hypotheses rather than provide validated clinical predictions.

## Research Questions

### Pathogen Dissemination

- How might pathogen burden evolve across neural tissue over time?
- Which anatomical regions may be vulnerable to early pathogen colonization?
- What factors could influence regional dissemination?

### Neuroinflammatory Dynamics

- How might inflammatory signaling evolve during acute infection?
- Could inflammatory activity propagate beyond pathogen-rich regions?
- Under what conditions might inflammation-mediated injury exceed direct pathogen-mediated injury?

### Blood–Brain Barrier Dysfunction

- How might barrier integrity change during disease progression?
- How could inflammatory signaling influence barrier permeability?
- What additional mechanisms would be required to model feedback between barrier dysfunction and infection?

### Neural Tissue Injury

- How might direct pathogen-mediated injury and host-mediated immunopathology interact?
- Could the model identify a theoretical transition between pathogen-dominated and inflammation-dominated injury?

## Mathematical Framework

The proposed model consists of five coupled biological state variables:

| Variable | Biological Interpretation |
|----------|---------------------------|
| P(x,t) | Pathogen density |
| V(x,t) | Viable neural tissue |
| I(x,t) | Neuroinflammatory activity |
| D(x,t) | Accumulated cellular debris |
| B(x,t) | Blood–brain barrier integrity |

Here, x represents anatomical location and t represents time.

### 1. Pathogen Dissemination

$$
\frac{\partial P}{\partial t}
=
d_P\frac{\partial^2P}{\partial x^2}
+
rP\left(1-\frac{P}{K}\right)\frac{V}{V_0}
-
\mu PI
$$

This equation represents hypothetical spatial spread, pathogen proliferation, tissue-dependent growth, and immune-mediated clearance.

### 2. Neural Tissue Viability

$$
\frac{\partial V}{\partial t}
=
-\alpha PV-\beta IV
$$

Neural tissue viability decreases through two proposed mechanisms:

- Direct pathogen-mediated injury
- Host-mediated neuroinflammatory injury

### 3. Neuroinflammatory Activity

$$
\frac{\partial I}{\partial t}
=
d_I\frac{\partial^2I}{\partial x^2}
+
\gamma P+\delta D-\mu_I I
$$

Inflammatory activity is stimulated by pathogen burden and tissue debris, with spatial propagation and regulatory decay.

### 4. Cellular Debris Accumulation

$$
\frac{\partial D}{\partial t}
=
\alpha PV+\beta IV-\lambda D
$$

Cellular debris accumulates through modeled tissue injury and decreases through clearance.

### 5. Blood–Brain Barrier Integrity

The original exploratory formulation is:

$$
\frac{\partial B}{\partial t}
=
-\theta I-\kappa P+\rho(1-B)
$$

This equation is retained for documentation of the initial framework.

Further refinement is required to maintain biologically meaningful bounds on barrier integrity and evaluate potential feedback mechanisms.

## Central Hypothesis

The framework explores whether PAM progression may involve a theoretical transition from pathogen-dominated injury toward inflammation-dominated injury.

The proposed transition occurs when:

$$
\beta I(x,t)V(x,t)>\alpha P(x,t)V(x,t)
$$

For positive viable tissue, this simplifies to:

$$
\beta I(x,t)>\alpha P(x,t)
$$

This condition identifies where the modeled rate of inflammation-mediated tissue injury exceeds the modeled rate of direct pathogen-mediated injury.

It is a theoretical criterion, not an established biological finding.

## Proposed Computational Methods

- Ordinary Differential Equations (ODEs)
- Partial Differential Equations (PDEs)
- Reaction–diffusion modeling
- Python scientific computing
- NumPy and SciPy
- Numerical simulation
- Parameter sensitivity analysis
- Uncertainty analysis

## Proposed Validation Strategy

Future research may investigate model plausibility through:

1. Comparison with published PAM animal-model studies
2. Analysis of relevant transcriptomic datasets, where available
3. Examination of inflammatory signaling pathways
4. Comparison with documented anatomical patterns of neural injury
5. Sensitivity and uncertainty analysis

## Development Roadmap

- [x] Develop initial research questions
- [x] Establish five-variable theoretical framework
- [x] Formulate initial coupled differential equations
- [ ] Define biological units and model parameters
- [ ] Establish initial and boundary conditions
- [ ] Evaluate mathematical consistency
- [ ] Implement an initial Python simulation
- [ ] Conduct sensitivity analysis
- [ ] Compare model behavior with published evidence
- [ ] Document results and limitations

## Current Limitations

This project remains theoretical and exploratory.

The equations require further mathematical refinement, parameter calibration, numerical implementation, and comparison with experimental observations.

No validated disease predictions, treatment recommendations, or therapeutic conclusions are claimed.

## Researcher

**Kenya Montagueo**

Incoming Biological Sciences Transfer Student  
Hunter College — Spring 2027

Associate of Science, Computer Science  
City College of San Francisco

U.S. Navy Nuclear Propulsion Veteran

**Research Interests:**

Computational Biology | Systems Biology | Immunology | Neuroscience | Host–Pathogen Interactions | Infectious Disease | Translational Medicine

---

*Independent research project. Initial framework developed in 2026. Ongoing mathematical and computational refinement.*
