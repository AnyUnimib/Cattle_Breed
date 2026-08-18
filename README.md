# 🐄 Cattle Breed Classification through Multiple Approaches

Bachelor's thesis project — Department of Computer Science & Engineering, Premier University Chittagong.

**Authors:** Any Das · Imtiaz Alam Chowdhury · Shahnaz Siddika
**Supervisor:** Md. Neamul Haque, Lecturer

---

## 📌 Overview

This project detects and classifies cattle breeds from images using both classical machine learning and deep learning approaches. It was built to help automate a task that is traditionally done manually by farmers and livestock experts — supporting more efficient and accurate livestock management in agriculture.

Five cattle breeds are covered:

| Breed | 
|---|
| Holstein Friesian |
| Black Angus |
| Red Chittagong |
| Shahiwal |
| White Native |

## 🎯 Objective

To contribute to advancements in agricultural technology by providing efficient and accurate tools for cattle breed classification — aiding farmers and researchers in optimizing livestock practices.

## 💡 Motivation

- Replace manual, traditional cattle breed identification with an automated system
- Give farmers a practical way to identify breed directly from a captured image
- Address common shortcomings of prior work: small datasets, overfitting, and low accuracy

## 🌾 Applications

- Automated breed-identification systems for farmers
- Decision support for livestock management

## 📂 Dataset

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
- **Environment:** Google Colab (Windows 10)
- **Libraries:** TensorFlow, Keras, scikit-learn, OpenCV, NumPy, Matplotlib, Seaborn, PIL, mlxtend

## 🧪 Methodology

**1. Image preprocessing** — all images resized to 300×300.

**2. Data augmentation** — rescale, rotation, shift, shear, flip, and zoom, used to balance and expand the dataset.

**3. Models trained and compared:**
- Convolutional Neural Network (CNN)
- Support Vector Machine (SVM)
- Decision Tree
- K-Nearest Neighbors (KNN)
- Random Forest

## 📊 Results

| Model | Precision | Recall | F1-score | Accuracy |
|---|---|---|---|---|
| Random Forest | 0.9810 | 0.9808 | 0.9807 | **98%** |
| SVM | 0.9731 | 0.9728 | 0.9728 | 97% |
| CNN | 0.9675 | 0.9677 | 0.9672 | 97% |
| Decision Tree | 0.9517 | 0.9516 | 0.9513 | 95% |
| KNN | 0.9095 | 0.9084 | 0.9083 | 91% |

**Random Forest was the best-performing model overall**, with CNN and SVM close behind. Full confusion matrices, classification reports, and ROC-AUC curves for every model are included in the notebook.

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
├── Cattle_Breed_Classification_Report.pdf          # Detailed project report
├── CattleBreed_Classification(1).ipynb             # Full implementation (preprocessing, training, evaluation)
└── README.md
```

## 📚 References

1. R. Kasarda et al., "Classification of cattle breeds based on the random forest approach," *Livestock Science*, vol. 267, 2023.
2. S. Li et al., "Individual dairy cow identification based on lightweight convolutional neural network," *PLOS ONE*, vol. 16, no. 11, 2021.
3. M.E. Hossain et al., "A systematic review of machine learning techniques for cattle identification: Datasets, methods and Future Directions," *Artificial Intelligence in Agriculture*, vol. 6, 2022.
