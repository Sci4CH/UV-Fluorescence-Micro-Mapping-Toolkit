# UV Fluorescence Micro-Mapping Toolkit

A Python GUI toolkit for processing micro-mapping data from the **Ideaoptics Gora-Lite 405 nm UV Fluorescence Microscopy** system.

This toolkit provides spectral preprocessing, range-based mapping, clustering analysis, ROI tools, interactive GUI visualization, and export of spectra, maps, and clustering results.

---

## Introduction

This Python script is created for processing the micro-mapping data of the **Ideaoptics Gora-Lite 405 nm UV Fluorescence Microscopy** system.

The toolkit is designed for datasets in which:
- each mapping point is stored as an individual JSON spectral file
- mapping parameters are stored in `MappingParameters.json`

---

## Main Features

### Spectral preprocessing
- Cosmic spike removal
- Savitzky–Golay smoothing
- ALS baseline subtraction
- Min-max normalization

### Processing modes
- Full Range Max
- Full Range Max (Log10)
- Full Range Average
- Full Range Average (Log10)
- Range Sum

### Clustering methods
- K-Means
- PCA + K-Means
- t-SNE + K-Means
- UMAP + K-Means
- SOM labeling
- DBSCAN
- Agglomerative

---

## Additional Functions

- Interactive PySide6 GUI
- 2×2 visualization layout:
  - microscopic image
  - mapping
  - spectrum viewer
  - clustering map
- Hover spectrum preview
- Click-to-select pixel and inspect the corresponding spectrum
- Baseline preview overlaid on the raw spectrum
- Save current selected spectrum as:
  - `.jpg`
  - `.svg`
- ROI tools:
  - rectangular ROI
  - polygon ROI
  - ROI transparency overlay
  - ROI pixel list export
  - ROI mean spectrum plotting
  - ROI mean spectrum export as figure and CSV
  - ROI statistics on the current mapping
  - clustering restricted to ROI
- Spot size display mode:
  - Sampling grid mode
  - Physical spot footprint mode
- Batch export of selected mapping modes
- Export of processed figures and data tables
- Cluster result export:
  - clustering map figure
  - cluster label table
  - summary text
  - mean spectra for each cluster
- Dark theme support
- Scrollable control panels for high-density layouts
- Support for dense or overlapped mapping grids inferred from actual filenames

---

## Data Format

The toolkit expects:
- a folder named `OriginalData`
- one mapping parameter file:
  - `MappingParameters.json`
- multiple point-by-point spectrum files:
  - `mapping_X_Y.json`

Example:
- `mapping_1_1.json`
- `mapping_60_60.json`

The spectrum files indicate:
- wavelength values are stored in `Arguments`
- intensity values are stored in `Values`
- mapping parameters include:
  - `XRange`
  - `YRange`
  - `XStep`
  - `YStep`
---

## How to Use

### 1. Install dependencies

```bash
pip install numpy pandas matplotlib scipy scikit-learn umap-learn minisom pillow pyside6
```

### 2. Expected folder structure
```text
ProjectRoot/
├─ MappingArea.png
├─ UVF_micro-mapping_GUI.py
└─ OriginalData/
   ├─ MappingParameters.json
   ├─ mapping_1_1.json
   ├─ mapping_1_2.json
   └─ ...
```

### 3. Run the script
```bash
python UVF_micro-mapping_GUI.py
```

### 4. Load the project in the GUI
- Click **Load Root Folder**
- Select `ProjectRoot/`

### 5. Process your mapping data
Use the GUI to:
- apply preprocessing
- generate mappings
- inspect spectra
- draw ROIs
- run clustering
- export processed results
---
## Output Directory
Generated output goes into:
```text
ProjectRoot/
└─ processed/
```
Typical outputs include:
- mapping figures
- selected spectrum figures
- ROI mean spectrum figures and CSV
- clustering map figures
- clustering label tables
- clustering summary text files
- cluster mean spectra

## Notes
- The toolkit assumes that all mapping points share the same wavelength axis, as expected for measurements acquired with the same spectrometer configuration 
`mapping_1_1.json` `mapping_60_60.json`.
- The mapping grid is inferred from the actual mapping_X_Y.json filenames, rather than assuming a fixed number of points from the scan range alone.
- This allows the toolkit to support denser or overlapped mapping grids as long as the files are present and consistently named.

## License
This project is licensed under the **GNU General Public License v3.0.**

## Author
**Dr. Yu Li**
E-mail: **liyu AT ihep.ac.cn**
