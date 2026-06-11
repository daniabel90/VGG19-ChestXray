# VGG19 — Pediatric Chest X-Ray Classification

[![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?style=flat&logo=python&logoColor=white)](https://python.org)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-FF6F00?style=flat&logo=tensorflow&logoColor=white)](https://tensorflow.org)
[![Kaggle](https://img.shields.io/badge/Dataset-NIH_Chest_X--Ray14-20BEFF?style=flat&logo=kaggle&logoColor=white)](https://www.kaggle.com/datasets/nih-chest-xrays/data)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat)](LICENSE)
[![Stars](https://img.shields.io/github/stars/daniabel90/VGG19-ChestXray?style=flat)](https://github.com/daniabel90/VGG19-ChestXray)

> **Part of the [PneumoCNN4](https://github.com/daniabel90) comparative study** — benchmarking 8 CNN architectures for pediatric chest X-ray multi-label classification  
> 🎓 Master's thesis — Université Saad Dahleb Blida 1, 2025 | Author: [Dania Beloufa](https://github.com/daniabel90)

---

## 🔬 About this Model

Deeper VGG variant with 19 layers for enhanced feature extraction on chest X-ray pathologies.

Deeper than VGG16, VGG19 captures more abstract features at the cost of slightly higher computational demand.

**Task:** Multi-label classification of 14 chest pathologies from frontal-view X-rays  
**Dataset:** NIH Chest X-Ray14 (112,120 images, 30,805 patients)

---

## 📊 Results

<div align="center">

| Metric | Score |
|:------:|:-----:|
| 🎯 **Test Accuracy** | **86.8%** |
| 📈 **Mean AUC** | **0.80** |
| ⚖️ **Macro F1** | **0.73** |

</div>

---

## 🏗️ Architecture

| Property | Value |
|----------|-------|
| **Model** | VGG19 |
| **Layers** | 19 weight layers (16 conv + 3 FC) |
| **Pre-training** | ImageNet |
| **Input size** | 224 × 224 × 3 |
| **Output** | 14-class sigmoid (multi-label) |

---

## 🗂️ Repository Structure

```
VGG19-ChestXray/
├── 📓 vgg19_chest_xray.ipynb    ← Full training + evaluation notebook
├── 📋 requirements.txt                    ← Python dependencies  
└── 📖 README.md
```

---

## 🚀 Quick Start

```bash
# 1. Clone
git clone https://github.com/daniabel90/VGG19-ChestXray.git
cd VGG19-ChestXray

# 2. Install dependencies
pip install -r requirements.txt

# 3. Download dataset (requires Kaggle API)
kaggle datasets download -d nih-chest-xrays/data
unzip data.zip -d data/

# 4. Launch notebook
jupyter notebook vgg19_chest_xray.ipynb
```

---

## 🔄 Pipeline Overview

```
NIH Chest X-Ray14 (112,120 images)
         │
         ▼
   Preprocessing: resize 224×224, normalize [0,1]
         │
         ▼
   Augmentation: rotation ±10°, horizontal flip, zoom 10%
         │
         ▼
   VGG19 (ImageNet weights)
         │
         ▼
   Custom head: GAP → Dense(512) → BN → Dropout → Dense(256) → Sigmoid(14)
         │
         ▼
   Phase 1: Feature extraction (25 epochs, frozen base)
         │
         ▼
   Phase 2: Fine-tuning (10 epochs, top 40% unfrozen)
         │
         ▼
   Evaluation: per-class AUC, ROC curves, Grad-CAM
```

---

## 🏥 14 Pathology Classes

| | Pathology | | Pathology |
|--|-----------|--|-----------|
| 1 | Atelectasis | 8 | Pneumothorax |
| 2 | Cardiomegaly | 9 | Consolidation |
| 3 | Effusion | 10 | Edema |
| 4 | Infiltration | 11 | Emphysema |
| 5 | Mass | 12 | Fibrosis |
| 6 | Nodule | 13 | Pleural Thickening |
| 7 | Pneumonia | 14 | Hernia |

---

## 🔗 Full Comparative Study

| Model | Accuracy | Mean AUC | Repo |
|-------|----------|----------|------|
| VGG16 | 87.3% | 0.81 | [VGG16-ChestXray](https://github.com/daniabel90/VGG16-ChestXray) |
| VGG19 | 86.8% | 0.80 | [VGG19-ChestXray](https://github.com/daniabel90/VGG19-ChestXray) |
| ResNet50 | 88.2% | 0.83 | [ResNet50-ChestXray](https://github.com/daniabel90/ResNet50-ChestXray) |
| ResNet101 | 88.6% | 0.83 | [ResNet101-ChestXray](https://github.com/daniabel90/ResNet101-ChestXray) |
| DenseNet121 | 89.1% | 0.84 | [DenseNet121-ChestXray](https://github.com/daniabel90/DenseNet121-ChestXray) |
| EfficientNetB0 | 90.2% | 0.86 | [EfficientNetB0-ChestXray](https://github.com/daniabel90/EfficientNetB0-ChestXray) |
| **HybridCNN ⭐** | **92.1%** | **0.89** | [HybridCNN-ChestXray](https://github.com/daniabel90/HybridCNN-ChestXray) |

---

## 📚 Citation

```bibtex
@mastersthesis{beloufa2025pneumocnn4,
  author  = {Beloufa, Dania},
  title   = {Comparative Analysis of CNN Architectures for Pediatric Chest X-Ray Classification},
  school  = {Université Saad Dahleb Blida 1},
  year    = {2025},
  note    = {MSc Electronic Instrumentation — Distinction}
}
```

---

## 👩‍💻 Author

**Dania Beloufa** — Biomedical Engineer & MSc in Electronic Instrumentation (Distinction, 2025)  
Université Saad Dahleb Blida 1, Algeria  
🔗 [GitHub @daniabel90](https://github.com/daniabel90)

---

<div align="center">⭐ Star this repo if it's useful for your research!</div>
