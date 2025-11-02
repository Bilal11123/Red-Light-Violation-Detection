# 🚦 Vehicle Detection & Red Light Violation System

This project detects vehicles in a video stream and automatically flags **red light violations** using a YOLO-v8-based object detection model. It processes traffic footage, identifies vehicles crossing the stop line during a red light, and saves cropped images of violating vehicles. It also provides a visual flash alert in the annotated video output. NOTE: This project is a prototype and only includes a sample video footage, however, real-time video can be sourced and used as the input to the existing project.

## 📌 Features

- **Real-time Vehicle Detection** using a trained YOLO model (`best.pt`)
- **Red Light Violation Detection** based on predefined signal timing
- **Flashing Alert** for vehicles violating the stop line during red light
- **Automatic Cropping & Saving** of violating vehicles’ images
- **Annotated Output Video** showing bounding boxes, traffic light status, and violation count
- **Customizable Parameters** for adapting to real-world conditions

## 🖼 Demo

<img width="1558" height="869" alt="image" src="Screenshot.png" />

---

## 📂 Project Structure

Vehicle-Detection-Project/

- ├── 📄 main.py # Main script (vehicle detection + violation logging)
- ├── 🎯 best.pt # YOLO trained weights
- ├── 🎥 Traffic_video.mp4 # Input video for detection
- ├── 📄 Vehicle_Detection_Training.ipynb
- └── 📖 README.md # Project documentation

## Project Resources

- `Traffic_video.mp4` I used was [link](https://www.youtube.com/watch?v=Y1jTEyb3wiI), you can find a better one.
- The traffic video can be a normal one as the project time as traffic signal and draws it on image.

## 🤖 Model & Training Reference

The YOLO model (`best.pt`) used in this project was trained using a dataset and preprocessing pipeline from **Roboflow**, originally created and shared by another contributor.

**Original Roboflow Project:** [Vehicle Object Detection Model](https://app.roboflow.com/vehicle-object-detection-oyglk/vehicle_detection-rdah2-wvwbb/generate/preprocessing)

All credit for the dataset and preprocessing configuration goes to the original creator. This repository only covers the detection, logging, and visualization implementation.

To use this dataset, you must:

- Fork the dataset.
- create a dataset version [roboflow help](https://docs.roboflow.com/datasets/dataset-versions/create-a-dataset-version)
- download the dataset [roboflow help](https://docs.roboflow.com/datasets/download-a-dataset)

## ⚙️ Installation and Setup

1. **Clone this repository**

```bash
git clone https://github.com/Bilal11123/Red-Light-Violation-Detection.git
cd Red-Light-Violation-Detection
```

2. **Train the model**

- Upload the Vehicle_Detection_Training.ipynb file to Google Colab.
- Upload the download dataset [link](https://app.roboflow.com/vehicle-object-detection-oyglk/vehicle_detection-rdah2-wvwbb/generate/preprocessing).
- Train the dataset.
- download `best.pt` in the root of your project.

3. **Install Dependencies**

```bash
pip install ultralytics opencv-python numpy
```

4. Add the YOLO model weights
   Place your trained YOLO weights file (`best.pt`) in the project folder.

5. Add your video
   Replace `Video_final_4.mp4` with your own traffic video or rename accordingly.

---

## 🚀 Usage

Run the detection script:

```bash
python main.py
```

Press **Q** anytime to exit

## 🛠 Customization

**Change red light timing**
In `main.py`, modify the `is_red_light()` function:

```python
def is_red_light():
    current_pos_seconds = cap.get(cv.CAP_PROP_POS_MSEC) / 1000.0
    return current_pos_seconds > 12  # Change threshold for your video
```

Adjust frame skipping,

```python
frame_skip = 5  # Lower = smoother but slower
```

Modify stop line position:

```python
line_y = 310  # Change based on your camera angle
```

## 📊 Output

- `violations/` → Cropped images of violating vehicles
- `Annotated_Video.mp4` → Video with annotations and alerts
- Terminal logs → Shows when violations are detected

## 🖥 Requirements

- Python 3.8+
- Ultralytics YOLO
- OpenCV
- NumPy

## 📜 License

This project is for educational purposes only. For real-world deployment, follow all local traffic monitoring laws.
