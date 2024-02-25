# Image Augmentation

## Introduction
This project focuses on augmenting MRI data to enhance datasets for machine learning in medical diagnostics. It utilizes Python to simulate various realistic conditions in MRI imaging, such as noise addition and k-space truncation.

## System Requirements
- **Platform**: Python 3.x
- **Environment**: Jupyter Notebook (for `.ipynb` file execution)

## Dependencies
Required libraries and their versions:
- `numpy`
- `PIL` (Pillow)
- `matplotlib`
- `imgaug`
- `os` (standard library in Python)
- `scipy.fft`

## Setting Up the Environment
1. **Install Python**: Download Python 3.x from [python.org](https://www.python.org/downloads/).
2. **Virtual Environment (Optional)**:
   - Create and activate a virtual environment:
     ```bash
     python -m venv venv
     # Windows
     venv\Scripts\activate
     # macOS/Linux
     source venv/bin/activate
     ```
3. **Install Dependencies**:
   - Use pip to install the required libraries:
     ```bash
     pip install numpy pillow matplotlib imgaug scipy
     ```

## Project Structure
- **Input Directory (`images_folder`)**:
  - Create a folder named `images_folder` in your project directory.
  - Place all high-quality MRI images in this folder. Supported formats include `.png`, `.jpg`, and `.jpeg`.

- **Output Directory (`output`)**:
  - The script will automatically create an `output` folder in your project directory.
  - All augmented images, including low-quality, Gaussian noisy, and salt-and-pepper noisy images, will be saved here with descriptive filenames.

## Running the Code
1. **Start Jupyter Notebook**:
   - Launch Jupyter Notebook within your project directory:
     ```bash
     jupyter notebook
     ```
2. **Execute the Notebook (`FMI_Final_code-2.ipynb`)**:
   - Open the notebook and run the cells in sequence to process the images.

## Notes
- Ensure the input and output folder paths are correctly set in the code.
- Adjust augmentation parameters (e.g., noise levels, k-space truncation factors) as per your requirement. It will be explained in detail in the below section.
- The project is designed to handle a large number of images. However, processing time and memory usage may vary based on image size and quantity.

### Augmentation Parameters

The project utilizes several parameters to control the augmentation process, ensuring the generated images closely mimic real-world MRI scenarios. Understanding these parameters is crucial for fine-tuning the augmentation effects:

1. **Gaussian Noise Parameters**:
   - **Mean (`mean`)**: The average value of the Gaussian noise distribution, typically set to 0. This represents the baseline level of noise.
   - **Standard Deviation (`sigma`)**: Determines the spread or intensity of the Gaussian noise. A higher sigma value results in more pronounced noise, affecting the image's clarity.

2. **Salt-and-Pepper Noise Parameters**:
   - **Noise Ratio (`salt_pepper_ratio`)**: Dictates the proportion of salt (white) to pepper (black) noise. A ratio of 0.5 typically implies equal amounts of both.
   - **Amount (`amount`)**: Specifies the percentage of pixels in the image to be affected by the salt-and-pepper noise. Increasing this value results in a higher density of noise pixels.

3. **K-Space Truncation Factor**:
   - This factor determines the extent of k-space data that is retained during truncation. A smaller truncation factor simulates a lower resolution by retaining less high-frequency data in the k-space representation.

4. **Image Augmentation Techniques** (Implemented using `imgaug` library):
   - **Affine Transformations**: Includes rotation (within a specified range) and scaling. These transformations simulate the variations due to patient positioning and camera angles.
   - **Flipping**: Both horizontal (left-right) and vertical (up-down) flipping are used, reflecting the arbitrary orientation of images in real-world scenarios.
   - **Gaussian Blur (`sigma`)**: Adds blur to the image, which can simulate motion blur or focus issues in MRI imaging. The intensity of the blur is controlled by the `sigma` value.

These parameters play a pivotal role in the augmentation process, allowing for a customizable and realistic simulation of various imaging conditions. Adjusting these parameters can help in creating a dataset that is more representative of the challenges encountered in medical imaging and is thus invaluable for training robust machine learning models.

