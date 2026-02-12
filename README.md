# 🌸 Flower Classifier
---
пипец, я ща обнаружил, что этот датасет запрещен... аааааааааааааааааааааааа
## 📋 Problem statement

To develop a system for classifying color images into 4 categories.  
**Key objective:** close the retake and receive embeddings of images for future expansion of functionality.

### Data format
- **Entrance:** Image (jpg/png)
- **Exit:** JSON with the predicted class

### Quality metrics
- Accuracy
- F1-score
- Cross-Entropy

---

## 📊 Dataset

A public dataset is being used **[Flowers Recognition](https://www.kaggle.com/datasets/alxmamaev/flowers-recognition )** with Kaggle.

**Features:**
- 2,871 images
- 4 classes: `daisy`, `roses`, `dandelion`, `sunflowers`
- ~700 images per class
- Resolution: ~320×240 pixels (different aspect ratio)
- Sources: Flickr, Google Images, Yandex Images

**Partitioning:**
- Training sample
- Validation sample
- Test sample

*The division is done randomly.*

---

## 🧠 Modeling

### 🔹 Basic approach (Baseline)

| Component | Details |
|--------------------|----------------------------------------|
| Preprocessing | Resize, normalization, transformations |
| Backbone           | RexNet-150 (pretrained on ImageNet)   |
| Classifier | Fully connected layer into 4 classes |
| Loss function | `CrossEntropyLoss`                   |
| Validation | Standard on deferred sampling |

### 🔹 Main model

| Component | Details |
|--------------------|----------------------------------------|
| Backbone           | RexNet-150 (pretrained on ImageNet)    |
| Loss function | `CrossEntropyLoss` + `CosineEmbeddingLoss` |
| Embeddings | Are saved for future reference |

---

## 🛠 Tools and infrastructure

| Tool | Purpose |
|------------|---------------------------------------------|
| **Hydra**  | Managing training configs |
| **MLflow** | Logging of parameters, metrics, and models |
| **Seed** | Fixing for reproducibility of results |

---

## 🚀 Integration

The system is supplied in one of two formats:

1. **REST service** — deploying the model via the API
2. **Package** — an encapsulated integration solution

Both options are configured via Hydra and logged into MLflow.

---

## ✅ Reproducibility requirements

- Fixed `random_seed` for all libraries (Python, NumPy, PyTorch)
- All experiment parameters are set in the Hydra YAML configs
- Each launch is logged in MLflow with the ability to compare experiments

---
