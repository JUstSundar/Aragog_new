Hand Gesture Recognition with MQTT Control
A real-time hand gesture recognition system using MediaPipe for hand tracking, custom classifiers for static/dynamic gestures, and MQTT for remote control commands.

Features
1) Real-time hand detection and landmark tracking.
2) Static gesture classification (e.g., "Open Hand", "Fist", "Stop").
3) MQTT integration for sending control commands (e.g., 'f' for "Forward", 'e' for "Stop").
4) Data logging in terminal for training custom gestures.
5) Visual feedback with bounding boxes, landmarks, and FPS overlay.

Prerequisites
Python 3.8+
OpenCV (pip install opencv-python)
MediaPipe (pip install mediapipe)
Paho-MQTT (pip install paho-mqtt)

Other dependencies:
bash

Copy
pip install numpy pandas scikit-learn

Installation

Clone the repository:

bash
Copy
git clone https://github.com/yourusername/hand-gesture-recognition.git
cd hand-gesture-recognition
Install dependencies:

bash
Copy
pip install -r requirements.txt
Usage
1. Run the Gesture Recognition System
bash
Copy
python app_new.py [--device 0] [--width 960] [--height 540] [--use_static_image_mode]
Command-Line Arguments:

Argument	Description	Default
--device	Camera device ID	0
--width	Frame width	960
--height	Frame height	540
--use_static_image_mode	Enable static image mode (no tracking)	False
--min_detection_confidence	Detection confidence threshold	0.7
--min_tracking_confidence	Tracking confidence threshold	0.5
2. Gesture Commands
Gesture (Label)	MQTT Command	Description
✋ Open Hand	'f'	Move Forward
✊ Fist	'b'	Move Backward
👈 Left	'l'	Turn Left
👉 Right	'r'	Turn Right
🛑 Stop	'e'	Stop
3. MQTT Setup
Uncomment and configure MQTT in app_new.py:

python
Copy
broker = 'your_broker_ip'  # e.g., '192.168.1.100'
port = 1883
topic = 'control/gestures'
username = 'your_username'
password = 'your_password'
File Structure
Copy
├── app_new.py               # Main application  
├── utils.py                 # FPS calculator utility  
├── model/  
│   ├── keypoint_classifier/  
│   │   ├── keypoint.csv     # Training data for static gestures  
│   │   └── keypoint_classifier_label.csv  # Gesture labels  
│   └── point_history_classifier/  
│       ├── point_history.csv  # Training data for dynamic gestures  
│       └── point_history_classifier_label.csv  
├── README.md  
└── requirements.txt  
Training Custom Gestures
Collect Data:

Press 0–9 to log landmarks for a gesture (labels are defined in keypoint_classifier_label.csv).

Switch modes:

n: Normal operation

k: Log static gestures (keypoints)

h: Log dynamic gestures (point history)

Retrain Models:

Use train.py (if available) or Jupyter notebooks to retrain classifiers.

Troubleshooting
Low FPS?

Reduce camera resolution (--width 640 --height 480).

Disable GPU if unused (os.environ['CUDA_VISIBLE_DEVICES'] = '-1').

MQTT not connecting?

Check broker IP/credentials and firewall settings.

License
MIT License. See LICENSE for details.

Demo
Demo GIF

Replace demo.gif with an actual screen recording. Let me know if you’d like to add/remove any sections!
