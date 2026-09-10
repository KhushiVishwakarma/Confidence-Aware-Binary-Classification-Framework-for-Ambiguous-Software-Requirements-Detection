# Confidence-Aware Binary Classification Framework for Ambiguous Software Requirements Detection

This repository contains the reproducible experimental implementation associated with the ICCTRDA 2026 paper:

**Confidence-Aware Binary Classification Framework for Ambiguous Software Requirements Detection**

**Submission ID:** 358

## Experimental setup

- Dataset: `pure_labeled.csv`
- Total requirements: 6,725
- Task: binary classification (Clear = 0, Ambiguous = 1)
- Training: 4,692
- Validation: 1,017
- Test: 1,016
- Random seed: 42

## Models

1. Sentence-BERT (`all-MiniLM-L6-v2`) embeddings
2. Decision Tree
3. Random Forest
4. SVM
5. XGBoost
6. BERT (`bert-base-uncased`)

## Confidence-aware framework

BERT validation logits are calibrated using temperature scaling. A confidence threshold of **0.95** is frozen before final test evaluation:

- confidence >= 0.95 → automatic decision
- confidence < 0.95 → human review

## Evaluation

Standard model metrics:

- Accuracy
- Precision
- Recall
- F1
- ROC-AUC

Confidence-aware metrics:

- Coverage
- Selective Accuracy
- Risk
- Human Review Rate
- Expected Calibration Error (ECE)

## Repository structure

```text
notebooks/   Reproducible experiment notebook
data/        Dataset or instructions for obtaining it
results/     Generated CSV results
figures/     Generated figures
```

## Reproduction

Install dependencies:

```bash
pip install -r requirements.txt
```

Place the dataset at:

```text
data/pure_labeled.csv
```

Then open:

```text
notebooks/ConfidenceAware.ipynb
```

and run the notebook from top to bottom.

## Data note

Only redistribute `pure_labeled.csv` if its source and licensing terms permit redistribution. Otherwise, provide instructions for obtaining/reconstructing the dataset in `data/README.md`.
