# Gestures_Recognizer
Real-time Hand Gesture Recognition using MediaPipe and OpenCV with on-screen overlays and optional sound feedback (Python 3.13).

# Hand Gesture Recognition (MediaPipe + OpenCV)

Real-time hand gesture recognition using **MediaPipe Hands** and **OpenCV**. Tracks hand landmarks from a webcam and overlays recognized gestures (Open Hand, Point/Join, Peace, Thumbs Up, Fist) directly on the video feed. Optional sound cues supported via `playsound`.

![demo](assets/demo.gif)

---

## ✨ Features
- Real-time hand tracking (up to 2 hands) with MediaPipe
- Gesture detection: **Open Hand**, **Pointing**, **Peace**, **Thumbs Up**, **Fist**
- Clean UI overlay with gesture labels and instructions
- Optional audio notifications (plug-and-play with `playsound`)
- Simple, readable Python code (single file)

##Steps to Build this Project
#Installation

1.Clone the repository
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>

2.Create & activate a virtual environment (recommended)
Windows:

python -m venv .venv
.venv\Scripts\activate

macOS / Linux:

python3 -m venv .venv
source .venv/bin/activate

Install dependencies

pip install -r requirements.txt

If you’re on a headless server (no GUI), use:

pip install opencv-python-headless mediapipe numpy playsound
Optional: Add sound files

Create a sounds/ folder and drop files like:

sounds/hello.mp3
sounds/join.mp3

Then enable the playsound calls in the code (look for the playsound() comments in hand_gesture_recognition.py).

Run the app
python hand_gesture_recognition.py

A window named "Hand Gesture Recognition - Project H" opens. Press q to quit.

Controls & Gestures

Open Hand (Palm) → shows "Sai Krishna"

Pointing (index finger only) → shows "Join the Workshop"

Peace (index + middle) → shows "Peace!"

Thumbs Up (thumb only) → shows "Thumbs Up!"

Fist (no fingers) → shows "Fist"

The label appears near your hand with a dark background for readability.

Expected Result (What you’ll see)

Console output (example):

DEBUG: Main function started
Hand Gesture Recognition Started!
Gestures:
- Open Hand (Palm): Shows 'Sai Krishna'
- Pointing Gesture: Shows 'Join the Workshop'
Press 'q' to quit

On-screen:

Live camera window with hand skeleton/landmarks drawn in real-time

A green gesture label (e.g., “Peace!”) above your hand

“Press 'q' to quit” in the bottom-left

Troubleshooting

Camera won’t open

Another app might be using the webcam—close it and try again

Try another device index: in the code, change cv2.VideoCapture(0) to 1 or 2

On Windows, try cv2.VideoCapture(0, cv2.CAP_DSHOW)

Black/blank window

Ensure correct camera index

Check OS camera permissions

Update GPU / video drivers

playsound errors

Try WAV files if MP3s fail on your OS

Alternatives: simpleaudio or pygame for more reliable cross-platform playback

Install issues (mediapipe/opencv)

Update build tools and pip:

pip install --upgrade pip setuptools wheel

On Apple Silicon/macOS or ARM Linux, ensure Python and pip are native (no Rosetta mismatches)

How it works (brief)

Capture frames from the webcam (OpenCV).

Detect hand landmarks with MediaPipe (21 points/hand).

Classify gesture by simple geometric rules (which fingers are extended).

Overlay landmark lines and the recognized gesture label on the frame.

Notes

If you mirror the frame (cv2.flip(frame, 1)) handedness may be mirrored too; refine thumb logic using MediaPipe handedness if needed.

Extend gestures easily by adding new rules inside recognize_gesture().

Step-by-step (from writing code → running → result)

Create files

hand_gesture_recognition.py (your provided code)

requirements.txt (list of dependencies)

README.md (this file)

Optionally: assets/demo.gif, sounds/ folder

Initialize Git & commit

git init
git add .
git commit -m "Initial commit: Hand Gesture Recognition (MediaPipe + OpenCV)"

Create the GitHub repo & push

git branch -M main
git remote add origin https://github.com/<your-username>/<your-repo>.git
git push -u origin main

Set up locally

Create a virtual environment

pip install -r requirements.txt

Run

python hand_gesture_recognition.py

Observe result

Landmarks drawn on your hand(s)

Gesture labels (e.g., “Join the Workshop” when pointing)

Press q to exit

Requirements
opencv-python
mediapipe
numpy
playsound

Tip: If you’re deploying to a headless server (no GUI), replace opencv-python with opencv-python-headless.

License

This project is released under the MIT License. Include a LICENSE file if you want the full license text.

Acknowledgements

MediaPipe Hands

OpenCV
