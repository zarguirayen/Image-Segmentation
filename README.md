# A Comparative Review of Chan-Vese, K-Means, and Otsu Image Segmentation Algorithms

[![Language](https://img.shields.io/badge/Language-C%2B%2B-blue.svg)](https://isocpp.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![OpenCV](https://img.shields.io/badge/Library-OpenCV-green.svg)](https://opencv.org/)

A comprehensive university project presenting a comparative analysis of several image segmentation methods. This work was developed by **Rayen Zargui**, **Rayen Mansour**, and **Hana Feki** as part of their curriculum at **ENSTA Paris** & **ENIT**.

This repository contains the source code and findings from our exploration of the Chan-Vese, Otsu, and K-Means algorithms for image segmentation. The project details the evolution of our work, from an initial implementation of Chan-Vese to the evaluation of more robust and effective methods.

## Table of Contents
- [Project Overview](#project-overview)
- [Algorithms Explored](#algorithms-explored)
- [Key Findings](#key-findings)
- [Demonstration](#demonstration)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation and Usage](#installation-and-usage)
- [Difficulties Encountered](#difficulties-encountered)
- [Conclusion & Future Work](#conclusion--future-work)

## Project Overview
Image segmentation is a fundamental task in computer vision that involves partitioning an image into meaningful regions to simplify its analysis. This project initially focused on the **Chan-Vese algorithm**, an active contour model. However, due to its limitations in handling intensity variations and its high computational cost, we expanded our research to include:

- **Otsu's Method**: A histogram-based automatic thresholding technique.
- **K-Means Clustering**: An unsupervised learning algorithm for instance segmentation.

This report documents our methodology, implementation details, validation tests, and a comparative analysis of the performance of these three algorithms.

## Algorithms Explored

### 1. Chan-Vese Algorithm
A variational method that segments an image into two relatively homogeneous regions. It uses a level-set function to represent the evolving contour, making it robust to topological changes.
- **Challenges**: Sensitive to intensity variations, difficulty in detecting sharp boundaries, and high computational cost.

### 2. Otsu's Method
An automatic thresholding technique that finds an optimal threshold to separate foreground from background by maximizing the between-class variance.
- **Strengths**: Simple, fast, and effective for images with bimodal histograms.

### 3. K-Means Clustering
An unsupervised algorithm that groups pixels into K clusters based on their intensity values. It allows for multi-class segmentation, offering more granularity than Otsu's method.
- **Strengths**: More flexible than binary thresholding and can handle more complex images.

## Key Findings
- **Preprocessing is Crucial**: Techniques like grayscale conversion, Gaussian blurring, and histogram equalization significantly improve the performance and reliability of all segmentation algorithms by reducing noise and enhancing contrast.
- **Chan-Vese Limitations**: While theoretically powerful, the Chan-Vese algorithm was found to be less practical for our use cases due to its sensitivity and computational demands.
- **Otsu and K-Means as a Solution**: Otsu's method and K-Means clustering provided more stable, faster, and overall better segmentation results, especially after proper image preprocessing.

## Demonstration

Here is a visual comparison of the results obtained with different algorithms:

| Original Image | Otsu Segmentation | K-Means Segmentation |
|:--------------:|:-------------------:|:----------------------:|
| <img src="assets/sphinx_original.jpg" width="250"> | <img src="assets/sphinx_otsu.png" width="250"> | <img src="assets/sphinx_kmeans.png" width="250"> |

_(Note: You will need to create an `assets` folder and place the relevant images there for this section to display correctly.)_

## Project Structure
```
.
├── src/                # C++ source code for the algorithms
├── images/             # Test images used for validation
├── Report.pdf          # The final project report (this document)
├── README.md           # This README file
└── .gitignore          # Git ignore file
```

## Prerequisites
- A C++ compiler (C++17 or newer)
- [CMake](https://cmake.org/) (version 3.10+)
- [OpenCV](https://opencv.org/) (version 4.x)

## Installation and Usage
1.  **Clone the repository:**
    ```bash
    git clone https://github.com/zarguirayen/Image-Segmentation.git
    cd Image-Segmentation
    ```
2.  **Configure and build the project:**
    ```bash
    mkdir build && cd build
    cmake ..
    make
    ```
3.  **Run an algorithm:**
    ```bash
    ./segmenter <algorithm_name> <input_image_path> <output_image_path>
    ```
    **Example:**
    ```bash
    ./segmenter otsu ../images/cat.jpg ../results/cat_otsu.png
    ```

## Difficulties Encountered
The primary technical challenge was the **installation and configuration of OpenCV in C++**, which involved managing dependencies, compilers, and libraries across different environments. This led us to pivot from our initial, less satisfactory results with the Chan-Vese algorithm towards more robust methods like Otsu's and K-Means.

## Conclusion & Future Work
This project successfully evaluated and compared several core image segmentation algorithms. While the Chan-Vese method proved challenging, Otsu's method and K-Means provided reliable and efficient alternatives.

Future improvements could include integrating machine learning techniques, such as **Convolutional Neural Networks (CNNs)**, for more precise and adaptable segmentation, particularly for complex applications like medical imaging. Our parallel work on 3D brain tumor detection using MRI scans has already shown promising results in this direction.
