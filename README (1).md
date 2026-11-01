# Modularity on the Karate Club Graph (DSC212, Graph Theory Module)

Recursive spectral modularity bisection implemented from scratch with NumPy, NetworkX and Matplotlib on Zachary's Karate Club network, followed by node-metric tracking (degree, betweenness, closeness, clustering) after every split.

**Author:** Aditya Sarikar, MIT Vishwaprayag University, Solapur

## Files

| File | Description |
|---|---|
| `dsc212-karate-club-modularity.ipynb` | The notebook, already executed. All outputs and all 10 figures are embedded, so they show directly on GitHub |
| `README.md` | This file |

## How to run

```bash
pip install numpy "networkx>=3.0" matplotlib jupyter
jupyter notebook dsc212-karate-club-modularity.ipynb   # then: Kernel -> Restart & Run All
```

The notebook needs no input files and no internet connection, is deterministic (fixed layout seed, no random numbers) and runs in about 10 seconds. When run, it also saves PNG copies of the figures into a `figures/` folder next to the notebook.

Tested with Python 3.13, NumPy 2.5.3, NetworkX 3.7, Matplotlib 3.11.2.

## Result in brief

* 4 accepted splits give **5 communities**, modularity **Q = 0.4094**:
  `{8, 9, 14, 15, 18, 20, 22, 23, 26, 29, 30, 32, 33}`, `{0, 1, 2, 3, 7, 12, 13, 17, 19, 21}`, `{4, 5, 6, 10, 16}`, `{24, 25, 27, 28, 31}`, `{11}`.
* The first split (leading eigenvalue 4.977, Q = 0.3715) reproduces Zachary's recorded factions for 33 of 34 members; node 8 is the only exception.
* The handout's gain formula is exact only for the first split. The notebook reports the exact gain next to it, adds two transparent safeguards that can only veto a split, and checks the accumulated gains against an independently computed final modularity (Section 6).
* 115 validation checks (symmetry, dimensions, eigen-consistency, valid partition, gains, metrics against their definitions, every number quoted in the discussion) are run inside the notebook and all pass.

## References

* Newman, M. E. J. (2006). Modularity and community structure in networks. *PNAS* 103(23), 8577-8582.
* Zachary, W. W. (1977). An information flow model for conflict and fission in small groups. *Journal of Anthropological Research* 33(4), 452-473.
