# Homework 1 — PageRank

A compact, reproducible Python/Jupyter project based on the PageRank project brief in the *Computational Linear Algebra for Large-Scale Problems* handbook. It uses the senior's previous-year notebook as a reference, but does not assume that last year's Exercise 8 or Exercise 10 are current-year requirements.

## Files

- `PageRank_HW1.ipynb` — main notebook with mathematical formulation, implementation, experiments, tables, and plots.
- `data/dataset1.txt` — four-page directed graph from the reference repository.
- `data/dataset2.txt` — five-page graph containing two closed groups (rank-sink example) from the reference repository.
- `data/community_graph.txt` — small directed graph with two internally connected groups joined by two directed bridges.
- `requirements.txt` — Python dependencies.
- `REPORT_OUTLINE.md` — suggested structure for the final 8–12 page report.

## Run the project

Use Python 3.10 or newer. From this folder, create and activate a virtual environment, then install dependencies:

```bash
python3 -m venv .venv
source .venv/bin/activate        # Linux / WSL / macOS
# .venv\Scripts\Activate.ps1  # Windows PowerShell
python -m pip install -r requirements.txt
```

Start Jupyter:

```bash
python -m jupyter notebook
```

Open `PageRank_HW1.ipynb`, select the `.venv` Python kernel, and use **Run All**. In VS Code, install the Microsoft Python and Jupyter extensions and select `.venv/bin/python` when connected to WSL/Linux.

## Hollins real-graph data

The notebook attempts to download the Hollins dataset automatically. If the download is blocked, download `hollins.dat` from:

`https://raw.githubusercontent.com/Gianbattistabsn/ComputationalLinearAlgebra/main/HW1/hollins.dat`

Save it as `data/hollins.dat` and rerun the Hollins section. The three synthetic datasets are included locally and can be run without internet access. The real-graph experiment must still be completed and its results added to the report before final submission.

## What the notebook covers

1. Directed graphs and sparse link matrices.
2. Dangling-page handling using the single ghost-node construction from the senior's reference submission, with a column-stochasticity check.
3. Sparse Power Iteration with an L1 stopping test and fixed-point residual.
4. Rank-sink, weak-community, and dangling-page examples.
5. Damping-parameter experiments related to the subdominant eigenvalue and spectral gap.
6. Comparison of Power Iteration with an Arnoldi/ARPACK solver, including runtime, operator applications, and estimated workspace.
7. Edge-perturbation sensitivity measured using the L1 score difference and Spearman rank correlation, plus a controlled near-tie illustration.
8. Sparse-scaling experiment.
9. Hollins real-graph analysis when the data file is available.

## Modeling choice: the ghost node

Each dangling page points to one artificial ghost node, and the ghost node points to itself. The Google operator is applied without forming a dense teleportation matrix. For display, the ghost component is removed and ordinary-page scores are renormalized. This is a modeling choice and is **not identical** to the common convention that redistributes dangling-page mass over the ordinary pages. The report should state and discuss this distinction rather than claiming equivalence.

## Current validation status

- The notebook has been executed from a clean kernel using the included synthetic datasets.
- The Hollins dataset download was unavailable in the preparation environment because outbound network/DNS access was blocked; its numerical results are therefore not included yet.
- Runtime measurements depend on the machine. The solver workspace figures are estimates, not measurements of total process memory.
- The course handbook also asks for an 8–12 page report and a 12-minute presentation. Those deliverables remain to be prepared after collecting the real-graph results.
