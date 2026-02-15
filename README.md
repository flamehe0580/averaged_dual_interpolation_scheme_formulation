# Quasi-C¹ Interpolation Scheme for Structural Analysis

## Overview

This repository provides the complete mathematical derivation and **continuity verification** of the **averaged dual-path interpolation scheme**, a novel approach to constructing quasi-C¹ continuous shape functions for eight-node quadrilateral elements. This formulation ensures derivative continuity across element boundaries while permitting internal discontinuity along a predefined partition, enabling smooth stress fields without post-processing in finite element analysis of beams and plates.

The derivation presented here corresponds to Section 2.1 of our paper: *"A Unified Quasi-C¹-PIM Formulation for Static and Dynamic Analysis of Beams and Plates with Arbitrary Cross-Sections"* (submitted to *Applied Sciences*).

## Repository Contents

| File | Description |
|------|-------------|
| `path1.nb` | Mathematica notebook detailing the **η-first interpolation path** (Path 1), including shape function derivation and continuity verification. |
| `path2.nb` | Mathematica notebook detailing the **ξ-first interpolation path** (Path 2), including shape function derivation and continuity verification. |

## The Averaged Dual-Path Interpolation Scheme

The proposed quasi-C¹ interpolation scheme consists of six key steps:

1. **Path 1 (η-first)**: Interpolate along η at fixed ξ = -1, 0, 1, then along ξ using Hermite interpolation
2. **Path 2 (ξ-first)**: Interpolate along ξ at fixed η = -1, 0, 1, then along η using Hermite interpolation
3. **Averaging**: The final shape functions are obtained as the average of the two independent paths: `H₂₄ = (H₂₄⁽¹⁾ + H₂₄⁽²⁾)/2`

This dual-path approach ensures:
- **C⁰ continuity** across all element boundaries
- **C¹ continuity** of first derivatives across external element boundaries
- **Inherently smooth stress fields** without post-processing requirements

## Key Features of the Derivation

The Mathematica notebooks provide:

- Complete formulation of 24 shape functions for each interpolation path
- **Systematic verification of C⁰ continuity** at element interfaces for both function values and derivatives
- **Systematic verification of C¹ continuity** across external element boundaries, demonstrating how the two paths complement each other to achieve global continuity
- Symbolic manipulation for clarity and reproducibility

### Continuity Verification Highlights

The notebooks explicitly demonstrate:

- For **left-right adjacent elements**: C⁰ continuity of function values and C¹ continuity of ξ-derivatives
- For **top-bottom adjacent elements**: C⁰ continuity of function values and, crucially, how Path 2 compensates for the discontinuity in Path 1 to achieve overall C¹ continuity
- The complementary nature of the two interpolation paths in achieving global derivative continuity

## Usage

To explore the derivation and verification:

1. Open the notebooks in Mathematica (version 13.0 or later recommended)
2. Evaluate the cells sequentially to follow the step-by-step derivation
3. Examine the continuity verification sections to confirm the element's properties at interfaces
4. Modify parameters or extend the formulation as needed for your research

## Citation

If you use this derivation in your research, please cite our paper:

> He, G.; Li, X.; Li, X. A Unified Quasi-C¹-PIM Formulation for Static and Dynamic Analysis of Beams and Plates with Arbitrary Cross-Sections. *Applied Sciences* (submitted).

For direct reference to this repository:
