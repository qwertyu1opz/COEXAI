# Function Breakdown

## Dependencies
```python
import os
import cv2
import torch
import numpy as np
import argparse
import logging
from ultralytics import YOLO
```
These are the required dependencies for the project, including OpenCV, PyTorch, and YOLO for object detection.

## `KalmanFilter` Class
### **Purpose:**
This class implements a **Kalman Filter** for tracking object positions over time, smoothing predictions to reduce noise in detections.

### **Implementation:**
```python
class KalmanFilter:
    def __init__(self):
        self.kf = cv2.KalmanFilter(4, 2)
        self.kf.measurementMatrix = np.array([[1, 0, 0, 0],
                                              [0, 1, 0, 0]], np.float32)
        self.kf.transitionMatrix = np.array([[1, 0, 1, 0],
                                             [0, 1, 0, 1],
                                             [0, 0, 1, 0],
                                             [0, 0, 0, 1]], np.float32)
        self.kf.processNoiseCov = np.eye(4, dtype=np.float32) * 0.01
        self.kf.measurementNoiseCov = np.eye(2, dtype=np.float32) * 0.1
```

- **State Variables:**
  - The filter has **4 state variables** (x, y, dx, dy).
  - It predicts the future state based on the previous measurement.
- **Matrices:**
  - `measurementMatrix`: Converts measurements into the filter's internal state.
  - `transitionMatrix`: Defines how the state evolves over time.
  - `processNoiseCov`: Controls how much noise is assumed in the process.
  - `measurementNoiseCov`: Defines the uncertainty of measurements.

### **Updating the Filter:**
```python
    def update(self, x: float, y: float) -> tuple[float, float]:
        measurement = np.array([[x], [y]], dtype=np.float32)
        self.kf.correct(measurement)
        predicted = self.kf.predict()
        return float(predicted[0]), float(predicted[1])
```
- **`update(x, y)`**:
  - Takes a new position measurement `(x, y)`.
  - Updates the filter's state.
  - Predicts the next position.
  - Returns the smoothed `(x, y)` coordinate.

---

## Full Code
```python
# Full implementation of the Parking Detection System
<INSERT FULL CODE HERE>
```

This section contains the full implementation of the project.
