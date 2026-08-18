# 🐄 Cattle Breed Classification through Multiple Approaches

Bachelor's thesis project — Department of Computer Science & Engineering, Premier University Chittagong.

**Authors:** Any Das · Imtiaz Alam Chowdhury · Shahnaz Siddika

**Supervisor:** Md. Neamul Haque, Lecturer

---

## 📌 Overview

Cattle breeding is a major part of Bangladesh's agricultural economy, but breed identification is traditionally done manually. This project builds an automated system that detects and classifies cattle breed from images, comparing one deep learning approach (CNN) against four classical machine learning approaches (SVM, Decision Tree, KNN, Random Forest) on a self-collected dataset of 5,025 images across five breeds — aiming to give farmers and researchers a fast, accurate breed-ID tool.

Five cattle breeds are covered:

| Breed |
|---|
| Holstein Friesian |
| Black Angus |
| Red Chittagong |
| Shahiwal |
| White Native |

## 🎯 Objective

- Predict the breed of a real-world cattle image using the trained models
- Run a comparative analysis across models, highlighting their respective strengths and weaknesses
- Contribute to agricultural technology by providing efficient, accurate breed-classification tools for farmers and researchers

## 💡 Motivation

- Replace manual, traditional cattle breed identification with an automated system
- Give farmers a practical way to identify breed directly from a captured image
- Address common shortcomings of prior work: small datasets, overfitting, and low accuracy

## 🌾 Applications

- Automated breed-identification systems for farmers
- Decision support for livestock management

## 📂 Dataset

**Collection:** Images were gathered first-hand over ~20–25 days of on-site photography (digital cameras and smartphones) across dairy farms (Iqbal Agro, Saara Agro, Asian Agro, A.U.R Agro Farm, Green Harvest Agro, Bhuiyan Agro), cow huts and cattle markets (Bibirhat, 1 Kilometer, Chowdhury Hut, Shagorika, Ilias Brothers Hut, Qurbani Hut, Moijjartek Gorur Bazar), and open streets/fields — to capture real-world variation in setting and lighting.

**Cleaning & labeling:** ~10,000 images were initially collected; after filtering out unclear or ambiguous samples, 5,025 images remained. Each was manually labeled by breed, and PhotoRoom (an AI photo-editing tool) was used for spot-fixing — removing stray objects like extra cow legs bleeding in from neighboring animals.

**Original dataset:** 2,050 images across 5 breeds

| Breed | Original images |
|---|---|
| Holstein Friesian | 558 |
| Black Angus | 330 |
| Red Chittagong | 470 |
| Shahiwal | 380 |
| White Native | 312 |

**After data augmentation:** 5,025 images (balanced to ~1,000 per class), split 70% train / 30% test.

| Breed | Total (augmented) | Train (70%) | Test (30%) |
|---|---|---|---|
| Holstein Friesian | 1000 | 710 | 290 |
| Black Angus | 1025 | 706 | 319 |
| Red Chittagong | 1000 | 714 | 286 |
| Shahiwal | 1000 | 682 | 318 |
| White Native | 1000 | 706 | 294 |

## 🛠️ Tech Stack

- **Language:** Python
- **Environment:** Google Colab (TPU runtime)
- **Libraries:** TensorFlow, Keras, scikit-learn, OpenCV, NumPy, Matplotlib, Seaborn, PIL, mlxtend
- **Pretrained model:** VGG16 (ImageNet weights) — used as a feature extractor for KNN and Random Forest

## 🧪 Methodology

**1. Preprocessing** — images resized to 180×180, batch size 12, pixel values normalized to [0, 1], split 70/30 into 3,518 training / 1,507 test images.

**2. Data augmentation (CNN only)** — random horizontal flip, random rotation, and random zoom, applied as Keras preprocessing layers to expand and balance the dataset.

