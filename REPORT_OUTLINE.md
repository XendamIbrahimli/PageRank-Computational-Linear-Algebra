# PageRank report outline

The course handbook asks for an **8–12 page report** and a **12-minute presentation**. Keep the report focused on the PageRank formulation, the implementation, experiments, and interpretation. Do not add last year's Exercises 8 and 10 unless the professor explicitly assigns them this year.

## Suggested structure (8–12 pages)

1. **Introduction and objective (about 1 page)**  
   Explain the directed web graph and the goal of ranking pages from their incoming links. State the guiding question: how do graph structure and the damping parameter affect convergence and ranking stability?

2. **Mathematical formulation (1–2 pages)**  
   Define the directed graph, outdegree, link matrix, column-stochastic matrix, Google operator, damping parameter, personalization vector, and PageRank fixed-point/eigenvector equation. Explain why columns represent source pages in our convention.

3. **Dangling pages and ghost-node treatment (1 page)**  
   Explain why a dangling page gives a zero column. Show how the extra ghost node restores column-stochasticity. State clearly that the ghost is absorbing and that the displayed ordinary-page scores are renormalized after removing ghost mass. Mention that this differs from uniform dangling-mass redistribution.

4. **Numerical method and implementation (1–2 pages)**  
   Describe CSR sparse storage, Power Iteration, the L1 stopping criterion, the fixed-point residual, and the Arnoldi/ARPACK alternative. Explain why the dense Google matrix is never formed.

5. **Graph experiments and results (2–3 pages)**  
   Include the small verification graph, the rank-sink graph, the two-community graph, and the Hollins web graph. Report graph sizes, edges/nonzeros, dangling-page counts, stochasticity checks, PageRank rankings, convergence iterations, and residuals.

6. **Damping, solver comparison, sensitivity, and scaling (2–3 pages)**  
   Plot iteration count and subdominant eigenvalue magnitude against damping. Compare Power Iteration and Arnoldi by runtime, matrix–vector/operator applications, residual, and estimated workspace memory. Report the edge-perturbation L1 score change and Spearman rank correlation. Include the sparse storage/runtime scaling plot.

7. **Discussion, limitations, and conclusion (about 1 page)**  
   Interpret what the experiments show. Distinguish eigenvector residual from stability of ranking order. Discuss the ghost-node modeling choice, the machine dependence of runtime, and the fact that PageRank measures link-structure importance rather than page quality or truth.

8. **References and reproducibility**  
   Cite the course handbook, the PageRank literature, and the Hollins dataset source. State Python/NumPy/SciPy versions, random seed, and how to run the notebook.

## Figures and tables to use

- Diagram or schematic of the directed graph and column-index convention.
- Small-graph PageRank score tables.
- Damping parameter: iteration count and `|lambda_2|` / spectral gap.
- Power Iteration vs. Arnoldi comparison table.
- Edge-perturbation score comparison and Spearman correlation.
- Sparse storage/runtime versus graph size.
- Hollins top-10 PageRank table and graph statistics.
