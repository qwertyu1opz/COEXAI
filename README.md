# Parking Detection System

This project is a parking detection system using **YOLO object detection** and **ArUco marker-based tracking**. It processes images and videos, detecting objects such as parking lines and vehicles using **deep learning** models.

## Features

- **YOLO-based Segmentation**: Uses a pre-trained **YOLO model** for detecting objects like parking lines and cars.
- **ArUco Marker Tracking**: If parking lines are not clearly detected, the system uses **ArUco markers** for precise positioning.
- **Kalman Filter for Object Tracking**: Implements a **Kalman Filter** to predict object positions smoothly over frames.
- **Multi-Frame Processing**: Can handle both **static images** and **real-time video streams**.
- **Fallback Mechanism**: If parking lines are not detected, the system estimates positions based on ArUco markers.
- **Flexible Input Handling**: Supports **image, video, and live streams (URL-based)**.
- **Device Support**: Works on **CPU** and **GPU (CUDA)**.

## Installation

### Prerequisites
- Python 3.x
- OpenCV
- PyTorch
- Ultralytics YOLO
- NumPy

### Install Dependencies
```sh
pip install -r requirements.txt
```

## Usage

### Running on an Image
```sh
python main.py --input path/to/image.jpg --mode segmentation --device cpu
```

### Running on a Video
```sh
python main.py --input path/to/video.mp4 --mode segmentation --device cuda
```

### Running on a Live Stream
```sh
python main.py --input http://stream-url --mode segmentation --device cuda
```

## Configuration Options
| Argument       | Description                                      | Default |
|---------------|--------------------------------------------------|---------|
| `--device`    | Processing device (`cpu` or `cuda`)             | `cpu`   |
| `--model`     | Path to YOLO model                              | `model.pt` |
| `--input`     | Path to image, video, or stream                 | Required |
| `--mode`      | Detection mode (`segmentation`, `detection`)    | `segmentation` |

## License
MIT License

---
Feel free to contribute by submitting issues or pull requests!
