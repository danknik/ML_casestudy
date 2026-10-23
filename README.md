# NSD fMRI Decoding

A classical machine-learning pipeline for decoding broad COCO object supercategories from fMRI responses in the Natural Scenes Dataset (NSD).

## Project summary

This project uses preprocessed fMRI beta responses from NSD participant `subj01`. The task is to predict the dominant COCO supercategory of the natural image viewed on each trial.

- 12 COCO supercategories
- `nsdgeneral` ROI: 15,724 voxels
- Training: NSD Sessions 1-3
- Testing: held-out NSD Session 4
- 2,230 labeled trials total
- PCA: 1,000 components, retaining 90.92% of training variance

## Results

| Model | Top-1 accuracy | Top-5 accuracy |
|---|---:|---:|
| RidgeClassifier | 45.89% | 82.32% |
| Logistic Regression | **46.43%** | **85.00%** |

The 12-class top-1 chance level is 8.33%.

## Repository contents

```text
nsd_pipeline.ipynb
results/
  nsd.csv
  nsd_logistic_confusion_matrix.png
  nsd_logistic_per_class.csv
```

## Reproducibility

The notebook downloads prepared NSD beta data, applies the `nsdgeneral` ROI mask, maps NSD images to COCO annotations, creates dominant-supercategory labels, and evaluates RidgeClassifier and Logistic Regression.

Raw NSD data, COCO annotation archives, and derived feature matrices are intentionally excluded from this repository. NSD access requires agreeing to the dataset terms and completing the data-access form at <https://naturalscenesdataset.org/>.

## Requirements

```text
numpy
pandas
scipy
nibabel
scikit-learn
pycocotools
matplotlib
```
