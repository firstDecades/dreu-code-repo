# Kagome Fermi-Hubbard Agent Guidelines

## 1. Solver Selection Strategy
- **N <= 12 sites:** Execute `solve_exact_diagonalization` directly.
- **N > 12 sites:** 
  1. Break system into sub-clusters (3, 6, or 9 site motifs).
  2. Compute sub-clusters using `solve_exact_diagonalization` or `solve_mps_tenpy`.
  3. Reconstruct full matrices via `extrapolate_from_subclusters`.

## 2. Storage Protocols
- ALWAYS query `query_databank` before running expensive calculations.
- Save newly verified exact matrices using `save_to_databank`.