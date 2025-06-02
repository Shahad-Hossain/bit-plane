# Bit-Plane Image Encryption Research Project

This is a research project conducted by **Shahad Hossain**, a student at the **College of Staten Island**, under the guidance of **Professor Sos Agaian**. In this project, we aim to explore the potential of using **bit-plane decomposition** with a **random shuffling algorithm** for encrypting images. Our primary goal is to evaluate the efficiency of this novel encryption mechanism for real-time applications such as **object motion detection** and **food safety**. The project explores encryption methods that offer inherent memory and speed advantages compared to traditional encryption techniques, making them suitable for applications where real-time processing is crucial.Feel free to contribute ideas, improvements, and code to this open-source project. Any feedback or suggestions are greatly appreciated.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Code Walkthrough](#code-walkthrough)
- [Contributing](#contributing)
- [License](#license)

## Introduction

This research explores a new approach to encrypting images using **bit-plane decomposition** and **random shuffling algorithms**. The image is first converted to greyscale, then decomposed into its individual bit-planes. These planes are then shuffled using a random algorithm to form an encrypted version of the original image. This process is designed to be computationally efficient, offering potential for applications that require real-time data processing.

The goal of this research is to assess the effectiveness of this encryption mechanism, particularly in **real-time object motion detection** and **food safety**, by measuring performance in terms of speed and memory usage compared to existing encryption schemes.

## Features

- **Greyscale Image Conversion**: Convert images to greyscale using OpenCV.
- **Bit-Plane Decomposition**: Break the greyscale image into 8 individual bit-planes.
- **Encryption with Random Shuffling**: Apply a random shuffling algorithm (Fisher-Yates shuffle) to the bit-planes for image encryption.
- **Open-Source Contribution**: Open for contributions to improve encryption algorithms, memory usage, and application domains.

## Installation

To get started with the project, follow these steps:

1. **Clone the repository**:

    ```bash
    git clone https://github.com/Shahad-Hossain/bit-plane.git
    cd bit-plane
    ```

2. **Install dependencies**:

    Ensure you have Python 3.x and `pip` installed. Then, install the necessary Python packages.

    ```bash
    pip install -r requirements.txt
    ```

## Usage

1. Place your image in the `img/` directory with the name `landscape.jpg`.
   
2. Run the script to see the greyscale image and the bit-plane decomposition:

    ```bash
    python bitplane_encryption.py
    ```

   The script will:
   - Load the image.
   - Convert it to greyscale.
   - Decompose the image into 8 bit-planes.
   - Shuffle the bit-planes to perform encryption (though this part is a work in progress).
   
3. Modify the code to experiment with encryption and decryption methods, or explore other applications like object motion detection.

## Code Walkthrough

### `bitPlanes` Class

- **Constructor**: Takes an image (in `np.ndarray` format) and prepares it for processing.
- **greyScale()**: Converts the image to greyscale.
- **bitPlaneSlices()**: Breaks the image into 8 bit-planes (one for each bit in a byte).
- **map()**: Returns a flattened version of each bit-plane for use in the encryption scheme.

### `Encryption` Class

- **Constructor**: Accepts the bit-plane map for the encryption process.
- **shuffle()**: Implements the Fisher-Yates shuffle algorithm to randomly shuffle the bit-planes.
- **__randomScramblingAlg()**: Applies the random shuffling algorithm to the bit-plane indices.
- **accessRandomScramble()**: Calls the scrambling algorithm.

```python
# Example Usage in Python
from bit_plane_encryption import Encryption, bitPlanes

img_path = "img/landscape.jpg"
image = cv2.imread(img_path)
bitPlane = bitPlanes(image)

# Encryption Process
encryption_obj = Encryption(bitPlane.map())
encryption_obj.access