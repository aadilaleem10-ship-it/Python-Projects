# Face Recognition Using Python and OpenCV

## Project Overview

This project demonstrates real-time face detection using Python and
OpenCV. It captures video from a webcam, detects human faces using a
Haar Cascade classifier, and draws rectangles around detected faces in
real time.

> Note: Despite the filename mentioning "Face Recognition", the code
> performs **face detection**, not face recognition. Face recognition
> identifies who a person is, while face detection only locates faces in
> an image or video.

------------------------------------------------------------------------

## Source Code Analysis

``` python
import cv2

a = cv2.CascadeClassifier('haarcascade_frontalface_default.xml')
b = cv2.VideoCapture(0)

while True:
    c_rec,d_image = b.read()
    e= cv2.cvtColor(d_image,cv2.COLOR_BGR2GRAY)
    f = a.detectMultiScale(e,1.3,6)

    for (x1,y1,w1,h1) in f:
        cv2.rectangle(d_image, (x1,y1), (x1+w1,y1+h1),(255,0,0),2)

    cv2.imshow('img',d_image)
    h = cv2.waitKey(40) & 0xFF
    if h == 40:
        break

b.release()
cv2.destroyAllWindows()
```

------------------------------------------------------------------------

# Detailed Explanation

## 1. Import OpenCV

``` python
import cv2
```

OpenCV (Open Source Computer Vision Library) provides tools for image
processing, video capture, and object detection.

------------------------------------------------------------------------

## 2. Load Haar Cascade Classifier

``` python
a = cv2.CascadeClassifier('haarcascade_frontalface_default.xml')
```

This loads a pre-trained Haar Cascade model for detecting frontal human
faces.

### Haar Cascade

-   Machine learning-based object detection algorithm.
-   Trained using thousands of positive and negative images.
-   Fast and suitable for real-time applications.
-   Detects facial patterns such as eyes, nose, and mouth regions.

------------------------------------------------------------------------

## 3. Access Webcam

``` python
b = cv2.VideoCapture(0)
```

`0` represents the default webcam connected to the system.

### Purpose

-   Captures live video frames.
-   Each frame is processed individually for face detection.

------------------------------------------------------------------------

## 4. Infinite Processing Loop

``` python
while True:
```

Runs continuously until the user exits the application.

------------------------------------------------------------------------

## 5. Read Video Frame

``` python
c_rec, d_image = b.read()
```

### Variables

-   `c_rec` → Boolean value indicating successful frame capture.
-   `d_image` → Current frame captured from webcam.

------------------------------------------------------------------------

## 6. Convert Frame to Grayscale

``` python
e = cv2.cvtColor(d_image, cv2.COLOR_BGR2GRAY)
```

### Why Grayscale?

-   Reduces computational complexity.
-   Haar Cascade works on intensity values rather than colors.
-   Improves processing speed.

------------------------------------------------------------------------

## 7. Detect Faces

``` python
f = a.detectMultiScale(e, 1.3, 6)
```

### Parameters

#### Scale Factor = 1.3

Controls image scaling during detection.

-   Larger value = Faster but less accurate.
-   Smaller value = More accurate but slower.

#### Min Neighbors = 6

Controls detection quality.

-   Higher value = Fewer false positives.
-   Lower value = More detections but potentially inaccurate.

### Output

Returns:

``` python
[(x, y, width, height)]
```

Where: - x = X-coordinate - y = Y-coordinate - width = Face width -
height = Face height

------------------------------------------------------------------------

## 8. Draw Bounding Box

``` python
for (x1,y1,w1,h1) in f:
    cv2.rectangle(
        d_image,
        (x1,y1),
        (x1+w1,y1+h1),
        (255,0,0),
        2
    )
```

Draws a blue rectangle around each detected face.

### Parameters

-   Starting point → `(x1, y1)`
-   Ending point → `(x1+w1, y1+h1)`
-   Color → Blue `(255,0,0)`
-   Thickness → `2` pixels

------------------------------------------------------------------------

## 9. Display Video

``` python
cv2.imshow('img', d_image)
```

Displays the processed frame with detected faces highlighted.

------------------------------------------------------------------------

## 10. Keyboard Input

``` python
h = cv2.waitKey(40) & 0xFF
```

Waits 40 milliseconds for a key press.

### Current Exit Condition

``` python
if h == 40:
    break
```

This exits when the key code equals 40.

### Recommended Alternative

``` python
if h == ord('q'):
    break
```

This allows the user to press **Q** to quit, which is more intuitive.

------------------------------------------------------------------------

## 11. Release Resources

``` python
b.release()
cv2.destroyAllWindows()
```

### Purpose

-   Releases webcam access.
-   Closes all OpenCV windows.
-   Prevents resource leaks.

------------------------------------------------------------------------

# Workflow

1.  Start webcam.
2.  Capture video frame.
3.  Convert frame to grayscale.
4.  Detect faces.
5.  Draw rectangles around faces.
6.  Display frame.
7.  Repeat until user exits.
8.  Release resources.

------------------------------------------------------------------------

# Requirements

## Install OpenCV

``` bash
pip install opencv-python
```

------------------------------------------------------------------------

## Required File

Download:

`haarcascade_frontalface_default.xml`

OpenCV typically includes this file inside:

``` text
opencv/data/haarcascades/
```

------------------------------------------------------------------------

# Limitations

-   Detects faces only.
-   Does not identify individuals.
-   Accuracy decreases in poor lighting.
-   Sensitive to face orientation.
-   Older Haar Cascade approach compared to modern deep learning
    methods.

------------------------------------------------------------------------

# Possible Improvements

## Face Recognition

Use: - LBPH Face Recognizer - EigenFaces - FisherFaces - DeepFace -
FaceNet

## Performance Improvements

-   Add FPS counter
-   Multi-threading
-   GPU acceleration

## User Experience

-   Press Q to quit
-   Display face count
-   Save detected faces
-   Take snapshots

------------------------------------------------------------------------

# Technologies Used

-   Python
-   OpenCV
-   Haar Cascade Classifier
-   Computer Vision
-   Webcam Video Processing

------------------------------------------------------------------------

# Expected Output

When the program runs:

-   Webcam opens.
-   Faces are detected automatically.
-   Blue rectangles appear around detected faces.
-   Detection updates in real time.
-   Application closes when exit key is pressed.

------------------------------------------------------------------------

# Conclusion

This project is a beginner-friendly computer vision application that
demonstrates real-time face detection using OpenCV's Haar Cascade
classifier. It provides a strong foundation for advanced projects such
as attendance systems, security monitoring, facial recognition systems,
and AI-powered surveillance applications.
