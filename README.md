**Vehicle Detection and Counting System**

This project provides a Python-based implementation for detecting and counting vehicles using OpenCV. The script processes a video file, detects moving vehicles, and counts how many vehicles cross a designated line in the video. The technique used involves background subtraction and contour detection.

Features
Detects moving vehicles from a video file.
Counts vehicles that pass through a predefined line.
Displays the real-time video feed with bounding boxes around detected vehicles.
Displays the vehicle count in real-time.
Requirements
Python 3.x
OpenCV library (opencv-python, opencv-python-headless for environments without GUI)
NumPy library
Install the necessary dependencies using the following commands:

bash
Copy code
pip install opencv-python numpy
How the Code Works
Initialization:

The script starts by setting the minimum width (largura_min) and height (altura_min) for valid vehicle detection.
pos_linha is the vertical position of the line where vehicles are counted.
offset is a tolerance factor for line-crossing detection.
Video Capture:

The video file (video.mp4) is loaded using cv2.VideoCapture(). You can replace 'video.mp4' with the path to your video file.
Background Subtraction:

The background subtraction model is created using cv2.createBackgroundSubtractorMOG2(). This helps isolate moving objects (vehicles) from the background.
Frame Processing:

For each frame, the image is converted to grayscale and blurred to reduce noise.
The background subtraction is applied, followed by morphological operations (dilation and closing) to enhance the contours of the detected objects.
Contour Detection:

Contours are detected using cv2.findContours(). Each contour represents a detected moving object.
The bounding box of each contour is calculated, and if the width and height are larger than the minimum size, the object is considered a vehicle.
Vehicle Counting:

For each valid vehicle, the script calculates its center point using the pega_centro() function.
If the vehicle’s center point crosses the predefined line (pos_linha), it is counted as a vehicle, and the vehicle count is updated.
Display:

The processed frames are displayed using cv2.imshow() with bounding boxes around detected vehicles and a line indicating the counting zone.
The vehicle count is shown on the video feed.
Exit Condition:

The video feed runs in a loop, and the program terminates when the Esc key is pressed.
Usage
Modify the video file path if necessary.
Run the script:
bash
Copy code
python vehicle_counter.py
The video will play, and the vehicles crossing the line will be counted and displayed in real-time.
Notes
You may need to adjust the pos_linha and offset based on the video resolution and the position of the road in the video.
The vehicle size thresholds (largura_min, altura_min) may also need tuning depending on the video quality and camera angle.
This system provides a basic framework for vehicle detection and counting. For more advanced features such as speed detection, multi-lane tracking, or object classification, additional techniques and libraries may be integrated.
