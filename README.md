Real-Time Vehicle Speed Detection Web App

A browser-based system that measures vehicle speed from a live camera feed using computer vision and object tracking.
Built with YOLOv8, OpenCV, and Flask, this project estimates vehicle speeds in km/h by correcting perspective distortion with homography.

Designed for learning, experimentation, and smart traffic analytics projects.

✨ Highlights

Live vehicle detection and ID tracking with YOLOv8

Perspective (homography) correction for real-world distance mapping

Instant speed estimation displayed over each vehicle

Smooth video streaming directly in the browser

Multi-threaded frame capture for better performance

Exponential Moving Average (EMA) to stabilize speed readings

Detects stationary vehicles

Visual calibration area to improve measurement accuracy

🧰 Tech Stack
Layer	Tools Used
Backend	Python, Flask
Vision	OpenCV
Detection	YOLOv8 (Ultralytics)
Tracking	BoT-SORT
Math	NumPy, SciPy
Frontend	HTML, CSS
📁 Project Layout
vehicle-speed-detection/
│
├── app.py                # Flask server + speed estimation pipeline
├── yolov8m.pt            # Main YOLOv8 weights
├── yolov8n.pt            # Lightweight model (optional)
├── templates/
│   └── index.html        # Web UI
├── static/
│   └── style.css         # Styling
└── README.md

⚙️ How the System Works

YOLOv8 detects and tracks vehicles frame by frame.

A homography matrix converts pixel motion into meters.

Distance traveled over time is used to compute speed.

EMA smoothing reduces sudden fluctuations.

The calculated speed (km/h) is drawn above each vehicle.

Speed Formula

speed (km/h) = (distance_in_meters / time_in_seconds) × 3.6

✅ Requirements

Python 3.9 or higher

IP camera stream (Android IP Webcam / RTSP camera)

GPU is helpful but optional

🚀 Setup Instructions
1) Clone the repo
git clone https://github.com/YOUR-USERNAME/vehicle-speed-detection.git
cd vehicle-speed-detection

2) Create & activate virtual environment

Windows

python -m venv venv
venv\Scripts\activate


Mac/Linux

python -m venv venv
source venv/bin/activate

3) Install dependencies
pip install -r requirements.txt

🔧 Configuration

Open app.py and set your camera stream URL:

IP_CAMERA_URL = "http://YOUR_IP:PORT/videofeed"


If your camera angle or road layout changes, update the homography source points for accurate measurements.

▶️ Run the App
python app.py


Open in your browser:

http://localhost:5000

🧠 Speed Estimation Details

Each vehicle is assigned a unique tracking ID

Pixel displacement is converted to meters using perspective transform

Speed is filtered using minimum/maximum thresholds

EMA smoothing prevents noisy spikes

Stationary vehicles are recognized and handled

⚠️ Important Note

This project is intended for educational and experimental purposes.
Accuracy depends heavily on proper camera calibration and should not be used for legal enforcement.

🔮 Possible Enhancements

Automatic lane detection

License plate recognition (ANPR)

Speed violation alerts

Data logging to a database

Cloud deployment (AWS / GCP / Azure)
