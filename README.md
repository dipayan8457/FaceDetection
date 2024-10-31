# Face Detection using MTCNN and OpenCV

This project implements real-time face detection using the **Multi-task Cascaded Convolutional Networks (MTCNN)** for detecting facial landmarks and **OpenCV** for displaying results. It provides functionality for detecting faces and facial key points in both static images and real-time video streams from a webcam.

## Overview

This project uses MTCNN, a robust face detection model capable of detecting faces and locating key facial landmarks (eyes, nose, and mouth) within an image. With OpenCV, the system draws bounding boxes around detected faces and highlights key facial features on both static images and real-time video streams.

## Features

- **Face Detection in Images**: Detects faces and facial landmarks in static images.
- **Real-time Face Detection**: Processes live video feed from a webcam to detect faces continuously.
- **Facial Key Points Visualization**: Marks key facial landmarks (eyes, nose, mouth) within detected faces.

## Usage

### 1. Face Detection in Static Images

The code reads an image from the `images` directory, detects faces, draws bounding boxes around them, and marks key facial landmarks. Key points include left and right eyes, nose, and left and right corners of the mouth.

#### Key Steps
1. **Detect Faces**: The `detector.detect_faces(img)` method returns a list of dictionaries, each containing the bounding box coordinates and key points for each detected face.
2. **Draw Bounding Boxes and Key Points**:
   - Bounding boxes are drawn around each detected face.
   - Circles are drawn at each facial landmark (eyes, nose, mouth corners).

3. **Display Image**: The processed image with detected faces and landmarks is displayed in a window.

To view the output:
- Run the code, and a window will open displaying the image with detected features highlighted.

### 2. Real-time Face Detection

This section of the code uses a webcam feed to detect and draw bounding boxes around faces in real time. It runs in a loop, continuously capturing frames from the webcam and processing each frame for face detection.

#### Key Steps
1. **Capture Webcam Feed**: Captures frames in real time from the webcam using OpenCV’s `VideoCapture`.
2. **Detect Faces**: For each frame, the `detector.detect_faces(frame)` function identifies faces and their bounding boxes.
3. **Draw Bounding Boxes**: Bounding boxes are drawn around detected faces in each frame.
4. **Exit Condition**: Pressing the 'x' key exits the loop and closes the webcam feed.

To run:
- Execute the script, and a window will display the webcam feed with face detection applied in real time. Press 'x' to exit.

### Example Code Snippet

```python
from mtcnn import MTCNN
import cv2

# Initialize the face detector
detector = MTCNN()

# Read an image and detect faces
img = cv2.imread('images/vk.jpg')
output = detector.detect_faces(img)
print(output)

# Draw bounding boxes and key points on detected faces
for i in output:
    x, y, width, height = i['box']
    cv2.rectangle(img, pt1=(x, y), pt2=(x + width, y + height), color=(255, 0, 0), thickness=3)
    # Draw key points like left eye, right eye, etc.
    # ...

# Display the result
cv2.imshow('Face Detection', img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

This code gives a concise view of how the system reads images, detects faces, marks key points, and displays the result.

---
