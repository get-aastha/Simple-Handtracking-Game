# simple_hand_tracking_game

This project is a fun game built with Python libraries OpenCV and MediaPipe. The objective is to touch a moving green circle (enemy) with your index fingertip. Every successful touch increases your score.

# How to Play

1. Open the code on any Python environment (I am using VSCode).
2. Use your index finger to try and touch the green circle (enemy) that appears on the screen.
3. Every successful touch increases your score displayed in the top left corner.
4. The green circle (enemy) will move to a random location after each touch.
5. Press 'q' on your keyboard to quit the game.

# Code Explanation

## Imports:

- mediapipe: This library provides functionalities for hand pose and gesture recognition.
- cv2: OpenCV library for computer vision tasks like video capture and image processing.
- numpy: Used for numerical operations with arrays.
- random: Used to generate random numbers for enemy placement.
  
## Variables:

- score: Keeps track of the game score (number of successful touches).
- x_enemy and y_enemy: Define the random x and y coordinates of the green circle (enemy).

## enemy() function:

- This function draws a green circle at the (x_enemy, y_enemy) coordinates on the frame.
- It also increments the score and updates the enemy position when a successful touch is detected (commented out in the provided code).

## Video Capture and Processing:

- A webcam video capture object is created (video).
- A MediaPipe hand tracking object is created (hands) with specific confidence thresholds.
  
## Main Loop:

- The loop continuously reads frames from the webcam.
- The frame is converted to RGB color format for MediaPipe processing.
- The frame is flipped horizontally (image = cv2.flip(image, 1)) to match our perspective.
- Hand landmarks are detected using the hands.process method.
- The frame is converted back to BGR format for OpenCV display.
- Score and text are displayed on the frame.
- The enemy() function is called to draw the green circle.
- If hand landmarks are detected:
    - It iterates through each hand landmark.
    - It calculates the pixel coordinates for each landmark based on the image dimensions.
    - It checks if the landmark point corresponds to the index fingertip (point=='HandLandmark.INDEX_FINGER_TIP').
    - If yes, it attempts to draw a circle around the fingertip (commented out in the provided code).
    - It then checks if the fingertip is close enough to the enemy's x-coordinate (pixelCoordinatesLandmark[0]).
    - If a successful touch is detected (commented out in the provided code):
    - The score is incremented.
    - The enemy position is updated with random coordinates.
    - The score is displayed on the frame.
    - The enemy() function is called to redraw the enemy at the new location.
- The processed frame is displayed with the title "Hand Tracking".
- The program waits for a 'q' key press to quit.

## Cleanup:

- The video capture object is released.
- All OpenCV windows are closed.

# Demo Video

https://github.com/get-aastha/simple_hand_tracking_game/assets/108509128/0321a228-66fd-4bd8-bd8b-4371ea416a97

