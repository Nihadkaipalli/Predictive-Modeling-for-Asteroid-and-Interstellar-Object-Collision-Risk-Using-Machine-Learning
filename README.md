# **Predictive-Modeling-for-Asteroid-and-Interstellar-Object-Collision-Risk-Using-Machine-Learning**


## **Table of Contents**

- [Project Overview](#project-overview)  
- [Features](#features)  
- [Installation](#installation)  
- [Usage](#usage)  
- [Dataset](#dataset)  
- [Pipeline](#pipeline)  
- [Models and Evaluation](#models-and-evaluation)  
- [Interpretability](#interpretability)  
- [Results](#results)  
- [Future Improvements](#future-improvements)  
- [Contributing](#contributing)  
- [License](#license)  

---

## **Project Overview**

Asteroids pose a potential threat to Earth, and predicting collision risks is critical for planetary defense. This project implements a data-driven approach to assess asteroid collision risks using machine learning models trained on orbital parameters, ensuring robust performance and interpretability.

---

## **Features**

- **Data Preprocessing**: Handles missing values, categorical encoding, date processing, and scaling.
- **Feature Engineering**: Derived features like `orbital_velocity`, `relative_orbital_distance`, and `adjusted_eccentricity` enhance the prediction capabilities.
- **Model Training**: Implements Random Forest, XGBoost, and Neural Networks.
- **Edge Case Analysis**: Monte Carlo simulations to evaluate model robustness under extreme orbital conditions.
- **Model Interpretability**: Leverages LIME for explaining individual predictions.
- **Extensive Visualization**: Includes correlation heatmaps, ROC/PR curves, feature importance plots, and calibration curves.

---

## **Installation**

1. Clone this repository:
   ```bash
   git clone https://github.com/Nihadkaipalli/Predictive-Modeling-for-Asteroid-and-Interstellar-Object-Collision-Risk-Using-Machine-Learning.git
   cd Predictive-Modeling-for-Asteroid-and-Interstellar-Object-Collision-Risk-Using-Machine-Learning

   cd asteroid-collision-risk-prediction
---

## **Usage**

1. Load the dataset into the specified directory.
2. Run the complete pipeline by executing:
   
  Predictive_Modeling_for_Asteroid_Collision_Risk_Using_Machine_Learning_and_Orbital_Dynamics_final_code_version.ipynb

---

## **Dataset**

The dataset contains orbital parameters and physical characteristics of asteroids, which are crucial for predicting collision risks. Key features include:

- **Orbital Parameters**:
  - `a`: Semi-major axis (AU)
  - `e`: Eccentricity
  - `i`: Inclination (degrees)
  - `q`: Perihelion distance (AU)
  - `tp`: Time of perihelion passage (Julian Date)

- **Physical Parameters**:
  - `H`: Absolute magnitude
  - `neo`: Near-Earth Object (binary flag)
  - `pha`: Potentially Hazardous Asteroid (binary flag)

- **Derived Features**:
  - `relative_orbital_distance`: Distance between perihelion and semi-major axis
  - `orbital_velocity`: Orbital velocity derived using Kepler's laws
  - `adjusted_eccentricity`: Adjusted eccentricity combining orbital properties

- **Target Variable**:
  - `collision_risk`: Binary classification:
    - `1`: High risk (Minimum Orbit Intersection Distance `moid < 0.05 AU`)
    - `0`: Low risk (Minimum Orbit Intersection Distance `moid ≥ 0.05 AU`)

### **Source**
The dataset is sourced from the **NASA JPL Small-Body Database** and processed for machine learning purposes.

### **Structure**
The dataset is a CSV file with the following structure:
| Column                | Description                                      |
|-----------------------|--------------------------------------------------|
| `a`                  | Semi-major axis (AU)                             |
| `e`                  | Eccentricity                                     |
| `q`                  | Perihelion distance (AU)                         |
| `i`                  | Inclination (degrees)                            |
| `neo`                | Near-Earth Object flag (1: Yes, 0: No)           |
| `pha`                | Potentially Hazardous Asteroid flag (1: Yes, 0: No) |
| `H`                  | Absolute magnitude                               |
| `moid`               | Minimum Orbit Intersection Distance (AU)         |
| `collision_risk`     | Binary target (1: High risk, 0: Low risk)        |

### **Usage**
1. Download the dataset and place it in the `data/` directory of your project.
2. Ensure the file is named `Asteroid_Collision_Dataset V2.csv` for compatibility with the pipeline.

---

---

## **Pipeline**

The project is structured into the following steps:

1. **Data Preprocessing**:
   - Handle missing values (imputation or dropping columns).
   - Encode categorical and binary features.
   - Scale numerical data using `StandardScaler`.

2. **Feature Engineering**:
   - Derive new features from orbital dynamics, such as:
     - `relative_orbital_distance`
     - `orbital_velocity`
     - `adjusted_eccentricity`.

3. **Model Training**:
   - Train and save models: Random Forest, XGBoost, and Neural Networks.
   - Apply hyperparameter tuning for optimal performance.

4. **Evaluation**:
   - Evaluate models using metrics like accuracy, F1-score, precision, recall, and ROC-AUC.
   - Visualize confusion matrices, ROC curves, and precision-recall curves.

5. **Monte Carlo Simulations**:
   - Analyze edge cases for robustness testing under extreme orbital scenarios.

6. **Interpretability**:
   - Explain predictions using LIME for all three models.

---

---

## **Models and Evaluation**

Three machine learning models were implemented and evaluated:

| Model                 | Accuracy | F1 Score | Precision | Recall | ROC-AUC |
|-----------------------|----------|----------|-----------|--------|---------|
| **Random Forest**     | 99.51%   | 91.64%   | 85.48%    | 98.75% | 99.92%  |
| **XGBoost**           | 99.71%   | 94.73%   | 92.75%    | 96.80% | 99.97%  |
| **Neural Network**    | 99.36%   | 89.48%   | 81.24%    | 99.57% | 99.95%  |

### **Evaluation Metrics**:
- **Confusion Matrix**: Detailed analysis of true positives, false positives, true negatives, and false negatives.
- **ROC Curve**: Comparison of model sensitivity and specificity.
- **Precision-Recall Curve**: Evaluation of precision and recall trade-offs.
- **Feature Importance**: Identifies the most influential features for Random Forest and XGBoost.

---

---

## **Interpretability**

Understanding model predictions is critical for a high-stakes application like asteroid collision risk prediction. This project employs **LIME (Local Interpretable Model-agnostic Explanations)** to:

1. Explain individual predictions:
   - Identify the most influential features for each prediction.
   - Visualize their impact (positive or negative) on the predicted probability.

2. Perform batch analysis:
   - Analyze multiple test samples to understand overall model behavior.

3. Test edge cases using Monte Carlo simulations:
   - Explore robustness in scenarios like high eccentricity, extreme velocities, and Earth proximity.

**Edge Case Analysis**:
Predictions under conditions such as:
- **Extreme Eccentricity**: Highly elliptical orbits.
- **Proximity to Earth**: Near-collision scenarios with `q` close to zero.
- **High Orbital Velocity**: Unusually fast-moving asteroids.

---

---

## **Results**

### **Key Takeaways**:
- Models achieved **high accuracy and recall**, critical for identifying high-risk scenarios.
- **Feature Importance**:
  - The most influential features include:
    - `q` (Perihelion distance)
    - `neo` (Near-Earth Object flag)
    - `H` (Absolute Magnitude).
- Models demonstrated robustness across extreme edge cases.

### **Visual Highlights**:
- **ROC Curves**: Demonstrates near-perfect performance for all models.
- **Precision-Recall Curves**: Indicates minimal false positives.
- **Calibration Curves**: All models are well-calibrated with true probabilities.

---

---

## **Future Improvements**

The following enhancements are planned to improve the project:

1. **Real-Time Data**:
   - Integrate live asteroid tracking data from APIs such as NASA's Near-Earth Object Web Service (NEOWS).

2. **Neural Network Optimization**:
   - Apply **Keras-Tuner** to explore more complex architectures and hyperparameters.

3. **Interactive Web App**:
   - Build a **Streamlit** or **Flask** application for real-time predictions and visualizations.

4. **Expanded Dataset**:
   - Include additional orbital dynamics features like gravitational perturbations and long-term orbital stability.

---

---

## **Contributing**

Contributions are welcome! Follow these steps to contribute:

1. Fork the repository.
2. Create a new branch for your feature or bug fix:
   ```bash
   git checkout -b feature-name


---

### **License**

```markdown
---

## **License**

This project is licensed under the **MIT License**. You are free to use, modify, and distribute this software under the terms of the license.

For more details, see the LICENSE file.

---

---

## **Contact**

For any inquiries or feedback, feel free to reach out:

- **Email**: nihadkaipalli@gmail.com

---
