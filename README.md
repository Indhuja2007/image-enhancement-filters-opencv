# Image Smoothing and Sharpening Using OpenCV

## Aim

To write a Python program using OpenCV to apply different smoothing filters (Averaging, Weighted Averaging, Gaussian, Median) and sharpening filters (Laplacian Kernel and Laplacian Operator) for image enhancement, and display each result separately along with the original image for comparison.

---

## The program performs the following operations:

- Read and display an input image  
- Apply Averaging filter  
- Apply Weighted Averaging filter  
- Apply Gaussian filter  
- Apply Median filter  
- Apply Laplacian sharpening using kernel  
- Apply Laplacian operator  
- Display all outputs for comparison  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image (e.g., `image.jpg`).

### Step 3:
Convert the image from BGR to RGB format for display.

### Step 4:
Apply Averaging Filter using `cv2.blur()`.

### Step 5:
Apply Weighted Averaging Filter using a custom kernel with `cv2.filter2D()`.

### Step 6:
Apply Gaussian Filter using `cv2.GaussianBlur()`.

### Step 7:
Apply Median Filter using `cv2.medianBlur()`.

### Step 8:
Apply Laplacian Sharpening using Kernel with `cv2.filter2D()`.

### Step 9:
Convert image to grayscale and apply Laplacian Operator using `cv2.Laplacian()`.

### Step 10:
Display all filtered images using a grid layout for comparison.

---

##  Developed By

- **Name: INDHUJA.K** 
- **Register No: 212225040133** 
---

## Program and Output

## Import Required Libraries:
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

## Read the Input Image:
```
img = cv2.imread("paris.jpeg")

if img is None:
    print("Image not found")
else:
    print("Image loaded successfully")
```

## Convert BGR to RGB and Display Original Image:
```
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")
plt.show()
```
<img width="343" height="517" alt="image" src="https://github.com/user-attachments/assets/fefa1841-025e-4968-84dd-8ae116c5c9a8" />

## Apply Averaging Filter:
```
avg = cv2.blur(img, (25, 25))

avg_rgb = cv2.cvtColor(avg, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.imshow(avg_rgb)
plt.title("Averaging Filter")
plt.axis("off")

plt.show()
```
<img width="870" height="522" alt="image" src="https://github.com/user-attachments/assets/8a90c690-8a8c-4db2-9c3d-4f88e1992594" />

## Apply Weighted Averaging Filter:
```
kernel = np.array([[1, 2, 1],
                   [2, 4, 2],
                   [1, 2, 1]], dtype=np.float32) / 16

weighted = cv2.filter2D(img, -1, kernel)

weighted_rgb = cv2.cvtColor(weighted, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.imshow(weighted_rgb)
plt.title("Weighted Averaging Filter")
plt.axis("off")

plt.show()
```
<img width="866" height="523" alt="image" src="https://github.com/user-attachments/assets/ee186261-da86-4474-906f-36d1f536b1ae" />

## Gaussian Filter:
```
gaussian = cv2.GaussianBlur(img, (25, 25), 0)

gaussian_rgb = cv2.cvtColor(gaussian, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.imshow(gaussian_rgb)
plt.title("Gaussian Filter")
plt.axis("off")

plt.show()
```
<img width="865" height="531" alt="image" src="https://github.com/user-attachments/assets/806e0dd0-0958-4ad3-b1f2-6264e292afa3" />

## Median Filter:
```
# Apply Median Filter
median = cv2.medianBlur(img, 5)

# Convert BGR to RGB
median_rgb = cv2.cvtColor(median, cv2.COLOR_BGR2RGB)

# Display Original and Median Filter images
plt.figure(figsize=(12, 5))

plt.subplot(1, 2, 1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.imshow(median_rgb)
plt.title("Median Filter")
plt.axis("off")

plt.show()
```
<img width="977" height="527" alt="image" src="https://github.com/user-attachments/assets/0625059c-9686-4964-9aa8-6da1beff88ba" />

## Laplacian Sharpening Using Kernel:
```
# Convert image to grayscale
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

# Define Laplacian kernel
lap_kernel = np.array([[0, -1, 0],
                       [-1, 4, -1],
                       [0, -1, 0]])

# Apply Laplacian kernel
lap = cv2.filter2D(gray, cv2.CV_64F, lap_kernel)

# Convert to unsigned 8-bit image
lap = cv2.convertScaleAbs(lap)

# Sharpen the image
sharp = cv2.add(gray, lap)

# Display output
plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)
plt.imshow(gray, cmap="gray")
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.imshow(sharp, cmap="gray")
plt.title("Laplacian Sharpening")
plt.axis("off")

plt.show()
```
<img width="862" height="518" alt="image" src="https://github.com/user-attachments/assets/59af6ecf-9bf1-4933-ac0b-7db34d81e450" />

## Laplacian Operator:
```
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

laplacian = cv2.Laplacian(gray, cv2.CV_64F)

laplacian = cv2.convertScaleAbs(laplacian)

plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)
plt.imshow(gray, cmap="gray")
plt.title("Original Grayscale")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.imshow(laplacian, cmap="gray")
plt.title("Laplacian Operator")
plt.axis("off")

plt.show()
```
## <img width="862" height="530" alt="image" src="https://github.com/user-attachments/assets/f03ebc6b-219e-49fa-bb74-93779f3d826c" />

## Display All Outputs Together:
```
# Store all images
images = [img_rgb, avg_rgb, weighted_rgb, gaussian_rgb,
          median_rgb, lap_rgb, laplacian]

# Image titles
titles = ["Original Image", "Averaging Filter",
          "Weighted Averaging", "Gaussian Filter",
          "Median Filter", "Laplacian Sharpening",
          "Laplacian Operator"]

# Create figure
plt.figure(figsize=(15, 12))

# Display all images
for i in range(len(images)):

    plt.subplot(3, 3, i + 1)

    if i == 6:
        plt.imshow(images[i], cmap="gray")
    else:
        plt.imshow(images[i])

    plt.title(titles[i])
    plt.axis("off")

plt.tight_layout()
plt.show()
```
<img width="672" height="647" alt="image" src="https://github.com/user-attachments/assets/4ca8dbaf-406b-4f5b-910a-17e2f214d865" />

### Smoothing Filters

- Averaging filter produces blurred image  
- Weighted averaging provides smoother result with less distortion  
- Gaussian filter preserves edges better while reducing noise  
- Median filter removes salt-and-pepper noise effectively  

###  Sharpening Filters

- Laplacian kernel enhances edges and fine details  
- Laplacian operator detects edges clearly in grayscale  


---

##  Result

Thus, smoothing filters and sharpening filters are successfully implemented using OpenCV.

The smoothing filters reduce noise and improve image quality, while sharpening filters enhance edges and details for better feature extraction.
