# Monitoring_Accuracy_from_Image_transformation

# Rotation-Invariant MNIST Classification Study

## 🔍 Project Overview
This notebook investigates the impact of image rotation on classification performance, inspired by the Augerino framework. Starting with the MNIST dataset, we systematically rotate images from 0° upwards, evaluating model accuracy degradation to identify the angular robustness threshold (empirically set at 85% accuracy).

**Key Insight**: The methodology developed here can be extended to EEG signal analysis with appropriate spatial transformations, potentially uncovering orientation-sensitive features in neural data.

## 🎯 Objectives
1. **Quantify Rotation Sensitivity**: Measure accuracy drop-off as MNIST digits are rotated (0°→360°)
2. **Determine Robustness Threshold**: Identify the critical angle where accuracy falls below 85%
3. **Framework Generalization**: Establish protocol for adapting the approach to EEG data analysis

## 🛠️ Methodology
```python
for angle in np.arange(0, 360, step=5):
    rotated_images = apply_rotation(X_test, angle)
    accuracy = model.evaluate(rotated_images, y_test)
    if accuracy < 0.85: 
        break
