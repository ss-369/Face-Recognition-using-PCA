# Face-Recognition-using-PCA

This project implements a **face recognition system** using the **Principal Component Analysis (PCA)** technique. The system projects facial images onto a "face space" defined by the eigenfaces, which are the eigenvectors of the set of faces. The goal is to recognize a person's face by comparing it to a pre-existing database of faces and identifying the closest match.

This project is part of **SMAI Assignment - 2, Question 3** and uses the **AT&T Face Dataset**.

---

## **Project Description**

The project includes:
1. **PCA Implementation**: The PCA algorithm is implemented from scratch to extract eigenfaces from the training data.
2. **Image Reconstruction**: Test images are reconstructed using eigenfaces for different numbers of components, visualizing the impact of dimensionality reduction.
3. **Face Recognition Module**: A recognition system that identifies a face using the L2 norm (Euclidean distance) between projections in the eigenface space.
4. **Evaluation and Analysis**:
   - Accuracy of the recognition system for different numbers of eigenfaces.
   - Mean squared error (MSE) and semi-log plots to analyze reconstruction quality.

---

## **Dataset**

### AT&T Face Dataset
- **Description**: Contains grayscale images of 40 subjects, each with 10 variations.
- **Image Details**:
  - Dimensions: \(92 \times 112\) pixels (grayscale).
  - Variations: Images differ in lighting, facial expressions, and details (e.g., glasses).
- **Structure**:
  - Each subject's images are stored in a folder named `sX`, where `X` is the subject number.
  - Images are named `Y.pgm`, where `Y` is the image number (1 to 10).

- **Link**: [AT&T Face Dataset](https://git-disl.github.io/GTDLBench/datasets/att_face_dataset/)

---

## **Project Workflow**

### 1. **Data Preparation**
- Images are loaded, labeled, and split into training (90%) and test sets (10%) while ensuring at least one image per subject in the test set.
- Each image is flattened into a 1D array for PCA computation.

### 2. **PCA Implementation**
- **Steps**:
  - Compute the mean face and center the data.
  - Calculate the covariance matrix and its eigenvalues/eigenvectors.
  - Sort eigenvectors by eigenvalues in descending order.
  - Select the top \(k\) eigenvectors (principal components).

### 3. **Visualization**
- **Eigenfaces**: Visualize the top eigenfaces (principal components).
- **Mean Face**: Display the average face of the dataset.
- **Image Reconstruction**: Reconstruct test images for various numbers of eigenfaces (e.g., 5, 10, 50).

### 4. **Face Recognition**
- **Recognition Process**:
  - Project training and test images onto the eigenface space.
  - Identify the closest match in the training set using the L2 norm.
- **Accuracy**:
  - Test the recognition system with varying numbers of eigenfaces.
  - Analyze accuracy as the number of components increases.

### 5. **Evaluation**
- **Mean Squared Error (MSE)**: Measure reconstruction quality for different numbers of eigenfaces.
- **Semi-log Plot**: Plot MSE on a logarithmic scale for deeper analysis.

---

## **Key Results**

1. **Accuracy**:
   - Recognition accuracy improves with the number of eigenfaces.
   - Saturation is observed beyond 10 components, achieving ~95% accuracy.

2. **Reconstruction Error**:
   - MSE decreases sharply with more eigenfaces.
   - Minimal improvement in reconstruction quality beyond 10 components.

---

## **How to Run the Project**

### **Prerequisites**
- Python 3.x
- Required libraries: `numpy`, `matplotlib`, `cv2`, `os`, `tqdm`

### **Steps**
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/ss-369/Face-Recognition-using-PCA.git
   cd Face-Recognition-using-PCA
   ```

2. **Download the Dataset**:
   - Download the AT&T Face Dataset from [here](https://git-disl.github.io/GTDLBench/datasets/att_face_dataset/).
   - Place it in the project directory under a folder named `ATnT`.

3. **Run the Code**:
   - Open and run the notebook `facedetection.ipynb` for step-by-step implementation.

---

## **Observations**

1. **Effect of Components on Accuracy**:
   - Accuracy improves significantly with the number of components up to 10, then plateaus.
   - Maximum accuracy: ~95%.

2. **Effect of Components on Reconstruction Error**:
   - MSE decreases sharply with increasing components initially, reaching a stable value around 10 components.

3. **Trade-offs**:
   - Using fewer components reduces computation but sacrifices accuracy.
   - Adding more components increases complexity without significant gains in accuracy.

---

## **References**
- **Eigenfaces Paper**: [Eigenfaces for Recognition](https://sites.cs.ucsb.edu/~mturk/Papers/mturk-CVPR91.pdf)
- **AT&T Dataset**: [AT&T Face Dataset](https://git-disl.github.io/GTDLBench/datasets/att_face_dataset/)

---
