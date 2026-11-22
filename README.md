# ENG2440 Assignment 3: BBBP molecular classification

This folder contains the notebook for Sections A–G: molecular inspection/cleaning, graph construction, fixed random and scaffold splits, fingerprint logistic regression, a bond-aware GINE model, final evaluation, and error/similarity analysis.

## Environment and run order

The recorded environment is Python 3.12.2 on macOS, using CPU execution with two PyTorch threads. `requirements.txt` records installed package versions. The notebook is verified in this existing environment.

From this folder, create an environment and start Jupyter:

```sh
python3.12 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python -m ipykernel install --user --name eng2440-a3 --display-name "ENG2440 A3"
python -m jupyterlab
```

Open `YomnaElnikety_ENG2440_Assignment3.ipynb`, select that kernel, and choose **Restart Kernel and Run All Cells**. Run from this folder because data and artifact paths are relative to it. No supporting `.py` files are required. All implementations are inside the notebook.

The first run downloads BBBP through PyG's MoleculeNet loader and requires internet access. Later runs reuse `data/`. Do not manually download or publish the dataset. Section E trains six small models; a complete run can take several minutes. Rerunning from a fresh kernel reproduces the fixed experiment and replaces generated artifacts. Do not use the test results to revise models or thresholds.

## Outputs

- The notebook contains executed tables, molecular drawings, learning curves, final ROC/PR plots, and confusion matrices.
- `splits_seed42.npz`: cleaned-position split arrays.
- `artifacts/gnn/`: six checkpoints, settings, training histories, validation scores, and learning curves.
- `artifacts/final_evaluation/`: frozen baseline models, test probabilities, metric/comparison tables, and test plots.
- `artifacts/error_analysis/`: four molecular error/neighbor pairs and their figure.

All split indices refer to positions in the cleaned dataset, original dataset indices are stored separately in `clean_idx`. GNN seeds 42/43/44 vary training only; the split seed remains 42. PR-AUC is trapezoidal area, and standard deviations are sample SDs over three GNN runs, not confidence intervals. The notebook contains code, saved outputs and section headings; interpretation, experiment settings and references are in the accompanying report and repository.

## Submission status

The report is `YomnaElnikety_25011181_ENG2440_A3.pdf` (six main pages plus one references page).

