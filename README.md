# Geometric Transformations Using OpenCV

---

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image in color mode.

### Step 3: Image Translation
- Create a translation matrix to shift the image  
- Move the image 50 pixels to the right and 80 pixels down  
- Apply transformation using `cv2.warpAffine()`  
- Display original and translated images  

### Step 4: Image Scaling
- Resize the image to 0.5× (downscale)  
- Resize the image to 2× (upscale)  
- Use `cv2.resize()`  
- Display original, downscaled, and upscaled images  

### Step 5: Image Shearing
- Create transformation matrices for:
  - Horizontal shearing  
  - Vertical shearing  
- Apply transformations using `cv2.warpAffine()`  
- Display original and sheared images  

### Step 6: Image Reflection
- Perform flipping using `cv2.flip()`:
  - Horizontal reflection  
  - Vertical reflection  
  - Both axes  
- Display all reflected images  

### Step 7: Image Rotation
- Create rotation matrices for:
  - 45° rotation  
  - 90° rotation  
- Use `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`  
- Display original and rotated images  

---

##  Program
~~~
# Step 1: Import the required libraries: OpenCV, NumPy, and Matplotlib[cite: 5].
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 2: Read the input image (e.g., image.jpg)[cite: 5].
image_bgr = cv2.imread('images.jpg')

# Step 3: Convert the image from BGR to RGB format for display[cite: 5].
image_rgb = cv2.cvtColor(image_bgr, cv2.COLOR_BGR2RGB)

# Step 4: Apply Averaging Filter using cv2.blur()[cite: 5].
# Using a 5x5 kernel here for standard blurring
avg_filter = cv2.blur(image_rgb, (5, 5))

# Step 5: Apply Weighted Averaging Filter using a custom kernel with cv2.filter2D()[cite: 5].
# Defining a standard 3x3 weighted averaging kernel
kernel_weighted = np.array([[1, 2, 1],
                            [2, 4, 2],
                            [1, 2, 1]]) / 16.0
weighted_avg_filter = cv2.filter2D(image_rgb, -1, kernel_weighted)

# Step 6: Apply Gaussian Filter using cv2.GaussianBlur()[cite: 4].
gaussian_filter = cv2.GaussianBlur(image_rgb, (5, 5), 0)

# Step 7: Apply Median Filter using cv2.medianBlur()[cite: 4].
median_filter = cv2.medianBlur(image_rgb, 5)

# Step 8: Apply Laplacian Sharpening using Kernel with cv2.filter2D()[cite: 4].
# Defining a standard 3x3 Laplacian sharpening kernel
kernel_sharpening = np.array([[0, -1, 0],
                              [-1, 5, -1],
                              [0, -1, 0]])
laplacian_sharpen = cv2.filter2D(image_rgb, -1, kernel_sharpening)

# Step 9: Convert image to grayscale and apply Laplacian Operator using cv2.Laplacian()[cite: 4].
image_gray = cv2.cvtColor(image_bgr, cv2.COLOR_BGR2GRAY)
laplacian_operator = cv2.Laplacian(image_gray, cv2.CV_64F)

# Step 10: Display all filtered images using a grid layout for comparison[cite: 4].
plt.figure(figsize=(15, 10))

plt.subplot(3, 3, 1)
plt.imshow(image_rgb)
plt.title('Original Image')
plt.axis('off')

plt.subplot(3, 3, 2)
plt.imshow(avg_filter)
plt.title('Averaging Filter')
plt.axis('off')

plt.subplot(3, 3, 3)
plt.imshow(weighted_avg_filter)
plt.title('Weighted Averaging Filter')
plt.axis('off')

plt.subplot(3, 3, 4)
plt.imshow(gaussian_filter)
plt.title('Gaussian Filter')
plt.axis('off')

plt.subplot(3, 3, 5)
plt.imshow(median_filter)
plt.title('Median Filter')
plt.axis('off')

plt.subplot(3, 3, 6)
plt.imshow(laplacian_sharpen)
plt.title('Laplacian Sharpening (Kernel)')
plt.axis('off')

plt.subplot(3, 3, 7)
plt.imshow(laplacian_operator, cmap='gray')
plt.title('Laplacian Operator (Grayscale)')
plt.axis('off')

plt.tight_layout()
plt.show()
~~~

### Developed By:
**Name:** Varun Aravamudhan

### Register No:
212224240178
---

##  Output

<img width="1405" height="777" alt="image" src="https://github.com/user-attachments/assets/6efa8695-92c2-4dbc-bee3-e2793555fe74" />


### Image Translation
- Original image is displayed  
- Translated image (shifted right and down) is displayed  

### Image Scaling
- Original image is displayed  
- Downscaled image (0.5×) is displayed  
- Upscaled image (2×) is displayed  

### Image Shearing
- Original image is displayed  
- Horizontally sheared image is displayed  
- Vertically sheared image is displayed  

### Image Reflection
- Original image is displayed  
- Horizontally flipped image is displayed  
- Vertically flipped image is displayed  
- Both-axis flipped image is displayed  

### Image Rotation
- Original image is displayed  
- 45° rotated image is displayed  
- 90° rotated image is displayed  

---

##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
