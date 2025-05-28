# Amini Cocoa Contamination Challenge

**Team: Brain Blend**

This project was developed for the Amini Cocoa Contamination Challenge. The objective was to build lightweight machine learning models capable of detecting diseases in cocoa plant images—while generalizing to unseen diseases and operating efficiently on low-resource smartphones used by African farmers.

---

## 🧠 Challenge Overview

* **Goal**: Detect all visible plant diseases in images of cocoa leaves.
* **Constraints**:

  * Must generalize to unseen diseases.
  * Must run efficiently on low-resource smartphones.

---

## 🔄 ETL Process

* Used **StratifiedGroupKFold (10-fold)** for balanced cross-validation splits.
* Each fold's annotations were organized into YOLO-compatible directories:

  * `images/train`, `images/val`, `labels/train`, `labels/val`.

---

## 🧠 Modeling Approach

### Model Choice

* Selected **YOLO11s** (lightweight and optimized for edge devices).

### Training Strategy

* Trained on **folds 6, 7, and 8**.
* For each fold:

  * Split validation into two halves:

    * One half merged into training.
    * The other reserved for evaluation.
* Total training time: **8h 33min**.

### Validation Performance (Local mAP)

| Fold | mAP   |
| ---- | ----- |
| 6    | 0.760 |
| 7    | 0.789 |
| 8    | 0.806 |

---

## 🧪 Inference Strategy

### Ensemble

* Used **Weighted Box Fusion (WBF)** on all three trained models.

### Multi-Scale Inference

* Performed inference across multiple image sizes:

  ```
  [640, 800, 960, 1120, 1280, 1440]
  ```

---

## ⏱ Runtime Summary

| Task      | Time         |
| --------- | ------------ |
| Training  | 8h 33min     |
| Inference | 40min        |
| **Total** | **9h 13min** |

---

## 🧩 Interpretability

* Implemented **EigenCAM** to visualize model attention maps.
* Notebook: `Team_Brain_Blend_Interpretability_Report.ipynb`

---

## ⚙ How to Run the Notebooks

### Training

* Open: `Team_Brain_Blend_Training_Notebook.ipynb`
* Set dataset path (preferably use Kaggle for reproducibility).
* Run all cells to retrain the models.

### 🧪 Inference

* Open: `Team_Brain_Blend_Inference_Notebook.ipynb`
* Choose between:

  * **Pre-trained weights** from ZIP archive or Kaggle:

    * 📦 [Download from Kaggle Dataset](https://www.kaggle.com/datasets/stephenkolesh/yolo11s-6-7-8) 
  * **Custom-trained weights** from the training notebook.

---

## 📱 Compliance with Constraints

* YOLO11s models are optimized for edge deployment.
* Training (≤9h) and inference (≤3h) are within challenge limits.
* Ensemble predictions done within time constraints.
* Exportable to **ONNX** for mobile deployment.

---

## 🤝 Teammates

We worked on this project together as Team Brain Blend.

* **[koleshjr](https://github.com/koleshjr)**
* **[Sodiq](https://github.com/Sodiq179)**


