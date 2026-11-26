# Original Working Framework (Archival Draft)

**Provenance:** Supplied by the author in October 2026 and believed by the author to be the most recent version developed around June 2026 (exact original date unverified). This file preserves the original model equations and conceptual structure for historical comparison with the later Phase I nonspatial framework described in [mathematical-framework.md](mathematical-framework.md)

## Archival Status

This document preserves an earlier conceptual formulation for historical reference.

The spatial framework described here is proposed rather than computationally implemented or experimentally validated.

This archival formulation should not be interpreted as the current Phase I implementation, an established biological mechanism, or a clinical predictive tool.

For the revised framework, see [Mathematical Framework](mathematical-framework.md).
---

## Project title

Computational Modeling of Spatiotemporal Host-Pathogen Dynamics and Neuroinflammatory Progression in Primary Amebic Meningoencephalitis (PAM)

## Purpose

Develop a theoretical systems biology framework to explore interactions among pathogen proliferation, neuroinflammatory signaling, neural tissue viability, and host immune responses during PAM. Intended to generate testable hypotheses, not validated clinical predictions.

## State variables

- P(x,t): pathogen density
- V(x,t): viable neural tissue
- I(x,t): neuroinflammatory activity
- D(x,t): cellular debris
- B(x,t): blood-brain barrier integrity

## Original equations (unchanged)

$$\partial_t P=d_P\partial_{xx}P+rP(1-P/K)(V/V_0)-\mu PI$$

$$\partial_t V=-\alpha PV-\beta IV$$

$$\partial_t I=d_I\partial_{xx}I+\gamma P+\delta D-\mu_I I$$

$$\partial_t D=\alpha PV+\beta IV-\lambda D$$

$$\partial_t B=-\theta I-\kappa P+\rho(1-B)$$

## Central hypothesis

The author proposes three overlapping hypothetical regimes: (1) pathogen-dominated expansion, (2) neuroinflammatory amplification, and (3) barrier dysfunction and systems decline. The model asks whether inflammation-associated injury may exceed pathogen-associated injury where `β I V > α P V`.

## Research themes and questions

- Spatial pathogen dissemination and regional susceptibility
- Propagation of inflammatory signaling and secondary tissue injury
- Timing and role of blood-brain barrier dysfunction
- Interaction of direct pathogen injury and host-associated immunopathology
- Hypothetical intervention windows

## Proposed methods

ODEs, PDEs, reaction-diffusion systems, parameter exploration, sensitivity analysis, and future Python-based scientific computing.

## Proposed validation directions

Animal model comparison, transcriptomics, cytokine network analysis, spatial pathology correlation, sensitivity and uncertainty analysis. These have **not** been performed.

## Limitations from original draft

The model is theoretical and exploratory, requires calibration, parameter optimization, and experimental validation, and cannot currently establish disease mechanisms or therapeutic timing.

> Preservation note: This file is a structured archival transcription of the author's supplied material, not a verbatim copy of every explanatory paragraph. Keep the complete original message separately if verbatim preservation is required.
