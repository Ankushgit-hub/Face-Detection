# Face and Hand Detection with MediaPipe

This project demonstrates real-time face and hand detection using the **MediaPipe** library, integrated with **OpenCV** for camera feed handling and displaying results. It provides an interactive experience where the user can start the camera stream by typing "start" and view detections of faces and hands in real-time.

## Requirements

Before running the code, make sure to install the required libraries:

- **OpenCV**: Used for capturing the webcam feed and displaying the images.
- **MediaPipe**: A framework for building pipelines for processing perceptual data like video, audio, and sensor data.

To install the required libraries, you can use `pip`:
```bash
pip install opencv-python mediapipe
```


If you're using Google Colab or Jupyter Notebook, you may also need the following for displaying images:
```
pip install google-colab
```


## How It Works

### Step-by-step process:

1. **User Input**: 
   - The program prompts the user to type "start" to begin the camera feed. If the input is incorrect, the user will be asked again until they type "start".
   
2. **Camera Feed**:
   - The program captures frames from the webcam using OpenCV's `cv2.VideoCapture()`. The frames are then processed for face and hand detection using the **MediaPipe** library.

3. **Face Detection**:
   - MediaPipe's `FaceDetection` model is used to detect faces in the webcam feed. The results are drawn on the image using `mp_drawing.draw_detection()`.

4. **Hand Detection**:
   - The `Hands` model from MediaPipe detects hand landmarks. Each hand's landmarks are drawn on the image using `mp_drawing.draw_landmarks()`.

5. **Display the Image**:
   - The processed image is displayed in a window using `cv2.imshow()`. The image is flipped horizontally to mimic a "selfie view."

6. **Exit the Program**:
   - The program continuously runs until the user presses the 'a' key to stop the camera feed and close the window.

## How to Run

1. Clone or download the project to your local machine.
2. Ensure that you have Python 3.x installed along with the required libraries (OpenCV and MediaPipe).
3. Run the script using:
```
python face_hand_detection.py
```

4. The program will prompt you to type "start" to begin the camera feed.
5. Once the camera is started, the program will continuously display the live camera feed with face and hand detection annotations.
6. To exit, press the 'a' key on your keyboard.

## Code Description

### Key Parts of the Code:

- **User Input Loop**:
```python
while True: user_input = input() if user_input.lower() == 'start': 
    break
```


- **Camera Initialization**:
```python
cap = cv2.VideoCapture(0) # Use 0 for default camera
```


- **Face and Hand Detection**:
The face and hand detection models are initialized using `mp_face_detection.FaceDetection()` and `mp_hands.Hands()`.
```python
with mp_face_detection.FaceDetection(model_selection=1, min_detection_confidence=0.5) as face_detection,
mp_hands.Hands(min_detection_confidence=0.5, max_num_hands=10, min_tracking_confidence=0.5) as hands:
```

- **Drawing Annotations**:
- Face detections are drawn using `mp_drawing.draw_detection()`.
- Hand landmarks are drawn using `mp_drawing.draw_landmarks()`.

- **Exit Condition**:
```python
if cv2.waitKey(5) & 0xFF == ord('a'): # Exit on pressing 'a' break
```


## Troubleshooting

- If the camera feed does not start, ensure that the webcam is properly connected to your computer and that no other applications are using the camera.
- If you encounter errors related to `MediaPipe` or `OpenCV`, make sure the correct versions of the libraries are installed.

## License

This project is licensed under the MIT License.

## Author

Ankush Panja
