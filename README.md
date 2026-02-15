# Quasi-C¹ Interpolation Scheme for Structural Analysis

## Overview

This repository provides the complete mathematical derivation and **continuity verification** of the **averaged dual-path interpolation scheme**, a novel approach to constructing quasi-C¹ continuous shape functions for eight-node quadrilateral elements. This formulation ensures derivative continuity across element boundaries while permitting internal discontinuity along a predefined partition, enabling smooth stress fields without post-processing in finite element analysis of beams and plates.

The derivation presented here corresponds to Section 2.1 of our paper: *"A Unified Quasi-C¹-PIM Formulation for Static and Dynamic Analysis of Beams and Plates with Arbitrary Cross-Sections"* (submitted to *Applied Sciences*).

## Repository Contents

| File | Description |
|------|-------------|
| `path1.nb` | Mathematica notebook detailing the **η-first interpolation path** (Path 1), including shape function derivation and continuity verification. |
| `path2.nb` | Mathematica notebook detailing the **ξ-first interpolation path** (Path 2), including shape function derivation and continuity verification. |

<!--新增部分开始-->
### Cross-Sectional Property Matrices

| File | Description |
|------|-------------|
| `cross-sectional property matrices/cross-sectional property matrices_v2.0.nb` | Mathematica notebook for generating the cross-sectional property matrices **m₀** (mass matrix) and **k₀** (stiffness matrix), which are essential for the unified beam-plate formulation. |
| `cross-sectional property matrices/quadrilateral mesh.xlsx` | Excel file containing the quadrilateral mesh data of the cross-section. This file serves as the input data source for `cross-sectional property matrices_v2.0.nb`. |
<!--新增部分结束-->

## The Averaged Dual-Path Interpolation Scheme

The proposed quasi-C¹ interpolation scheme consists of six key steps:

1. **Path 1 (η-first)**: Interpolate along η at fixed ξ = -1, 0, 1, then along ξ using Hermite interpolation
2. **Path 2 (ξ-first)**: Interpolate along ξ at fixed η = -1, 0, 1, then along η using Hermite interpolation
3. **Averaging**: The final shape functions are obtained as the average of the two independent paths: `H₂₄ = (H₂₄⁽¹⁾ + H₂₄⁽²⁾)/2`

This dual-path approach ensures:
- **C⁰ continuity** across all element boundaries
- **C¹ continuity** of first derivatives across external element boundaries
- **Inherently smooth stress fields** without post-processing requirements

<!--新增部分开始-->
## Cross-Sectional Property Matrices

The `cross-sectional property matrices` folder contains essential components for the unified beam-plate formulation:

- **`cross-sectional property matrices_v2.0.nb`**: This Mathematica notebook computes the cross-sectional property matrices **m₀** (mass matrix) and **k₀** (stiffness matrix) based on the quasi-C¹ interpolation scheme. These matrices are fundamental to the dimensional reduction procedure described in Section 2.2 of our paper, as they encapsulate the cross-sectional geometry and material properties into a compact 1D formulation.

- **`quadrilateral mesh.xlsx`**: This Excel file provides the quadrilateral mesh data of the cross-section, including nodal coordinates and element connectivity. It serves as the input data source for the property matrices notebook. The mesh discretization follows the eight-node quadrilateral element formulation established in the main derivation.

### Role of m₀ and k₀ in Structural Analysis

The cross-sectional property matrices play a pivotal role in the unified formulation:

- **Stiffness matrix k₀**: Encodes the cross-sectional resistance to deformation, enabling accurate prediction of displacements and stresses under static and dynamic loads.
- **Mass matrix m₀**: Captures the inertial characteristics of the cross-section, essential for dynamic analysis including free vibration and transient response.

By computing these matrices once per cross-section, the full 3D problem is reduced to an efficient 1D analysis along the beam axis, achieving 85-95% reduction in degrees of freedom while maintaining 3D solution fidelity.
<!--新增部分结束-->

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

<!--新增部分开始-->
To generate the cross-sectional property matrices:

1. Open `cross-sectional property matrices/quadrilateral mesh.xlsx` to review or modify the mesh data
2. Run `cross-sectional property matrices/cross-sectional property matrices_v2.0.nb` in Mathematica
3. The notebook will compute **m₀** and **k₀** based on the provided mesh and the quasi-C¹ interpolation formulation
<!--新增部分结束-->

## Citation

If you use this derivation in your research, please cite our paper:

> He, G.; Li, X.; Li, X. A Unified Quasi-C¹-PIM Formulation for Static and Dynamic Analysis of Beams and Plates with Arbitrary Cross-Sections. *Applied Sciences* (submitted).

For direct reference to this repository:
