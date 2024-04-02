# Real-time Pose Estimation using MediaPipe and OpenCV


## To run the code, please either use "Visual Studio" or "Jupyter Notebook from Anaconda Navigator".

### For the project video, please check the "Project Video" file. Thank you.

<br>

## Code Explanation:

1. **Importing Libraries**:
   - `import cv2`: Imports the OpenCV library for computer vision tasks.
   - `import mediapipe as mp`: Imports the MediaPipe library, which provides ready-to-use, high-level solutions for various tasks such as pose estimation.

2. **Initializing MediaPipe Pose Model**:
   - `mp_pose = mp.solutions.pose`: Initializes the MediaPipe Pose module.
   - `pose = mp_pose.Pose(static_image_mode=False, model_complexity=1, smooth_landmarks=True, min_detection_confidence=0.5, min_tracking_confidence=0.5)`: Initializes the Pose model with the specified parameters. This includes enabling real-time processing (`static_image_mode=False`), setting model complexity, and defining confidence thresholds.

3. **Initializing Drawing Utilities**:
   - `mp_drawing = mp.solutions.drawing_utils`: Initializes the MediaPipe drawing utilities for rendering pose landmarks and connections on the frame.

4. **Capturing Video**:
   - `cap = cv2.VideoCapture(0)`: Initializes a video capture object, capturing video from the default camera (index 0).

5. **Main Loop for Processing Frames**:
   - `while cap.isOpened():`: Starts a loop for processing video frames until the video capture is open.
   - `ret, frame = cap.read()`: Reads a frame from the video capture. `ret` indicates whether a frame was successfully read, and `frame` contains the captured frame.

6. **Converting Frame to RGB**:
   - `frame_rgb = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)`: Converts the BGR frame captured by OpenCV to RGB format, as required by MediaPipe.

7. **Pose Estimation**:
   - `results = pose.process(frame_rgb)`: Processes the RGB frame using the MediaPipe Pose model to detect and estimate human poses.

8. **Drawing Pose Landmarks**:
   - `if results.pose_landmarks:`: Checks if pose landmarks are detected in the frame.
   - `mp_drawing.draw_landmarks(frame, results.pose_landmarks, mp_pose.POSE_CONNECTIONS, ...)`: Draws the detected pose landmarks and connections on the frame using the MediaPipe drawing utilities. Different colors and thicknesses are used for rendering landmarks and connections.

9. **Displaying Frame**:
   - `cv2.imshow("MediaPipe Pose", frame)`: Displays the annotated frame with pose landmarks.

10. **Exiting the Program**:
   - `if cv2.waitKey(5) & 0xFF == 27:`: Waits for the ESC key to be pressed (ASCII value 27) to exit the program.

11. **Releasing Resources**:
   - `cap.release()`: Releases the video capture object.
   - `cv2.destroyAllWindows()`: Closes all OpenCV windows.


*** **Model Complexity -> 0** : by default, the code will run. Keypoints will be less and dynamic movement will also be less. No fluctuate.

*** **Model Complexity -> 1** : If the feature of frame (human) is not available, then system will break ; otherwise continue.

## Keypoints:
- Real-time pose estimation from webcam feed.
- Visualization of detected pose landmarks and connections on the video frame.
- Adjustable confidence thresholds for detection and tracking.
- Utilizes MediaPipe Pose model for accurate pose estimation.
