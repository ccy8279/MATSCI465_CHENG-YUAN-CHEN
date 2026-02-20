# **1. Methodology**
   
The project is structured into three distinct analytical tasks:

## **Task 1: Classical Image Processing & Quantification**

**Preprocessing:** Applied Median Filtering (disk radius 3) to suppress salt-and-pepper noise, followed by CLAHE (Contrast Limited Adaptive Histogram Equalization) with a clip limit of 0.025 to optimize contrast without over-amplifying background noise.

**Segmentation:** Implemented a Distance Transform-based Watershed algorithm. Seeds were generated from local maxima of the Euclidean distance map to resolve overlapping particles.

**Morphometrics:** Extracted fundamental geometric properties including Area, Perimeter, Eccentricity, and Circularity.

## **Task 2: Machine Learning AnalysisFeature** 

**Engineering:** Derived advanced descriptors such as LBP (Local Binary Pattern) variance and Edge-to-Area ratios.

**Supervised Classification:** Evaluated SVM (RBF kernel) and Random Forest (100 estimators). Feature importance was analyzed to identify the most discriminative morphological markers.

**Unsupervised Clustering:** Performed K-Means Clustering (k=3, 5, 7) on PCA-reduced feature space to identify inherent sub-populations within the particle dataset.

## **Task 3: Deep Learning (CNN & U-Net)**

**Data Augmentation:** To overcome the limitation of a small annotated dataset (15-20 images), we implemented a 5-variant augmentation pipeline (rotation, shift, zoom, flip, and reflection).

**CNN Architecture:** A compact convolutional network (Conv -> BatchNorm -> MaxPool) designed for robust particle classification.

**U-Net Segmentation:** An encoder-decoder model with Skip Connections to facilitate pixel-level semantic segmentation, preserving high-frequency edge information.

# **2. Quantitative Comparison**

The following table summarizes the performance metrics across all implemented methods.

-- Final Performance Comparison Table ---

| Number | Method |  Metric (F1/IoU) | Runtime | Data Required | Interpretability |
| --- | --- | --- | --- | --- | --- |
|0      |Watershed|           0.65  | Very Fast |         None  |           High|
|1            |SVM|             0.86|        Fast|           Low |          Medium|
|2  |Random Forest |            0.89 |     Medium|           Low |          Medium|
|3        |k-Means  |           0.75  |      Fast|          None |            High|
|4           | CNN   |          0.94  |Slow (GPU)|          High |             Low|
|5          |U-Net    |         0.82   |Very Slow |         High |            Low|

# **3. Recommended Use-Cases**

Based on our benchmarks, we recommend the following application strategies:

**High-Throughput Screening:** Use Watershed for rapid counting when particles are well-separated and contrast is high.

**Diagnostic Classification:** Use Random Forest when the decision-making process must be transparent (e.g., in clinical settings where feature importance matters).

**Complex Morphologies:** Use U-Net for samples with significant overlap or low signal-to-noise ratios (SNR), where classical thresholding fails to define accurate boundaries.
