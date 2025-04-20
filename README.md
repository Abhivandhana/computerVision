
# Liver Lesion Classification

This project focuses on classifying liver lesions based on medical imaging using both traditional Machine Learning (Random Forest) and Deep Learning (Neural Network) approaches. It includes preprocessing, feature extraction, clustering (BCLC stages), model training, and visualizations.

## Project Structure
```
computerVision/
├── train/                  # Training image dataset
├── val/                   # Validation image dataset
├── randomForest.ipynb     # Jupyter Notebook with full pipeline
├── lesion_features_bclc.csv   # Extracted features + cluster results
├── requirements.txt       # Python dependencies
├── README.md              # This file
```
## Setting Up the Environment

### 1. Clone the Repository

```bash
git clone <repository-url>
cd computerVision
```

### 2. Create a Virtual Environment

```bash
python3 -m venv myenv
```

### 3. Activate the Virtual Environment

```bash
source myenv/bin/activate
```

### 4. Install Required Packages

```bash
pip install -r requirements.txt
```

To deactivate the virtual environment later:

```bash
deactivate
```

Check Python version:

```bash
python3 --version
```

---

## Dataset Structure

Expected folder structure:

```
train/
├── Class0/
│   ├── volume-0_slice_0.jpg
│   ├── ...
├── ClassA/
│   ├── volume-0_slice_33.jpg
│   ├── ...

val/
├── Class0/
├── ClassA/
```

---

### Process:

1. **Data Loading** using `ImageFolder`
2. **Feature Extraction**:
   - Mean and Standard Deviation
   - GLCM (Contrast, Homogeneity)
   - Haralick features
   - Shape (Area, Radius, Linearity)
3. **Clustering** with KMeans into 5 BCLC Stages:
   - Stage 0 (Very Early)
   - Stage A (Early)
   - Stage B (Intermediate)
   - Stage C (Advanced)
   - Stage D (End-Stage)
4. **Random Forest Classification**
5. **Neural Network with Keras**
6. **Visualizations**:
   - Confusion Matrix
   - Accuracy & Loss Plots
   - Predicted vs Actual Image Overlays

---

## 📄 `lesion_features_bclc.csv`

This CSV file contains extracted features from training images + predicted BCLC stage clusters.

| Column | Description |
|--------|-------------|
| File_Name | Image filename |
| Mean_Intensity | Average grayscale intensity |
| STD_Intensity | Standard deviation |
| Contrast | Texture contrast (GLCM) |
| Homogeneity | GLCM homogeneity |
| Haralick_Feature | Haralick texture average |
| Radius | Radius of enclosing circle |
| Area | Area of lesion contour |
| Linearity | Perimeter² / Area |
| BCLC_Cluster | KMeans cluster number |
| BCLC_Stage | Assigned BCLC Stage label |

---

## Outputs

- Accuracy & classification reports for both models
- Confusion matrix heatmap
- Neural network training curves
- Visualization of predicted labels on actual images

---

## Implementation

You can open `randomForest.ipynb` in Jupyter Notebook and run the steps sequentially to extract features, perform clustering, train models, and visualize results.

---

## Author

Created by Abhivandhana

---

## License

MIT License
