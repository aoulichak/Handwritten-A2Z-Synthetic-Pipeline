# Handwritten-A2Z-Synthetic-Pipeline

## Project Overview
This project provides a comprehensive pipeline for generating high-variance synthetic handwritten character datasets. It was developed to address the scarcity of diverse, labeled handwriting data required for training robust Optical Character Recognition (OCR) systems. The generator bridges the gap between static digital fonts and organic handwriting by utilizing a wide array of typographic sources and advanced computer vision augmentations.

The resulting dataset consists of 359,000 images of uppercase letters (A-Z), formatted to be a drop-in replacement or supplement for standard benchmarks such as EMNIST.

---

## Dataset Specifications
The generated data follows a standardized format optimized for Convolutional Neural Networks (CNNs).

| Feature | Specification |
| :--- | :--- |
| Total Samples | 359,000 |
| Image Dimensions | 28 x 28 pixels |
| Color Space | Grayscale (Mode L) |
| Classes | 26 (Uppercase A-Z) |
| Text Intensity | 0 to 50 (Dark) |
| Background Intensity | 220 to 255 (Light) |

---

## Generation Pipeline
The pipeline is designed for scalability and reproducibility. It follows a four-stage process:

1. **Font Acquisition**: The system queries the Fontsource API to dynamically download hundreds of handwriting-style fonts from the Google Fonts library.
2. **Synthetic Rendering**: Characters are rendered using the TextRecognitionDataGenerator (trdg) engine, which allows for precise control over placement and distortion.
3. **Augmentation**: Each glyph undergoes a series of transformations to simulate real-world handwriting variability and capture imperfections.
4. **Post-Processing**: Images are normalized to 28x28 pixels and exported into a structured directory format.

---

## Data Augmentation Techniques
To ensure model generalization, the following stochastic augmentations are applied:

* **Geometric Transformations**: Random rotation, scaling, and translation.
* **Morphological Variations**: Dynamic adjustment of stroke widths to simulate different writing instruments such as pens, pencils, and markers.
* **Optical Distortions**: Application of Gaussian blur and salt-and-pepper noise to mimic physical scanning conditions.
* **Skewing**: Random slanting of characters to represent various handwriting styles.

---

## Class Distribution
The dataset contains a deliberate class imbalance to reflect real-world data distributions and to encourage the use of robust training strategies such as class weighting or focal loss.

* **Minimum samples per class**: 7,000
* **Maximum samples per class**: 25,000
* **Total count**: 359,000

---

## Installation and Requirements
To replicate the generation process, the following dependencies are required:

```bash
pip install trdg requests pillow numpy matplotlib tqdm
```

The core logic is contained within the provided Jupyter Notebook, which manages font acquisition, image synthesis, and automated reporting.

---

## Credits and Licensing

### Data Licensing
The generated dataset is provided under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license. Users are free to share and adapt the material for any purpose, including commercial use, provided appropriate credit is given to the original creator.

### Source Materials
* **Fonts**: All character images were generated using fonts sourced via **Google Fonts** and the **Fontsource API**. Individual fonts are subject to their respective licenses, typically the **SIL Open Font License (OFL)** or the **Apache License 2.0**.
* **Tools**: The generation pipeline was built using the **TextRecognitionDataGenerator (trdg)** library.

### Citation
If this dataset or the underlying generation pipeline is utilized in academic research or commercial development, please cite this project as the source of the synthetic handwriting data.
