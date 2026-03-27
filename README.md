# Landmark Recognition in Azerbaijan (CSCI 4701)

This project focuses on training a Convolutional Neural Network (CNN) to classify five landmarks in Azerbaijan using transfer learning and data augmentation. The dataset was self-collected, preprocessed, and uploaded to Hugging Face.

---

## 📌 Project Overview

* **Course**: CSCI 4701 – Deep Learning  
* **Team**: Team 5  
* **Topic**: Landmark Recognition in Azerbaijan  
* **Model**: ResNet-18 (Pretrained on ImageNet)  
* **Classes**:  
  - Maiden Tower  
  - Deniz Mall  
  - Shirvanshahlar  
  - Dede Gorgud  
  - Heydar Aliyev Center  

---

## 🗃️ Dataset Description

**📤 Dataset URL**: [Hugging Face – Azerbaijan Landmarks Dataset](https://huggingface.co/datasets/khaleed-mammad/azerbaijan-landmarks-dataset)

### ✅ Data Collection & Processing

* Images were collected collaboratively by Team 5 and Team 1.
* We divided tasks: some members captured daytime, others nighttime images.
* All images were originally in `.heic` format and were converted to `.jpg`.
* After labeling and folder organization, the dataset was uploaded to Hugging Face.

### 📊 Stats

* Dataset size: \~586 images in train & \~152 images in test (738 in total)
* Format: JPG
* Classes: 5 (One folder per class in train/ and test/)

---

## 🧠 Model Details

* **Architecture**: ResNet-18 (pretrained on ImageNet)
* **Final Layer**: Modified to output 5 classes with optional dropout
* **Freezing**: Backbone layers frozen during training
* **Regularization**:

  * Dropout (`p=0.3`)
  * Weight Decay (`1e-5`)
* **Augmentations**:

  * RandomResizedCrop, HorizontalFlip, ColorJitter, Rotation
* **Loss**: CrossEntropyLoss
* **Optimizer**: Adam (LR = 0.0005)

---

## 🧪 Training Results

### 📉 Baseline Model (no augmentation)

```
Final Training Accuracy: 94.37%
Final Test Accuracy:     98.68%
```

### 📈 Augmented Model (with stronger data augmentation)

```
Final Training Accuracy: 86.86%
Final Test Accuracy:     92.76%
```

---

## 🧰 Project Structure

```
team-project-team-project-team-5/
├── CSCI_4701_Team_5.ipynb              # Main training notebook
├── code/
│   ├── __init__.py
│   ├── data_loader.py                  # Loads and augments dataset
│   ├── model.py                        # Defines modified ResNet-18
│   └── utils.py                        # Training and evaluation functions
├── data/
│   └── data_prep.py                    # Hugging Face dataset loader (optional)
├── models/
│   ├── 0_model_team_5.pth              # Baseline model
│   └── 1_model_team_5.pth              # Augmented model
├── images/
│   └── loss_graph.png                  # Accuracy comparison plot
└── README.md
```

---

## ▶️ How to Run

**1. Clone the repo:**

```bash
git clone https://github.com/ADA-SITE-CSCI-4701/team-project-team-project-team-5
cd team-project-team-project-team-5
```

**2. Download dataset:**

```bash
git lfs install
git clone https://huggingface.co/datasets/khaleed-mammad/azerbaijan-landmarks-dataset
mv azerbaijan-landmarks-dataset data/
```

### 📁 Dataset Structure (After Download)

```
project_root/
├── data/
│   └── azerbaijan-landmarks-dataset/
│       ├── train/
│       │   ├── Maiden Tower/
│       │   ├── Deniz Mall/
│       │   └── ...
│       └── test/
│           ├── Maiden Tower/
│           ├── Deniz Mall/
│           └── ...
```

**3. Open the notebook:**
Run `CSCI_4701_Team_5.ipynb` in Jupyter Notebook or JupyterLab.

**4. Train the models:**
It will train both baseline and augmented models, plot comparison graphs, and save results.
