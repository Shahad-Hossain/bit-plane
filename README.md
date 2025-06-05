# Bit-Plane Image Encryption Research Project

This is a research project conducted by **Shahad Hossain**, a student at the **College of Staten Island**, under the guidance of **Professor Sos Agaian**. In this project, we explore the potential of using **bit-plane decomposition** combined with a **secure random shuffling algorithm** for encrypting images. Our aim is to test the computational efficiency and practical viability of this lightweight encryption technique for real-time use cases such as **object motion detection** and **food safety analysis**.

Feel free to contribute ideas, improvements, and code to this open-source project. Feedback and suggestions are always welcome.

## 📚 Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Code Walkthrough](#code-walkthrough)
- [Contributing](#contributing)
- [License](#license)

## 🔍 Introduction

This project implements a lightweight image encryption system that decomposes grayscale images into bit-planes and applies a randomized scrambling algorithm to encrypt them. The encrypted image is reconstructed from the shuffled bit-planes. We aim to analyze its speed, memory efficiency, and suitability for real-time environments.

The encryption uses a secure version of the **Fisher-Yates shuffle** via Python's `secrets` module to generate cryptographically secure permutations.

## ✨ Features

- **Grayscale Conversion**: Converts input color images to grayscale using OpenCV.
- **Bit-Plane Decomposition**: Separates the grayscale image into its 8 constituent bit-planes.
- **Secure Encryption**: Applies cryptographically strong shuffling to encrypt each bit-plane using two random keys.
- **File Saving**: Stores encrypted bit-planes and keys to disk (`.npy` and `.csv` respectively).
- **Decryption**: Reconstructs the original grayscale image using the stored keys and reshaped bit-planes.
- **Visualization**: Displays each encrypted bit-plane and the final decrypted image using Matplotlib.

## ⚙️ Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Shahad-Hossain/bit-plane.git
   cd bit-plane
   ```

2. **Install dependencies**:
   Make sure Python 3.x is installed. Then install the required libraries:
   ```bash
   pip install -r requirements.txt
   ```

## 🚀 Usage

1. Place your input image (e.g., `space_invader.png`) in the `img/` folder.

2. Run the main script:
   ```bash
   python bitplane_encryption.py
   ```

3. The script will:
   - Convert the image to grayscale
   - Decompose it into 8 bit-planes
   - Encrypt the bit-planes using a secure shuffle
   - Save the keys and encrypted bit-planes to disk
   - Load the keys and encrypted data
   - Decrypt and reconstruct the image
   - Display each encrypted bit-plane and the final decrypted output

## 🧠 Code Walkthrough

### `bitPlanes` Class
- **`__init__(image)`**: Initializes the image.
- **`greyScale(img)`**: Converts BGR image to grayscale.
- **`bitPlaneSlices()`**: Returns 8 individual bit-planes.
- **`map()`**: Returns a dictionary of flattened bit-planes for encryption.
- **`merge()`**: Reconstructs the grayscale image from bit-planes.

### `Encryption` Class
- **`__init__(bitPlaneIndiceMap)`**: Accepts the mapped bit-planes.
- **`shuffle(list)`**: Securely shuffles using Python's `secrets` module.
- **`__randomScramblingAlg()`**: Applies two rounds of secure shuffling on each bit-plane using `KEY1` and `KEY2`.
- **`saveToFile(filename)`**: Saves the scrambled bit-planes and keys to disk.

### Decryption (in your main script)
- Keys and encrypted planes are loaded from CSV and `.npy` files.
- Decryption applies reverse scrambling using the stored keys.
- The final image is merged and displayed.

## 👥 Contributing

Pull requests, issue reports, and feature suggestions are welcome! Feel free to fork the repo and submit improvements, especially related to:
- Speed optimization
- Memory efficiency
- Real-time application use cases
- Advanced image encryption techniques

## 📝 License

This project is open-source and free to use under the **MIT License**. See the [LICENSE](LICENSE) file for details.
