![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# Cat Detection — YOLO26 Training

## Overview
This project trains a YOLO26n object detector on a custom cat detection dataset
using Ultralytics. The model detects cats in images and outputs bounding boxes
with confidence scores.

## Dataset
- 3,327 images with YOLO-format annotations (single class: cat)
- Split: 70% train / 15% val / 15% test
- Dataset stored on Google Drive (not committed to repo)
## Environment
- Training was done on **Google Colab** with a free **T4 GPU**
- Dataset was accessed via **Google Drive** (mounted with `drive.mount('/content/drive')`)
- Colab reduced training time to ~2 hours

## Model
- Architecture: YOLO26n (2.4M parameters)
- Pretrained on COCO, fine-tuned on cat detection dataset
- Training: 30 epochs, imgsz=640, batch=16, Colab T4 GPU
- Best checkpoint: `runs/cats_v1-5/weights/best.pt`
## Results
| Metric | Value |
|---|---|
| mAP@0.5 | 0.913 |
| mAP@0.5:0.95 | 0.730 |
| Precision | 0.906 |
| Recall | 0.858 |

## How to Reproduce
1. Clone the repo
2. Install dependencies:
```bash
pip install ultralytics 
```
3. Download the dataset from Google Drive and place it at `
DATA_CLEAN/`
4. Open `m6-04-assessment.ipynb` and run all cells

## Repository Structure
```
m6-04-assessment/
  m6-04-assessment.ipynb   # main notebook
  data.yaml                # dataset config
  .gitignore               # excludes data/ and large artefacts
  README.md
  runs/
    cats_v1-5/
      weights/
        best.pt            # best model checkpoint
```

### Definition of done (checklist)
- [x] Dataset inspection: image and label counts, class distribution, 6-image visualisation with boxes.
- [x] `data.yaml` and split text files created and validated.
- [x] YOLO26 variant (your choice of `n`/`s`/`m`/`l`/`x`) chosen with a written justification, trained for at least 30 epochs, training results logged.
- [x] Test-set metrics reported in a table (mAP@0.5, mAP@0.5:0.95, P, R).
- [x] Prediction visualisations on at least 6 test images, including failures.
- [x] Reflection written.
- [x] Notebook runs end-to-end without errors.