**3. Per-model approach:**
- **CNN** — a custom sequential architecture (3× Conv2D + MaxPooling blocks → dense layers), trained end-to-end on the images, using the Adam optimizer and sparse categorical cross-entropy loss. Two versions were trained from scratch: a baseline (10 epochs, no augmentation) and a second version with the augmentation layers built in (15 epochs) — the augmented version is the one reported in the results below.
- **SVM** — a linear-kernel SVM trained on flattened, normalized pixel vectors.
- **Decision Tree** — scikit-learn's `DecisionTreeClassifier`, also trained on flattened, normalized pixel vectors.
- **KNN (k=5)** and **Random Forest (100 trees)** — instead of raw pixels, both were trained on deep features extracted from a VGG16 network pretrained on ImageNet (using the `block5_pool` layer as a fixed feature extractor).

## 📊 Results

| Model | Precision | Recall | F1-score | Accuracy |
|---|---|---|---|---|
| Random Forest | 0.9810 | 0.9808 | 0.9807 | **98.41%** |
| SVM | 0.9731 | 0.9728 | 0.9728 | 97.28% |
| CNN | 0.9675 | 0.9677 | 0.9672 | 97% |
| Decision Tree | 0.9517 | 0.9516 | 0.9513 | 95% |
| KNN | 0.9095 | 0.9084 | 0.9083 | 91% |

**Random Forest was the best-performing model overall**, with CNN and SVM close behind. Full confusion matrices, classification reports, and ROC-AUC curves for every model are included in the notebook.

**How this compares to prior work:** related studies on cattle breed classification reported accuracies around 85–92% (e.g., an SVM-based approach reaching 85% on an 8,000-image dataset). Using a larger, more diverse, and augmented dataset, this project's SVM reached 97.28% and Random Forest reached 98.41%.

## ⚠️ Limitations

- The dataset doesn't cover the full global diversity of cattle breeds, which limits generalization
- The models are restricted to recognizing only the five breeds included here

## 🔭 Future Work

- Expand the dataset with a wider range of breeds and environmental conditions
- Explore more advanced deep learning architectures
- Investigate transfer learning with pre-trained models

## 📁 Repository Structure

```
├── Cattle_Breed_Classification.pdf                 # Thesis defense slides
├── Cattle_Breed_Classification_Report.pdf          # Full thesis report
├── CattleBreed_Classification(1).ipynb             # Full implementation (preprocessing, training, evaluation)
└── README.md
```

## 📚 References

1. Briggs, H.M. & D.M. Briggs. *Modern Breeds of Livestock*. Fourth Edition. Macmillan Publishing Co., 1980.
2. "Breeds of Livestock – Bengali Cattle." Department of Animal and Food Sciences, Oklahoma State University.
3. Afroz, M. A., Hoque, M. A., and Bhuiyan, A. K. F. H. (2011). Estimation of heritability for growth traits of Red Chittagong cattle in a nucleus herd. *Bangladesh Veterinarian*, 28, 39–46.
4. Patel N, Upadhyay S. Study of various decision tree pruning methods with their empirical comparison in WEKA. *Int J Comp Appl*, 60(12):20–25.
5. "Buy upgraded Philippine native cattle for sale," Alpha Agventure Farms, Oct. 2023.
6. Roysfarm.com — Sahiwal cattle breed profile.
7. GeeksforGeeks — Convolutional Neural Network (CNN) in Machine Learning, Dec. 2020.
8. GeeksforGeeks — Support Vector Machine (SVM) Algorithm, Jan. 2021.
9. ResearchGate — General architecture of a support vector machine (SVM) model.
10. Towards Data Science — An exhaustive guide to Decision Tree classification in Python 3.X, Oct. 2021.
11. javatpoint — Decision Tree Algorithm in Machine Learning.
12. Section.io Engineering Education — Introduction to Random Forest in Machine Learning.
13. javatpoint — K-Nearest Neighbor (KNN) Algorithm for Machine Learning.
14. Towards Data Science — Machine learning basics with the K-nearest neighbors algorithm, Sep. 2018.
15. Built In — Random Forest: A Complete Guide for Machine Learning, Jul. 2021.


