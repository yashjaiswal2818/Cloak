🪄 Invisibility Cloak using OpenCV

This project creates a Harry Potter-style invisibility cloak using Python and OpenCV.
A red cloth is detected in the webcam feed and replaced with the background, making it look invisible.

🚀 How it Works
Capture background without cloak.
Convert each frame to HSV color space
Detect cloak color (red) using HSV ranges.
Replace cloak pixels with background.
Display final output in real-time.

▶️ Run the Project

Install dependencies:
pip install opencv-python numpy

Run:
python cloak.py


Controls:
ESC → Exit
b → Recapture background

✨ Key Code Steps
cap = cv2.VideoCapture(0)             # Open webcam

bg = cv2.flip(cap.read()[1], 1)       # Capture background

hsv = cv2.cvtColor(frame, cv2.COLOR_BGR2HSV)  # Convert to HSV

mask = cv2.inRange(hsv, lower, upper) # Detect red cloak

cloak = cv2.bitwise_and(bg, bg, mask=mask)  

rest  = cv2.bitwise_and(frame, frame, mask=cv2.bitwise_not(mask))

final = cv2.addWeighted(cloak, 1, rest, 1, 0)  # Merge


📸 Example
Without cloak → background captured.
With red cloak → cloak disappears, background shows.
