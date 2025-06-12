# Monitoring_Accuracy_from_Image_transformation

# Rotation-Invariant MNIST Classification Study

## 🔍 Project Overview
This project systematically evaluates how image rotation affects MNIST digit classification accuracy through two experimental paradigms:
1. **Specialized Models**: 10 models trained on narrow rotation ranges (`0°-10°`, `10°-20°`, ..., `90°-100°`)
2. **Progressive Models**: Models trained on cumulatively wider ranges (`0°-10°`, `0°-20°`, ..., `0°-100°`)

**Key Insight**: The methodology bridges computer vision and neurotechnology, with potential applications to EEG signal analysis via spatial transformations.

## 📊 Key Results
### Task 1 (Specialized Models)
- Each model excels within its trained angular range (e.g., `[20°-30°]` model peaks at 25°)
- Accuracy degradation observed outside trained ranges (Figure 1)
- Inter-range comparison reveals angular sensitivity thresholds (Figure 2)

### Task 2 (Progressive Models)
- Wider training ranges (`0°-N°`) show better generalization but lower peak accuracy
- Critical drop-off points identified at `60°` and `100°` (Figures 3-4)

## 🎯 Objectives
1. **Quantify Rotation Sensitivity**: 
   - Measure accuracy across `0°-100°` rotations
   - Compare specialized vs. progressive training approaches
2. **Robustness Analysis**:
   - Identify angular thresholds where accuracy drops below 85%
3. **Framework Extension**:
   - Protocol for adapting to EEG data via signal transformations

## 🛠️ Methodology
```python
# Task 1: Specialized Models
for i, (min_angle, max_angle) in enumerate([(0,10), (10,20), ..., (90,100)]):
    train_data = rotate_dataset(X_train, range=(min_angle, max_angle))
    model = train_classifier(train_data)
    test_accuracies = evaluate_on_all_angles(model, test_range=(0,100))

# Task 2: Progressive Models
for max_angle in range(10, 101, 10):
    train_data = rotate_dataset(X_train, range=(0, max_angle))
    model = train_classifier(train_data)
    test_accuracies.append(evaluate_on_all_angles(model))
