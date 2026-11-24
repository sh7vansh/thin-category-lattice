# The Categorical and Geometric Structure of Subobject Lattices

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24506442.svg)](https://doi.org/10.5281/zenodo.24506442)
[![Lean 4](https://img.shields.io/badge/Lean%204-v4.35.0-blue)](https://leanprover.github.io/)
[![Mathlib 4](https://img.shields.io/badge/Mathlib-v4.35.0-green)](https://github.com/leanprover-community/mathlib4)
[![License](https://img.shields.io/badge/License-Academic%20Evaluation-orange)](LICENSE)

**Author:** Shivansh Singh  
**Formalization:** Lean 4 (`v4.35.0` with Mathlib, 0 `sorry` placeholders, standard core axioms `[propext, Classical.choice, Quot.sound]`)

---

## Overview

This repository contains the papers and machine-checked Lean 4 formalization for:
1. **[thin-category-lattice.md](thin-category-lattice.md)**: *The Categorical and Geometric Structure of Subobject Lattices*
2. **[supplementarylatticenotes.md](supplementarylatticenotes.md)**: *Supplementary Lattice Notes: Combinatorial Theory of Sub-Associahedral Embeddings*

### Core Mathematical Contributions

1. **Posets as Thin Categories & Signed Modularity Defects:**
   - Universal realization of meets and joins as categorical products and coproducts.
   - Idempotent categorical monads (`CategoryTheory.Monad`) from closure operators and Galois connections.
   - Analysis of the signed modularity defect $\Delta(A, B) = (\mathrm{rk}(A) + \mathrm{rk}(B)) - (\mathrm{rk}(A \vee B) + \mathrm{rk}(A \wedge B))$.
   - Completion of the associahedral face poset into a lattice $\widehat{P}_n$, evaluation of its signed defects, geometric face rank dimension matching, and preservation under surrounding extensions.

2. **Associahedra, Higher Associativity & Root Geometry:**
   - Machine-checked order isomorphism between partial bracketings and noncrossing diagonals ($P_n \simeq_o F_n$) for every arity $n \ge 2$.
   - Loday's convex realization: supporting-face order isomorphism, vertex/facet counts, extreme point classification, and actual affine dimension $n-2$.
   - Constructive two-sided equivalence $\mathrm{Root}_{A_n} \simeq \mathrm{Facet}_{K_{n+2}} \simeq \mathrm{Diagonal}(n)$.
   - $A_3 \leftrightarrow K_5$ specialization: classification into 6 pentagons (cyclic length 2) and 3 squares (cyclic length 3).
   - Discrete 1D Dirichlet–Cartan quadratic form on $\mathbb{Z}^n$, positive definiteness, and norm invariance $\langle v, v \rangle = 2$.

3. **Path Valuations, Directed Reassociations & Transfinite Filtrations:**
   - Path valuations into the travel monoid $(\mathbb{N}, +) \times \mathbf{U}_2(\mathbb{Z})$ tracking path friction alongside unipotent shear labels, with functorial concatenation.
   - Proof that all full bracketings of a fixed labelled chain yield the identical composite arrow and valuation.
   - Directed rotation graph on full bracketings, signed rotation paths, and proof of the pentagon obstruction showing route-dependence and triviality of any additive target quotient.
   - Ascending Loewy filtrations on semi-Artinian objects in universe-stratified abelian categories ($\mathrm{Type}(u+1)$ with $\mathrm{Type}(u)$ homs), stabilization at Loewy length $\Omega$, terminal reconstruction $L_\Omega \cong U_0$, vanishing residual colimits, and well-founded generator selection.

4. **Operadic Subtree Embeddings & Asymptotic Geometry:**
   - Exact operadic factorization $\#\{T \in \mathcal{T}_N \mid I \triangleleft T\} = C_{k-1} C_{N-k}$ and global multiplicity $\Phi(N, k) = C_{k-1} \binom{2(N-k)}{N-k}$.
   - Exact variance and linear scaling $\mathrm{Var}(n_k)(N) = \mathcal{O}(N)$ with Chebyshev concentration.
   - Aldous's fringe law: single-shape equidistribution $q_k = 4^{-(k-1)}$, finite-pattern universality ($\mathbb{P}(n_S(T) \ge 1) \to 1$), and total fringe probability mass normalization $\sum_{k=2}^\infty \sum_{S \in \mathcal{T}_k} 4^{-(k-1)} = 1$.
   - Boundary tower $K_N \hookrightarrow K_{N+1}$, $(N-2)$-regularity of the Tamari graph, and asymptotic collapse of quadratic Tamari chain height relative to exponential horizontal edge expansion ($\binom{N}{2} / |\mathrm{Edge}(K_N)| \to 0$).

---

## Repository Structure

```text
thin-category-lattice/
├── LICENSE
├── README.md
├── CITATION.cff
├── .zenodo.json
├── thin-category-lattice.md            # Main research paper
├── supplementarylatticenotes.md        # Companion notes on subtree embeddings & fringe laws
└── math_project/                       # Lean 4 project root
    ├── lean-toolchain                  # pinned to leanprover/lean4:v4.35.0
    ├── lakefile.toml                   # Lake package configuration
    ├── lake-manifest.json              # Locked dependencies (Mathlib v4.35.0)
    └── MathProject/
        ├── AssociahedralComposition.lean
        ├── AssociahedralTrees.lean
        ├── AssociahedralRealization.lean
        ├── AssociahedralFaces.lean
        ├── AssociahedralDimension.lean
        ├── AssociahedralFacetProducts.lean
        ├── AssociahedralSignedDefects.lean
        ├── DirectedReassociation.lean
        ├── AssociahedralStructuralBridges.lean
        ├── FunctorialGeometry.lean
        ├── AssociahedralSubtreeEmbeddings.lean
        ├── AssociahedralFringeLaw.lean
        ├── AssociahedralBoundaryTower.lean
        ├── CheckAssociahedra.lean
        ├── CheckFacetProducts.lean
        ├── CheckPathValuations.lean
        ├── CheckSignedStructures.lean
        ├── CheckCellularFiltrations.lean
        └── CheckSubtreeEmbeddings.lean
```

---

## Building and Verifying the Lean 4 Proofs

### Prerequisites

Ensure you have [elan](https://github.com/leanprover/elan) installed:
```bash
curl https://raw.githubusercontent.com/leanprover/elan/master/elan-init.sh -sSf | sh
```

### Build Instructions

1. Enter the Lean project directory:
   ```bash
   cd math_project
   ```

2. Download pre-built Mathlib cache (recommended):
   ```bash
   lake exe cache get
   ```

3. Build the core mathematical library and check suites (matching the papers):
   ```bash
   # Build main theory modules
   lake build MathProject

   # Run paper check & audit suites
   lake build MathProject.CheckAssociahedra MathProject.CheckFacetProducts MathProject.CheckPathValuations
   lake build MathProject.CheckSignedStructures MathProject.CheckCellularFiltrations
   lake build MathProject.CheckSubtreeEmbeddings
   ```

All theorems compile cleanly with **0 `sorry` placeholders** and rely solely on the standard axioms `[propext, Classical.choice, Quot.sound]`.

---

## Citation

```bibtex
@misc{singh2026thincategorylattice,
  author    = {Shivansh Singh},
  title     = {The Categorical and Geometric Structure of Subobject Lattices},
  year      = {2026},
  publisher = {Zenodo},
  doi       = {10.5281/zenodo.24506442},
  url       = {https://doi.org/10.5281/zenodo.24506442}
}
```

---

## License

See [LICENSE](LICENSE) for terms of use (Academic and Scientific Evaluation).
