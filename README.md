# Geometric Transformations Using OpenCV

## AIM

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

1. Image Translation
2. Image Scaling (Resizing)
3. Image Shearing
4. Image Reflection (Flipping)
5. Image Rotation

## SOFTWARE REQUIRED

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (`cv2`)
- NumPy
- Matplotlib

## ALGORITHM

**Step 1:** Import the required libraries: OpenCV, NumPy, and Matplotlib.

**Step 2:** Read the input image `images.jpg` in color mode and convert it from BGR to RGB format.

**Step 3: Image Translation**

- Create a translation matrix to shift the image.
- Move the image 50 pixels to the right and 80 pixels down.
- Apply transformation using `cv2.warpAffine()`.
- Display original and translated images.

**Step 4: Image Scaling**

- Resize the image to 0.5× (downscale).
- Resize the image to 2× (upscale).
- Use `cv2.resize()`.
- Display original, downscaled, and upscaled images.

**Step 5: Image Shearing**

- Create transformation matrices for horizontal and vertical shearing.
- Apply transformations using `cv2.warpAffine()`.
- Adjust output dimensions to avoid cutting off the sheared image.
- Display original and sheared images.

**Step 6: Image Reflection**

Perform flipping using `cv2.flip()`:

- Horizontal reflection.
- Vertical reflection.
- Both-axis reflection.

Display all reflected images.

**Step 7: Image Rotation**

- Create rotation matrices for 45° and 90° rotation.
- Use `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`.
- Display original and rotated images.

## PROGRAM DEVELOPED BY

**NAME:** VARUN A

**REG NO:** 212224240178

## PROGRAM

### 1. Import the required libraries.

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

### 2. Create a helper function to display multiple images.

```python
def show_images(titles, images, rows, cols):
    plt.figure(figsize=(15, 5 * rows))
    for i in range(len(images)):
        plt.subplot(rows, cols, i + 1)
        plt.imshow(images[i])
        plt.title(titles[i])
        plt.axis('off')
    plt.tight_layout()
    plt.show()
```

### 3. Read the input image and convert BGR to RGB format.

```python
image = cv2.imread('images.jpg')
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
rows, cols, channels = image_rgb.shape
```

### 4. Perform Image Translation.

```python
tx, ty = 50, 80
M_translation = np.float32([[1, 0, tx], [0, 1, ty]])
translated_image = cv2.warpAffine(image_rgb, M_translation, (cols, rows))

show_images(['Original Image', 'Translated (Right 50, Down 80)'],
            [image_rgb, translated_image], 1, 2)
```

### 5. Perform Image Scaling (Resizing).

```python
downscaled_image = cv2.resize(image_rgb, None, fx=0.5, fy=0.5, interpolation=cv2.INTER_AREA)
upscaled_image = cv2.resize(image_rgb, None, fx=2.0, fy=2.0, interpolation=cv2.INTER_CUBIC)

show_images(['Original Image', 'Downscaled (0.5x)', 'Upscaled (2x)'],
            [image_rgb, downscaled_image, upscaled_image], 1, 3)
```

### 6. Perform Image Shearing.

```python
shx, shy = 0.2, 0.2
M_shear_x = np.float32([[1, shx, 0], [0, 1, 0]])
M_shear_y = np.float32([[1, 0, 0], [shy, 1, 0]])

sheared_x = cv2.warpAffine(image_rgb, M_shear_x, (int(cols + rows * shx), rows))
sheared_y = cv2.warpAffine(image_rgb, M_shear_y, (cols, int(rows + cols * shy)))

show_images(['Original Image', 'Horizontally Sheared', 'Vertically Sheared'],
            [image_rgb, sheared_x, sheared_y], 1, 3)
```

### 7. Perform Image Reflection (Flipping).

```python
flip_h = cv2.flip(image_rgb, 1)
flip_v = cv2.flip(image_rgb, 0)
flip_both = cv2.flip(image_rgb, -1)

show_images(['Original Image', 'Horizontally Flipped', 'Vertically Flipped', 'Both-axis Flipped'],
            [image_rgb, flip_h, flip_v, flip_both], 1, 4)
```

### 8. Perform Image Rotation.

```python
center = (cols // 2, rows // 2)

M_rot_45 = cv2.getRotationMatrix2D(center, 45, 1.0)
M_rot_90 = cv2.getRotationMatrix2D(center, 90, 1.0)

rotated_45 = cv2.warpAffine(image_rgb, M_rot_45, (cols, rows))
rotated_90 = cv2.warpAffine(image_rgb, M_rot_90, (cols, rows))

show_images(['Original Image', '45° Rotated', '90° Rotated'],
            [image_rgb, rotated_45, rotated_90], 1, 3)
```

## OUTPUT

<img width="1257" height="370" alt="Screenshot 2026-11-17 090656" src="https://github.com/user-attachments/assets/0bada6ba-c3ec-49bb-9dd0-9ab8cddb5bc7" />

<img width="1397" height="270" alt="Screenshot 2026-11-17 090711" src="https://github.com/user-attachments/assets/a13ce463-1df4-48d9-b29b-489049ebd130" />

<img width="1286" height="556" alt="Screenshot 2026-11-17 090722" src="https://github.com/user-attachments/assets/bf465006-7dd7-4419-a6d3-5ff3a8c51944" />

<img width="1506" height="277" alt="Screenshot 2026-11-17 090728" src="https://github.com/user-attachments/assets/3e93b993-d355-4a88-9df7-cb9bf5b4547e" />




## RESULT

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation were successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
