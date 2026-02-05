 Vehicle Speed Detection using YOLOv8 & Homography

A real-time web application that estimates vehicle speed from a live IP camera stream using computer vision and object tracking.

This project combines **YOLOv8**, **OpenCV**, and **Flask** to detect vehicles, track them across frames, and calculate their speed in **km/h** using perspective transformation.

> Built for learning, experimentation, and traffic analytics research.

---

## 🌟 Key Features

* Real-time vehicle detection and tracking
* Perspective correction using homography for accurate distance mapping
* Live speed display on each detected vehicle
* Smooth browser video streaming
* Multi-threaded frame capture for performance
* Exponential Moving Average (EMA) speed smoothing
* Stationary vehicle detection
* On-screen calibration zone for measurement accuracy

---

## 🛠️ Technology Stack

| Component            | Technology           |
| -------------------- | -------------------- |
| Backend              | Python, Flask        |
| Computer Vision      | OpenCV               |
| Object Detection     | YOLOv8 (Ultralytics) |
| Tracking             | BoT-SORT             |
| Numerical Processing | NumPy, SciPy         |
| Frontend             | HTML, CSS            |

---

## 📂 Project Structure

```
vehicle-speed-detection/
│
├── app.py
├── yolov8m.pt
├── yolov8n.pt
├── templates/
│   └── index.html
├── static/
│   └── style.css
└── README.md
```

---

## ⚙️ Working Principle

1. Vehicles are detected and tracked in each frame using YOLOv8.
2. Pixel movement is converted into real-world distance using a homography matrix.
3. Distance and time are used to calculate speed.
4. EMA smoothing reduces noise and sudden spikes.
5. Speed is rendered above each vehicle in the video stream.

### 📐 Speed Calculation Formula

```
Speed (km/h) = (Distance in meters / Time in seconds) × 3.6
```

---

## ✅ System Requirements

* Python 3.9+
* IP Camera stream (Android IP Webcam or RTSP)
* GPU recommended (optional)

---

## 🚀 Installation Guide

### Step 1 — Clone Repository

```bash
git clone https://github.com/YOUR-USERNAME/vehicle-speed-detection.git
cd vehicle-speed-detection
```

### Step 2 — Create Virtual Environment

**Windows**

```bash
python -m venv venv
venv\Scripts\activate
```

**Mac / Linux**

```bash
python -m venv venv
source venv/bin/activate
```

### Step 3 — Install Dependencies

```bash
pip install -r requirements.txt
```

---

## 🔧 Configuration

Open **app.py** and update the camera stream:

```python
IP_CAMERA_URL = "http://YOUR_IP:PORT/videofeed"
IP_CAMERA_URL = 0 for your webcam
```

> If camera position or road angle changes, recalibrate the homography source points.

---

## ▶️ Running the Application

```bash
python app.py
```

Visit in browser:

```
http://localhost:5000
```

---

## 🧠 Speed Estimation Logic

* Unique ID assigned to each vehicle
* Perspective transform converts pixels to meters
* Speed filtered using min/max thresholds
* EMA applied for stable readings
* Handles stopped vehicles gracefully

---


## 🔮 Future Improvements

* Lane detection
* License plate recognition
* Speed violation alerts
* Database logging
* Cloud deployment support
