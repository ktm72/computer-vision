# Computer Vision – Image Processing Basics

## Overview

This project implements a classical image-processing pipeline for detecting, analyzing, visualizing, and filtering blob-like objects in an image. Build the pipeline, beginning with image loading and ending with geometric filtering of connected components.

The implementation uses OpenCV and other Python libraries to process the image `blob_img_1.jpg`, which is expected to be available in the `resources` directory.

## Requirements

### Python

Python 3 is required. The notebook was designed to run in a Jupyter Notebook environment, including Google Colab.

### Python packages

Install the following packages:

```bash
pip install numpy opencv-python matplotlib pandas scikit-image
```

| Package | Purpose |
|---|---|
| `numpy` | Numerical operations and array handling |
| `opencv-python` (`cv2`) | Image loading, color conversion, thresholding, filtering, morphology, connected components, contours, and drawing |
| `matplotlib` | Displaying and comparing image-processing results |
| `pandas` | Presenting blob measurements in tabular form |
| `scikit-image` | Additional image-processing and feature utilities used by the course notebook |

The notebook also uses Python standard-library modules such as `os`, `glob`, `zipfile`, and `math`, which do not need to be installed separately.


### Image Loading and Conversion
- Loaded `blob_img_1.jpg` from the `resources` folder using OpenCV.
- Converted the image from OpenCV's BGR color format to RGB for correct visualization.
- Converted the original image to grayscale for subsequent image-processing steps.
- Displayed the RGB and grayscale images side by side.

### Thresholding
- Implemented inverse binary thresholding to separate foreground blobs from the darker background.
- Evaluated a range of threshold values and visualized the resulting binary images for comparison.
- Selected a threshold value based on the visual quality of foreground/background separation.
- Stored the selected threshold in `selected_threshold` and generated the corresponding binary image.

### Gaussian Filtering
- Applied Gaussian smoothing to the grayscale image before thresholding.
- Tested different Gaussian kernel sizes to investigate their effects on noise reduction and blob detail.
- Compared the resulting binary images and selected a kernel size that retained the target blob shapes.
- Stored the selected kernel size in `selected_gaussian_kernel` and the resulting binary image in `binary_filtered`.

### Morphological Opening
- Created rectangular structuring elements of different sizes.
- Applied morphological opening (erosion followed by dilation) to the thresholded image to remove small foreground noise.
- Compared the results for different kernel sizes and selected a suitable size that cleaned the image while preserving the target blobs.
- Stored the selected kernel size in `selected_morphology_kernel` and the cleaned binary image in `binary_clean`.
 
### Connected Component Analysis
- Implemented connected-component detection using OpenCV's `connectedComponentsWithStats()`.
- Identified foreground components while excluding the background label.
- Extracted component statistics, including area, bounding-box width and height, centroid coordinates, and aspect ratio.
- Displayed the label image and compiled the measurements into a table.
- Identified the smallest component, largest component, and component with the largest bounding-box aspect ratio.

### Blob Visualization
- Annotated the original RGB image with bounding boxes, centroids, labels, and blob areas.
- Highlighted the smallest blob, largest blob, and blob with the largest aspect ratio using distinct colors.
- Used a consistent color for the remaining blobs and displayed the final annotated image.

### Contour Detection
- Detected external contours in the cleaned binary image.
- Drew the contours on a copy of the original RGB image.
- Calculated contour area and perimeter.
- Used image moments to estimate contour centroids and annotated the image with contour IDs, areas, and perimeters.
- Displayed the contour visualization.

### Geometric Blob Filtering
- Implemented a filtering function based on connected-component geometric statistics.
- Retained blobs that satisfy all three conditions: area greater than 50 pixels, width greater than 10 pixels, and height greater than 10 pixels.
- Drew bounding boxes and labels for the retained blobs.
- Reported the number of detected blobs before and after filtering and displayed the filtered visualization.


## Input Data

- `blob_img_1.jpg` – the input image used for the blob-detection pipeline.
- `resources/` – the directory containing the course image and any other required resources.

If the course materials provide a `resources.zip` archive, extract it as directed in the notebook so the expected `resources` directory and image files are available.

## Running the Notebook

1. Open `image_processing.ipynb` in Jupyter Notebook or Google Colab.
2. Ensure the required packages are installed.
3. Place or extract the course resource files so `resources/blob_img_1.jpg` is accessible.
4. Run the notebook cells in order.
