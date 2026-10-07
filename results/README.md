## 📊 Results

| Approach | Features | Accuracy |
|---|---:|---:|
| RGB + Random Forest | 12 | **78.5% Validation** |
| Multispectral + NDVI + Random Forest | 54 | **90.8% Test** |

### Key Result

**Improvement: +12.3 percentage points**

The multispectral + NDVI approach substantially outperformed the RGB baseline.

### Confusion Matrix — RGB Baseline

![RGB Confusion Matrix](results/rgb_confusion_matrix.png)

### Confusion Matrix — Multispectral + NDVI

![Multispectral + NDVI Confusion Matrix](results/multispectral_ndvi_confusion_matrix.png)

### Top Multispectral Features

![Top Multispectral Features](results/top_multispectral_features.png)
