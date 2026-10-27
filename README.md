# edge-detection-opencv

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

---

## Software Required

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

## ⚙️ Algorithm

### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using `cv2.imread()`.

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply **Sobel operator** using OpenCV to detect edges.

### Step 5:
Apply **Prewitt operator** using custom kernels.

### Step 6:
Apply **Roberts operator** using custom kernels.

### Step 7:
Apply **Laplacian operator** using OpenCV.

### Step 8:
Apply **Canny edge detector** using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

---

## Developed By

- **Name:** ESWAR S
- **Register No:** 212225230067  

---

## Output

### Original Image
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread('cube.jpg') 
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')
```

<Figure size 640x480 with 1 Axes>

###  Sobel Edge Detector
- Detects edges in horizontal and vertical directions  
- Produces gradient-based edge map  
```
sobel_x = cv2.Sobel(gray_image, cv2.CV_64F, 1, 0, ksize=5)  
sobel_y = cv2.Sobel(gray_image, cv2.CV_64F, 0, 1, ksize=5)  
sobel_combined = cv2.magnitude(sobel_x, sobel_y)  
plt.imshow(sobel_combined, cmap='gray')
plt.title('Sobel Edge Detection')
plt.axis('off')
```
<Figure size 640x480 with 1 Axes>

###  Prewitt Edge Detector
- Similar to Sobel but simpler kernel  
- Detects directional edges  
```
image = cv2.imread("cube.jpg")

gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
prewitt_x = np.array([[1, 0, -1],
                      [1, 0, -1],
                      [1, 0, -1]])

prewitt_y = np.array([[1, 1, 1],
                      [0, 0, 0],
                      [-1, -1, -1]])

prewitt_x_edge = cv2.filter2D(gray, -1, prewitt_x)
prewitt_y_edge = cv2.filter2D(gray, -1, prewitt_y)
prewitt = cv2.magnitude(prewitt_x_edge.astype(np.float32),
                        prewitt_y_edge.astype(np.float32))

plt.imshow(Canny_edges, cmap='gray')
plt.title('Prewitt Edge Detection')
plt.axis('off')
```
<Figure size 640x480 with 1 Axes>

###  Roberts Edge Detector
- Detects edges using diagonal gradients  
- Sensitive to noise  
```
roberts_x = np.array([[1, 0], [0, -1]], dtype=np.float32)
roberts_y = np.array([[0, 1], [-1, 0]], dtype=np.float32)

rx = cv2.filter2D(gray_image, cv2.CV_64F, roberts_x)
ry = cv2.filter2D(gray_image, cv2.CV_64F, roberts_y)

roberts_combined = cv2.magnitude(rx, ry)

plt.imshow(roberts_combined, cmap="gray")
plt.title("Roberts Edge Detection")
plt.axis("off")
plt.show()
```
<Figure size 640x480 with 1 Axes>

###  Laplacian Edge Detector
- Detects edges using second-order derivatives  
- Highlights rapid intensity changes  
```
Laplacian = cv2.Laplacian(gray_image, cv2.CV_64F)
plt.imshow(Laplacian, cmap='gray')
plt.title('Laplacian Edge Detection')
plt.axis('off')
```
<Figure size 640x480 with 1 Axes>

###  Canny Edge Detector
- Multi-stage edge detection  
- Produces clean and thin edges  
```
Canny_edges = cv2.Canny(gray_image, 50, 150)
plt.imshow(Canny_edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')
```
<Figure size 640x480 with 1 Axes>

---

## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.