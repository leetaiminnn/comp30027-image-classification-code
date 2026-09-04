# COMP30027 Project 2 — Image Classification (full code)

> Write-up with figures and results:
> https://github.com/leetaiminnn/coarse-to-fine-image-classification

Submission for Project 2 (2026 S1). Two tasks:
- **Task 1**: 10 animal categories (coarse)
- **Task 2**: 10 bird species (fine-grained)

## Files

```
README.md                          this file
code/project2.ipynb                main notebook (all phases)
outputs/task1_submission.csv       Kaggle predictions for Task 1
outputs/task2_submission.csv       Kaggle predictions for Task 2
```

## Environment

Python 3.11 + the following packages:

```
pip install numpy pandas matplotlib seaborn scikit-learn pillow tqdm jupyter
pip install torch torchvision --index-url https://download.pytorch.org/whl/cpu
```

CPU is fine. ResNet50 feature extraction takes a few minutes the first time
and is cached, so re-runs are fast.

## How to run

1. Open `code/project2.ipynb` in Jupyter or VS Code.
2. `PROJECT_ROOT` is detected automatically (the repository root). Put the two
   dataset folders (`task1_data/task1_data`, `task2_data/task2_data`) in the
   repository root before running.
3. Run all cells from top to bottom. Phase 6 writes the two Kaggle CSV files
   to `outputs/`.

The notebook is organised in 6 phases:
- Phase 1: data loading and EDA
- Phase 2: baseline models on the 3 provided feature blocks
- Phase 3: ResNet50 feature extraction
- Phase 4: final models (LR, SVM, Random Forest) on CNN features
- Phase 4.5: GridSearchCV on Task 2 Random Forest
- Phase 5: error analysis (confusion matrix, per-class F1)
- Phase 6: generate the two Kaggle CSV files

## Best models (used for Kaggle CSV)

| Task | Model | Features | 5-fold CV accuracy |
|---|---|---|---|
| Task 1 | Logistic Regression | ResNet50 embedding (2048-d) | 91.5% |
| Task 2 | Random Forest | ResNet50 + 3 provided blocks (2267-d) | 86.3% |

Both submissions are produced in Phase 6 of the notebook.
