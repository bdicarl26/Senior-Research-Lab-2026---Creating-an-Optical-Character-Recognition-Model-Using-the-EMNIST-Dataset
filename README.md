# Senior-Research-Lab-2026---Creating-an-Optical-Character-Recognition-Model-Using-the-EMNIST-Dataset
# Project README

This project focuses on building and training a Convolutional Neural Network (CNN) model using Keras and the EMNIST (Extended MNIST) dataset to recognize handwritten characters. It then applies this trained model to a real-world image containing handwritten text, processing it to predict individual characters, and finally reconstructing the text with contextual and size-based case and spacing adjustments.

## Project Overview

1.  **Data Loading**: The EMNIST 'bymerge' dataset, which includes a comprehensive set of handwritten characters (digits and letters, including some lowercase variants), is loaded from gzipped IDX files stored in Google Drive.
2.  **Data Preparation**: The raw image data is preprocessed, reshaped, and normalized. Labels are converted to a categorical format suitable for neural network training.
3.  **Model Definition and Compilation**: A pre-trained Keras CNN model (`model_final.keras`) is loaded. This model is designed for character recognition.
4.  **Model Training**: The model is further trained or fine-tuned on the loaded EMNIST dataset.
5.  **Character Recognition from Image**: The core of the project involves processing an input image (e.g., `test_example.jpg` or `tnr_alt1_1.png`) to identify and extract individual character contours. Each extracted character image is then preprocessed and fed into the trained CNN model for prediction.
6.  **Text Reconstruction and Refinement**: Predicted characters are assembled into lines of text. Contextual heuristics (e.g., descender detection, size analysis) are applied to refine case predictions and spacing, aiming to produce a more accurate representation of the original handwritten text.
7.  **Markdown Output**: The reconstructed text, with alignment information, is saved to a Markdown file.

## How to Run the Code

1.  **Mount Google Drive**: Ensure your Google Drive is mounted in Colab. The notebook assumes the EMNIST dataset files and pre-trained models are accessible via Google Drive.
    ```python
    from google.colab import drive
    drive.mount('/content/drive')
    ```
2.  **Run All Cells**: Execute all cells in sequential order. The notebook is structured to flow from data loading and preparation to model application and text output.

## Packages, Libraries, and Tools

-   **Python 3**
-   **`emnist`**: For simplified loading of the EMNIST dataset.
-   **`numpy`**: For numerical operations, especially with array manipulation.
-   **`matplotlib`**: For plotting and visualizing images and results.
-   **`keras` / `tensorflow`**: For building, loading, and training the neural network model.
-   **`opencv-python` (cv2)**: For image processing tasks such as contour detection, thresholding, resizing, and drawing on images.
-   **`gzip`**: For decompressing EMNIST data files.
-   **`struct`**: For reading binary data from IDX files.

## Required Setup Steps

1.  **EMNIST Dataset in Google Drive**: The notebook expects the EMNIST 'bymerge' dataset files to be present in your Google Drive at the path specified by the `path` variable. Specifically, it looks for gzipped IDX files within `path + 'gzip/gzip/split_emnist/'`. **These `emnist-bymerge` chunk files (e.g., `emnist-bymerge-train-images-chunk-0-of-8.idx3-ubyte.gz`) must be downloaded from the [EMNIST GitHub repository](https://github.com/sorki/learn-to-read/blob/master/emnist.py) and placed into the specified `split_emnist` directory in your Google Drive.** You will need to download and organize these files accordingly.
2.  **Pre-trained Model**: A pre-trained Keras model named `model_final.keras` (or similar, as defined in the notebook) is expected to be in the `path` directory. This model is loaded for character prediction.
3.  **Input Image**: The notebook uses image files like `test_example.jpg` and `tnr_alt1_1.png` for character recognition. These images should also be placed in your Google Drive at the specified paths.

## Important Notes

-   **File Paths**: All file paths are relative to your Google Drive setup. Ensure the `path` variable (`/content/drive/MyDrive/SRL: Using an EMNIST-Trained Model to Convert Written Text to PDF - Bennett DiCarlo/`) correctly points to the root directory containing your dataset and model files.
-   **Model Training**: The notebook includes a section for training the model. If you intend to use a pre-trained model without further training, you can comment out the `model_suggested.fit()` call to save time. However, some training might be necessary for specific tasks or fine-tuning.
-   **Memory Usage**: Processing the full EMNIST dataset and large images can be memory-intensive. Be mindful of Colab's RAM limits, especially when running on a free tier.
-   **Heuristics for Case/Spacing**: The text reconstruction relies on several heuristics for case prediction (based on size and descender detection) and spacing. These heuristics are tailored to the EMNIST 'bymerge' dataset and might require adjustment for other datasets or handwriting styles.
