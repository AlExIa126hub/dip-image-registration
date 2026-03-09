# Image Registration

Digital Image Processing project implementing rigid image registration using control points and matrix transformations.

The project aligns a moving image with a fixed image by estimating the optimal rotation and translation between two sets of corresponding control points.

---

# Project Structure

```
image-registration/
│
├── notebooks/
│   └── image_registration.ipynb
│
├── data/
│   ├── image_fixed.png
│   └── image_moving.png
│
└── README.md
```

---

# Project Overview

Image registration is the process of aligning two or more images so that corresponding structures overlap correctly.

This technique is widely used in:

- medical imaging
- remote sensing
- computer vision
- image fusion

In this project, a **rigid transformation** is used to align a moving image with a fixed reference image.

Rigid transformations preserve distances and angles and consist only of:

- rotation
- translation

---

# Methodology

The alignment between the two images is estimated using corresponding control points selected on both images.

The following steps are implemented.

---

## 1. Control Point Selection

Corresponding control points are defined on:

- the fixed image
- the moving image

These points represent the same physical locations in both images.

---

## 2. Centroid Calculation

The centroid (mean position) of each point set is calculated.

This step helps normalize the coordinates of the points before computing the transformation.

---

## 3. Mean Centering

Both point sets are centered by subtracting their centroids.

This simplifies the computation of the rotation between the point sets.

---

## 4. Covariance Matrix

A covariance matrix is computed using the centered point sets.

This matrix captures the relationship between the coordinates of both point sets.

---

## 5. Singular Value Decomposition (SVD)

Singular Value Decomposition is applied to the covariance matrix.

The SVD result is used to compute the optimal rotation matrix that aligns the moving points with the fixed points.

---

## 6. Rotation Matrix

The rotation matrix is computed from the SVD components.

This matrix describes how the moving image must be rotated to align with the fixed image.

---

## 7. Translation Vector

After computing the rotation, the translation vector is calculated using the centroids of both point sets.

This vector shifts the rotated image so that the control points overlap.

---

## 8. Image Transformation

The final transformation is applied to the moving image:

```
Aligned Image = Rotation + Translation
```

The transformed moving image is then displayed together with the fixed image to verify the alignment.

---

# Results

The final output shows the moving image superimposed onto the fixed image after applying the estimated transformation.

Successful registration demonstrates that the computed rotation and translation correctly align the corresponding structures in both images.

---

# Technologies Used

- Python
- NumPy
- OpenCV
- Matplotlib
- Jupyter Notebook

---

# Running the Project

Clone the repository:

```
git clone <repository-url>
```

Install dependencies:

```
pip install numpy opencv-python matplotlib
```

Launch Jupyter Notebook:

```
jupyter notebook
```

Open and run:

```
notebooks/image_registration.ipynb
```

---

# Concepts Demonstrated

This project demonstrates several key concepts in digital image processing and computer vision:

- image registration
- rigid transformations
- control points
- centroid alignment
- covariance matrices
- singular value decomposition (SVD)
- rotation and translation estimation
