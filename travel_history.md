# Research Idea: Sampling-Dependent Views of Epidemic Phylogenies

## Core Motivation

A central challenge in phylodynamics is that **observed phylogenies are incomplete, sampling-dependent projections of the underlying transmission process**. Even when the epidemic dynamics are held fixed, different sampling strategies can produce substantially different genealogical structures. Making this relationship explicit is important for understanding what phylogenies can and cannot tell us about transmission history.

---

## Current Setup

I am working with a **two-strain epidemic model** where $I_1(t)$ and $I_2(t)$ represent infections from two competing strains with partial cross-immunity. The full system includes $S(t)$, $I_1(t)$, $I_2(t)$, $R_1(t)$, and $R_2(t)$.

Genealogies are simulated using a **Volz-type coalescent formulation**, where the coalescent rate is driven by the epidemic dynamics, with $I_i(t)$ acting as a proxy for effective population size. The genealogy is generated conditional on the forward-time epidemic trajectories.

I currently have two genealogies — one for each strain — simulated under **peak sampling**, defined as drawing a fixed number of samples from a narrow time window centered around the maximum of $I_i(t)$.

---

## Proposed Extension

I propose a simple but direct experiment to explicitly demonstrate the sampling-dependence of observed phylogenies:

> **Fix the epidemic dynamics entirely, and vary only the sampling scheme. Compare the resulting genealogies.**

### Sampling Schemes

| Scheme | Definition |
|---|---|
| **Peak sampling** | Fixed number of samples drawn from a narrow time window around $\max(I_i(t))$ |
| **Uniform sampling** | Fixed number of samples drawn evenly across the full duration of the epidemic |

### What to Compare

For each strain, generate genealogies under both sampling schemes and compare:

- **TMRCA** (time to most recent common ancestor)
- **Tree depth**
- **Branching structure** (e.g., imbalance, internal branch lengths)
- **Coalescent rate trajectory** implied by the tree

---

## Expected Result

Because the epidemic dynamics are identical across conditions, any differences in tree structure arise purely from sampling design. We expect:

- **Peak sampling** → shallower trees, coalescent events concentrated near the present, limited view of early epidemic history
- **Uniform sampling** → deeper trees, coalescent events spread across the epidemic, better recovery of ancestral dynamics

This directly illustrates that the observed phylogeny is not the transmission process itself, but a **partial, sampling-dependent summary** of it.

---

## Significance

This experiment serves three purposes within the current project:

1. **Conceptual clarity**: Provides an explicit demonstration of the gap between phylogeny and transmission history, which motivates the use of epidemic-informed coalescent models in the first place.

2. **Interpretive support**: Helps explain why tree-based summaries may appear insensitive to certain model differences — the tree may simply not be capturing the relevant part of the epidemic.

3. **Low implementation cost**: The epidemic trajectories are already simulated. Only the sampling step needs to be modified.

---

## Proposed Figure

A single multipanel figure:

- **Panel A**: $I_1(t)$ and $I_2(t)$ trajectories with sampling windows marked (peak vs. uniform)
- **Panel B**: Genealogy for strain 1 under peak sampling
- **Panel C**: Genealogy for strain 1 under uniform sampling
- **Panel D** *(optional)*: Summary statistics (TMRCA, tree depth) across conditions

Branch colors can distinguish strain 1 and strain 2 lineages where applicable.

---

## One-Sentence Summary

> By holding the epidemic fixed and varying only the sampling design, we show that the observed phylogeny provides an incomplete and sampling-dependent view of the underlying transmission process — a finding that directly motivates epidemic-aware phylodynamic inference.
