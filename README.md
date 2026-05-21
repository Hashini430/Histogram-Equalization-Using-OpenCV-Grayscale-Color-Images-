# Histogram Equalization Using OpenCV (Grayscale & Color Images)

### Developed By: HASHINI.R  
### Register Number: 212224240055  

---

# Aim

To write a Python program using OpenCV to perform histogram equalization on both grayscale and color images to enhance image contrast and brightness.

---

# 🛠️ Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

# ⚙️ Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the image `iron.jpg` in grayscale format.

### Step 3:
Display the grayscale image and plot its histogram.

### Step 4:
Apply histogram equalization using `cv2.equalizeHist()` to enhance contrast.

### Step 5:
Display original grayscale image, its histogram, enhanced image, and its histogram using a `2 × 2` grid.

### Step 6:
Read the same image in color format.

### Step 7:
Split the image into B, G, R channels and plot their histograms.

### Step 8:
Convert the image from BGR to HSV color space.

### Step 9:
Apply histogram equalization on the V (Value) channel.

### Step 10:
Merge the channels and convert the image back to BGR format.

### Step 11:
Display original color image, histogram, enhanced image, and enhanced histogram using a `2 × 2` grid.

---

# 💻 Jupyter Execution

### In [1]:

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

**Output:**

```python
# Libraries imported successfully
```

---

### In [2]:

```python
# Read image
image = cv2.imread('iron.jpg')

# Display original image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis('off')
plt.show()
```

**Output:**

```python
# Original image is displayed
```

---

### In [3]:

```python
# Convert image to grayscale
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Display grayscale image
plt.imshow(gray_image, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')
plt.show()
```

**Output:**

```python
# Grayscale image is displayed
```

---

### In [4]:

```python
# Calculate histogram of original grayscale image
hist_original = cv2.calcHist([gray_image], [0], None, [256], [0, 256])

# Plot histogram
plt.plot(hist_original, color='black')
plt.title("Original Histogram")
plt.xlim([0, 256])
plt.show()
```

**Output:**

```python
# Histogram of original image is displayed
```

---

### In [5]:

```python
# Apply histogram equalization
equalized_image = cv2.equalizeHist(gray_image)

# Display equalized image
plt.imshow(equalized_image, cmap='gray')
plt.title("Equalized Image")
plt.axis('off')
plt.show()
```

**Output:**

```python
# Equalized image is displayed
```

---

### In [6]:

```python
# Calculate histogram of equalized image
hist_equalized = cv2.calcHist([equalized_image], [0], None, [256], [0, 256])

# Plot equalized histogram
plt.plot(hist_equalized, color='black')
plt.title("Equalized Histogram")
plt.xlim([0, 256])
plt.show()
```

**Output:**

```python
# Equalized histogram is displayed
```

---

### In [7]:

```python
# Display grayscale results together
plt.figure(figsize=(10, 7))

plt.subplot(2, 2, 1)
plt.imshow(gray_image, cmap='gray')
plt.title('Original Grayscale Image')
plt.axis('off')

plt.subplot(2, 2, 2)
plt.imshow(equalized_image, cmap='gray')
plt.title('Equalized Image')
plt.axis('off')

plt.subplot(2, 2, 3)
plt.plot(hist_original, color='black')
plt.title('Original Histogram')
plt.xlim([0, 256])

plt.subplot(2, 2, 4)
plt.plot(hist_equalized, color='black')
plt.title('Equalized Histogram')
plt.xlim([0, 256])

plt.tight_layout()
plt.show()
```

**Output:**

```python
# Grayscale histogram equalization results are displayed
```

<img width="1424" height="873" alt="image" src="https://github.com/user-attachments/assets/581197fa-b3fe-4f25-b0f4-4060ab8ac021" />

---

### In [8]:

```python
# Split BGR channels
b, g, r = cv2.split(image)

# Plot BGR histograms
plt.figure(figsize=(8, 5))

plt.plot(cv2.calcHist([b], [0], None, [256], [0, 256]), color='blue')
plt.plot(cv2.calcHist([g], [0], None, [256], [0, 256]), color='green')
plt.plot(cv2.calcHist([r], [0], None, [256], [0, 256]), color='red')

plt.title("BGR Channel Histograms")
plt.xlim([0, 256])
plt.show()
```

**Output:**

```python
# B, G, R histograms are displayed
```

---

### In [9]:

```python
# Convert BGR image to HSV
hsv_image = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)

# Split HSV channels
h, s, v = cv2.split(hsv_image)

# Equalize V channel
v_equalized = cv2.equalizeHist(v)

# Merge HSV channels
hsv_equalized = cv2.merge((h, s, v_equalized))

# Convert back to BGR
enhanced_image = cv2.cvtColor(hsv_equalized, cv2.COLOR_HSV2BGR)

# Display enhanced image
plt.imshow(cv2.cvtColor(enhanced_image, cv2.COLOR_BGR2RGB))
plt.title("Enhanced Color Image")
plt.axis('off')
plt.show()
```

**Output:**

```python
# Enhanced color image is displayed
```

---

### In [10]:

```python
# Display original and enhanced color images

plt.figure(figsize=(10, 7))

plt.subplot(1, 2, 1)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Original Color Image")
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(cv2.cvtColor(enhanced_image, cv2.COLOR_BGR2RGB))
plt.title("Enhanced Color Image")
plt.axis('off')

plt.tight_layout()
plt.show()
```

**Output:**

```python
# Original and enhanced color images are displayed
```

---

# Result

Thus, histogram equalization is successfully performed on both grayscale and color images using OpenCV. The contrast and brightness of the images are significantly improved, enhancing visual quality and feature visibility.
