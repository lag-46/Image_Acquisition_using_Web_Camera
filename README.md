# Experiment 02 -- Image Acquisition Using Web Camera

### Name :PANDEESWARAN N
### Reg no: 212224230191

## Aim

To acquire an image using a web camera and display the captured image
and video. To resize and rotate the video frames using OpenCV.

## Procedure

1.  Import the required libraries: OpenCV (`cv2`), Matplotlib,
    `clear_output`, and `time`.
2.  Initialize the webcam using `cv2.VideoCapture(0)`.
3.  Capture a frame from the webcam and save it as `my.jpeg` using
    `cv2.imwrite()`.
4.  Read the saved image using `cv2.imread()` and display it using
    Matplotlib.
5.  Capture and display video frames continuously for a specified number
    of iterations.
6.  Resize each video frame using `cv2.resize()` and display the resized
    frames.
7.  Rotate each video frame by 90 degrees clockwise using `cv2.rotate()`
    and display the rotated frames.
8.  Release the webcam using `cap.release()` after each operation.

## Program

``` python
import cv2
import matplotlib.pyplot as plt
from IPython.display import clear_output
import time

# i) Capture and display an image using the webcam
cap = cv2.VideoCapture(0)
ret, frame = cap.read()

if ret:
    cv2.imwrite("my.jpeg", frame)

cap.release()

captured_image = cv2.imread("my.jpeg")

if captured_image is not None:
    plt.imshow(captured_image[:, :, ::-1])
    plt.title("Captured Frame")
    plt.axis("off")
    plt.show()

# ii) Display the video
cap = cv2.VideoCapture(0)

for i in range(50):
    ret, frame = cap.read()
    if not ret:
        break

    frame_rgb = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)
    clear_output(wait=True)
    plt.imshow(frame_rgb)
    plt.axis("off")
    plt.show()
    time.sleep(0.05)

cap.release()

# iii) Display the video by resizing the frames
cap = cv2.VideoCapture(0)

for i in range(50):
    ret, frame = cap.read()
    if not ret:
        break

    resized_frame = cv2.resize(frame, (100, 150))
    frame_rgb = cv2.cvtColor(resized_frame, cv2.COLOR_BGR2RGB)
    clear_output(wait=True)
    plt.imshow(frame_rgb)
    plt.axis("off")
    plt.show()
    time.sleep(0.05)

cap.release()

# iv) Rotate and display the video
cap = cv2.VideoCapture(0)

for i in range(50):
    ret, frame = cap.read()
    if not ret:
        break

    rotated_frame = cv2.rotate(frame, cv2.ROTATE_90_CLOCKWISE)
    frame_rgb = cv2.cvtColor(rotated_frame, cv2.COLOR_BGR2RGB)
    clear_output(wait=True)
    plt.imshow(frame_rgb)
    plt.axis("off")
    plt.show()
    time.sleep(0.05)

cap.release()
```

## Output

**Image Acquisition:**

<img width="687" height="532" alt="image" src="https://github.com/user-attachments/assets/bb966c19-d9e4-450d-b37b-4cf97f17668c" />


**Video Display:**

<img width="765" height="488" alt="image" src="https://github.com/user-attachments/assets/fca4eb31-aead-4895-8701-4f2364175b16" />

**Resized Video:** 

<img width="382" height="492" alt="image" src="https://github.com/user-attachments/assets/f83c0642-111e-40ea-9869-9fd1177e6788" />

**Rotated Video:**
   
<img width="413" height="496" alt="image" src="https://github.com/user-attachments/assets/2a3e99a2-0898-4123-ba1a-a1055bba2421" />



## Result

Thus, an image was successfully acquired using the web camera, and the
video was displayed in its original, resized, and 90-degree clockwise
rotated forms using OpenCV.
