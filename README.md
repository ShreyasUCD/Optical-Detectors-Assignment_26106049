# Space Detector Laboratory  Assignment 2

#### Name: Shreyas Dhumal
#### Student no: 26106049

### Overview

This assignment submission has two Jupyter notebooks containing  two parts of the assignment:
- **`hst-assignment.ipynb`  HST calibration:** This ipynb file workflow reads HST FITS data and mask files, identifies quality flags, applies calibration steps, performs photometric calculations, and compares results with supplied processed images using plots, residual statistics, and histograms.
- **`sentinel-assignment.ipynb`  Hunga Tonga analysis:** This ipynb file workflow calculates the island's land area from Google Earth white-light images, calculates vegetation area from Sentinel-2 bands, plots changes over time, generates spectral indices, and compares those indices with the supplied pipeline products.
The main aim is to document the processing workflow, inspect the images at each stage, and compare the results with reference products.

The notebooks use relative file paths, so I have adjusted the input folders accordingly.

### input-data structure
The notebooks assume that the provided data will be accessible locally.
```text
project-folder/
├── README.md
├── hst-assignment.ipynb
├── sentinel-assignment.ipynb
├── hst-calibration/
│   ├── ubai2505m/
│   ├── ubai2507m/
│   └── ubai2508m/
├── hst-processed/
│   ├── ubai2505m_c0m_aligned.fits
│   ├── ubai2507m_c0m_aligned.fits
│   └── ubai2508m_c0m_aligned.fits
└── sentinel-processed/
    ├── White_light/
    │   └── Google Earth JPG images
    ├── S2_2017-.../
    ├── S2_2018-.../
    └── S2_2019-.../
```


### Software requirements
The notebooks use Python and the following main packages:
- numpy
- matplotlib
- astropy (astropy.io.fits and astropy.stats)
- rasterio
- ipympl for the interactive Matplotlib used in the Sentinel-2 notebook</br>
They can be installed in the Python environment with: </br>
python -m pip install numpy matplotlib astropy rasterio ipympl

### Approach and methods
#### Part 1: HST calibration
The notebook follows the calibration process which are explored in the laboratory materials. It loads raw FITS images and mask data, identifies flag detector pixels, estimates the bias level, and applies bias, dark, and flat-field corrections. It then estimates and subtracts the sky background, performs a photometric flux calculation, and compares the result with supplied processed HST images using image plots, residuals, and histogram statistics.

#### Part 2: Hunga Tonga Analysis

**Google Earth images:** The scale is labelled 600 m and was measured as 307.5 pixels, giving approximately 1.951 m per pixel and 3.807 m² per pixel. An HSV-based colour mask is used to identify land pixels. The estimated land area is plotted against the image dates.

**Sentinel-2 images:** the red (B04) and near-infrared (B08) bands are used to calculate NDVI:

\[
NDVI = \frac{B08 - B04}{B08 + B04}
\]

Pixels with NDVI greater than 0.2 are classified as vegetation for the area estimate. The notebook also calculates the Normalized Water Index using B03 and B08, and a moisture index using B8A and B11. The calculated index images are plotted alongside the supplied pipeline products, and MAE and RMSE calculations are used for quantitative analysis.

### Learning materials and references

The code and workflow were developed with reference to the in-class workshop notebooks, including the Sentinel-2 workshop, and the Space Detector Laboratory guide supplied for the module.  The assignment code was made with the data and questions in this exercise.




    


