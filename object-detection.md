---
layout: page
title: Real-Time Object Detection Project
permalink: /object-detection/
---

# 👁️ Real-Time Object Detection System

**Can a computer "see" like a human?** That was the question I wanted to answer with this project. I built a Python application that uses Artificial Intelligence to identify and classify objects through a webcam in real-time.

<div style="text-align: center; margin: 20px 0;">
  <img src="https://raw.githubusercontent.com/ultralytics/assets/main/yolov8/banner-yolov8.png" alt="YOLOv8 Demo" style="border-radius: 8px; width: 100%; max-width: 600px;">
  <p><em>(Example of how the YOLO model sees the world)</em></p>
</div>

---

## 🛠️ The Tech Stack

I chose these tools to ensure the system was fast (real-time) and accurate:

* **Python:** For the core logic.
* **OpenCV:** To access the webcam feed and draw the visual boxes.
* **YOLOv8 (Ultralytics):** A state-of-the-art Deep Learning model pre-trained on the COCO dataset (80+ object classes).
* **VS Code:** My development environment.

---

## 🚀 How It Works

The logic flows in a continuous loop:

1.  **Input:** The script captures a single frame (image) from the live webcam feed using OpenCV.
2.  **Processing:** This frame is passed to the YOLOv8 AI model. The model analyzes the pixels to find patterns matching known objects (like "Person", "Cell Phone", "Cup").
3.  **Output:** The model returns the coordinates (x, y) of the objects.
4.  **Visualization:** I use OpenCV to draw a rectangle (bounding box) at those coordinates and label it with the object name.

### The Code Snippet
Here is the core logic loop that makes it happen:

```python
while True:
    ret, frame = cap.read()
    
    # AI Processing
    results = model(frame)
    
    # Visualization
    annotated_frame = results[0].plot()
    
    # Display
    cv2.imshow("My Object Detection", annotated_frame)
