# Leaf Morphometric Analysis

This repository contains a MATLAB workflow for **leaf morphometric analysis** using RGB photographs of leaves placed on a plain background with a reference coin. The project follows a multi‑stage image processing pipeline to segment leaf/coin regions, clean masks, compute histograms, annotate boundaries and centroids, and finally measure leaf morphometrics (length, width, area, perimeter) in real‑world units. It also includes a multi‑leaf batch analysis pipeline for ranking leaves and estimating damage percentage.

## Project Overview

The workflow is based on the following tasks (from the assignment brief):

1. **Threshold segmentation** of leaf and coin using RGB band‑pass thresholds.
2. **Morphological clean‑up** of binary masks (closing and hole filling).
3. **RGB histogram plots** for segmented objects.
4. **Boundary tracing** and visual annotation.
5. **Centroid/medoid calculation** and **Green Leaf Index (GLI)** annotation.
6. **Morphometric measurement** using a coin for scale calibration.
7. **Batch multi‑leaf analysis** including counting leaves, ranking by size/GLI, cropping, and damage metrics.

The main implementation is stored in `IP_tasks.mlx` (MATLAB live script), with reference material and task descriptions in the provided Word documents.

## Repository Contents

```
.
├── IP_tasks.mlx              # MATLAB live script with all tasks
├── Images/                   # Input image dataset (single + multi‑leaf)
│   ├── Leaf_coin.jpg         # Single leaf + coin image
│   ├── 1234.jpg ...          # Multi‑leaf samples
├── Leaf_Analysis.docx        # Full report / explanation
├── Problem Statement.docx    # Assignment brief
└── README.md                 # You are here
```

## Requirements

- **MATLAB** (R2020b+ recommended)
- Image Processing Toolbox

## How to Run

1. Open MATLAB and set the working directory to this repo root.
2. Open `IP_tasks.mlx`.
3. Run each section in sequence (the script is organized by tasks).
4. Ensure the `Images/` folder is accessible (contains the dataset).

### Single‑Image Workflow (Leaf + Coin)

The script performs the following on `Images/Leaf_coin.jpg`:

- Color thresholding for leaf and coin segmentation
- Morphological closing to fix holes and remove noise
- RGB histogram plots for each object
- Boundary overlay on the original image
- Centroid and medoid annotation
- GLI calculation
- Real‑world measurements based on coin size

### Multi‑Leaf Batch Workflow

For batch analysis, the script:

- Iterates over all images in `Images/`
- Segments leaves by multiple color thresholds (e.g., green/yellow)
- Separates coin regions by circularity
- Measures morphometrics per leaf
- Estimates **damage percentage** (hole area inside leaf masks)
- Crops each detected leaf
- Outputs summary metrics to CSV

## Dataset

The `Images/` folder includes:

- One **single‑leaf + coin** image (`Leaf_coin.jpg`)
- Multiple **multi‑leaf images** (`1234.jpg`, `12345.jpg`, etc.) containing 4–5 leaves

These images are used for threshold tuning and batch validation.

## Outputs

When executed in MATLAB, the script produces:

- Binary masks for leaf/coin
- Cleaned masks after morphology
- Histogram plots per object
- Annotated images with boundaries, centroid, medoid, GLI
- Cropped leaf images (batch mode)
- CSV summary with leaf metrics (batch mode)

## Notes

- Threshold values are based on MATLAB’s **Color Threshold App** and are included in the report.
- Morphological structuring element sizes may need tuning for different lighting conditions or leaf species.
- Batch pipeline assumes image filenames indicate the number of leaves (used for ranking in the script).

## References

- MATLAB Image Processing Toolbox documentation
- Assignment brief and report included in this repo

---

If you want additional automation (e.g., command‑line execution, Python re‑implementation, or CI checks), feel free to request enhancements.
