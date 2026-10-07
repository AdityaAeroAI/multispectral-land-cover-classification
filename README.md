# Multispectral Satellite Image Land-Cover Classification

A machine learning project exploring whether **multispectral satellite imagery and NDVI features can improve land-cover classification** compared with a simple RGB-based approach.

The project uses the **EuroSAT dataset** and Random Forest classifiers to compare RGB features with 13-band multispectral features and engineered NDVI features.

## 📌 Project Overview

Satellite images contain more information than what is visible through standard RGB imagery. Multispectral satellite sensors capture additional wavelengths such as **Near-Infrared (NIR)** and **Short-Wave Infrared (SWIR)**, which can provide useful information for distinguishing different types of land cover.

In this project, I built a classification pipeline and compared:

* **RGB baseline:** 3 RGB channels → 12 statistical features
* **Multispectral model:** 13 spectral bands → 52 statistical features
* **Multispectral + NDVI:** 13 spectral bands + NDVI → 54 features

The final model achieved **90.8% test accuracy**, compared with **78.5% validation accuracy** for the RGB baseline.

## 🛰️ Dataset

The project uses the **EuroSAT** satellite imagery dataset.

Each image represents a land-cover patch and belongs to one of 10 classes:

* Annual Crop
* Forest
* Herbaceous Vegetation
* Highway
* Industrial Buildings
* Pasture
* Permanent Crop
* Residential Buildings
* River
* Sea/Lake

The RGB version contains **3 visible-light channels**, while the multispectral version contains **13 spectral bands**.

## 🔬 Methodology

### 1. RGB Baseline

For every RGB image, I extracted four statistical features from each channel:

* Mean
* Standard deviation
* Minimum
* Maximum

This produced **12 features per image**.

A Random Forest classifier with 100 trees was trained as the baseline model.

### 2. Multispectral Features

The multispectral dataset contains 13 spectral bands.

For each band, I extracted:

* Mean
* Standard deviation
* Minimum
* Maximum

This produced **52 features per image**.

The same Random Forest configuration was used to compare the additional spectral information against the RGB baseline.

### 3. NDVI Feature Engineering

I also explored **Normalized Difference Vegetation Index (NDVI)**:

```text
NDVI = (NIR - Red) / (NIR + Red)
```

NDVI uses the relationship between Near-Infrared and Red reflectance to capture vegetation information.

The final feature set added:

* Mean NDVI
* Standard deviation of NDVI

This resulted in **54 features per image**.

## 📊 Results

| Approach                             | Features |             Accuracy |
| ------------------------------------ | -------: | -------------------: |
| RGB + Random Forest                  |       12 | **78.5% Validation** |
| Multispectral + NDVI + Random Forest |       54 |       **90.8% Test** |

### Key Result

**Improvement: +12.3 percentage points**

The multispectral + NDVI approach substantially outperformed the RGB baseline.

## 🔎 Error Analysis

The RGB baseline had particular difficulty classifying **Highway**, which was frequently confused with Residential Buildings and River.

After adding multispectral information, the confusion between Highway and River decreased, while Highway remained difficult to distinguish from Residential and Industrial Buildings.
This suggests that additional spectral information can help distinguish certain land-cover types, but simple statistical features are still limited when classes have similar spectral characteristics.

## 🛠️ Technologies

* Python
* NumPy
* Pandas
* Scikit-learn
* Matplotlib
* Seaborn
* Hugging Face Datasets
* Random Forest
* Remote Sensing
* Feature Engineering
* NDVI

## 📁 Project Structure

```text
multispectral-land-cover-classification/
│
├── README.md
├── requirements.txt
│
├── notebooks/
│   └── satellite_land_cover_classification.ipynb
│
├── src/
│   └── feature_extraction.py
│
├── results/
│   ├── rgb_confusion_matrix.png
│   ├── multispectral_confusion_matrix.png
│   └── accuracy_comparison.png
│
└── .gitignore
```

## 🚀 How to Run

Clone the repository:

```bash
git clone https://github.com/AdityaAeroAI/multispectral-land-cover-classification.git
cd multispectral-land-cover-classification
```

Install the required libraries:

```bash
pip install -r requirements.txt
```

Open the notebook and run the cells sequentially.

The EuroSAT datasets are loaded using the Hugging Face `datasets` library.

## 📈 Future Improvements

Possible extensions of this project include:

* CNN-based image classification
* Transfer learning with pretrained vision models
* Additional spectral indices such as NDWI and NDBI
* Hyperparameter tuning
* Feature selection
* More detailed per-class error analysis
* Comparison with other machine learning models
* Visualization of multispectral bands and spectral indices

## 👨‍💻 Author

**Aditya Singh Panwar**

GitHub: [AdityaAeroAI](https://github.com/AdityaAeroAI)

---

*This project was developed as an exploration of machine learning, feature engineering, and multispectral remote sensing for satellite image classification.*
