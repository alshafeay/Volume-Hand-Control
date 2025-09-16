# AI Gesture Volume Control

This project utilizes computer vision to control the system's master volume through hand gestures. By using a webcam, the application tracks the user's hand in real-time and adjusts the volume based on the distance between the thumb and the index finger.


## Features
- **Real-time Hand Tracking:** Uses Google's MediaPipe library for fast and accurate hand landmark detection.
- **Gesture-Based Volume Control:** Intuitively control your computer's volume by changing the distance between your thumb and index finger.
- **Visual Feedback:** The application window displays:
    - The camera feed with detected hand landmarks.
    - A line connecting the thumb and index finger, which changes in length with the gesture.
    - A dynamic volume bar that reflects the current system volume.
    - An FPS (Frames Per Second) counter to monitor performance.
- **Modular Code:** The hand tracking functionality is encapsulated in a reusable Python class (`HandTrackingModule.py`), making it easy to integrate into other projects.

## How It Works
1.  **Video Capture:** The script uses `OpenCV` to capture the video feed from the default webcam.
2.  **Hand Detection:** The `MediaPipe` framework processes each frame to detect and locate 21 distinct 3D landmarks on the hand.
3.  **Landmark Tracking:** The application specifically monitors the coordinates of the tip of the thumb (Landmark #4) and the tip of the index finger (Landmark #8).
4.  **Distance Calculation:** The Euclidean distance between these two points is calculated in real-time.
5.  **Volume Mapping:** This calculated distance (measured in pixels) is mapped to the system's volume range (e.g., 0% to 100%). The `numpy` library's `interp` function is used for this linear interpolation.
6.  **System Volume Control:** The `pycaw` library is used to interface with the system's core audio APIs (specifically for Windows) and set the master volume to the mapped value.


## Usage
To run the application, execute the main script from your terminal:
```bash
python VolumeHandControl.py
```
- A window will open showing your webcam feed.
- Show your hand to the camera.
- Move your thumb and index finger closer or farther apart to control the volume.
- To quit the application, press the `ESC` key.

## Acknowledgments
- This project is built upon the powerful [MediaPipe](https://google.github.io/mediapipe/) framework by Google.
- [OpenCV](https://opencv.org/) for computer vision functionalities.
- [pycaw](https://github.com/AndreMiras/pycaw) for system audio control.
