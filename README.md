# 🌍 Geospatial Drought Analysis & Time-Series Processing (Hungary)

## 📌 Project Overview

This repository contains two Jupyter Notebook workflows developed as part of a GIS and environmental data analysis thesis project focusing on drought-related geospatial processing in Hungary.

The project combines:

1. **Raster-based drought preprocessing and clipping** using data from the European Drought Observatory (EDO)
2. **Temporal analysis and visualization workflows** for processed drought datasets

The workflows are implemented in Python using geospatial and scientific computing libraries such as Rasterio, GeoPandas, Pandas, NumPy, and Matplotlib.

---

# 📂 Repository Structure

```text
.
├── README.md
├── drought_clip.ipynb          # Raster clipping and summer filtering workflow
├── date_n_diss.ipynb           # Temporal analysis and visualization workflow

```

---

# 📘 Notebook Descriptions

## 1️⃣ drought_clip.ipynb

### Purpose

This notebook processes raster datasets obtained from the **European Drought Observatory (EDO)** and clips them to the geographic boundary of Hungary.

The workflow also filters the processed rasters to retain only summer-season observations for further environmental analysis.

### Main Tasks

* Batch processing of `.tif` raster files
* Spatial clipping using Hungary boundary shapefiles
* CRS harmonization
* Summer month filtering (May–September)
* Exporting clipped raster datasets

### Workflow Summary

#### Step 1 — Load Required Libraries

Imports geospatial and file-handling libraries:

```python
import rasterio
import geopandas as gpd
import glob
import os
```

---

#### Step 2 — Define Input and Output Paths

Paths are specified for:

* Input raster datasets
* Hungary shapefile
* Output folders

---

#### Step 3 — Load Hungary Boundary

The shapefile is loaded using GeoPandas:

```python
gdf = gpd.read_file(shapefile_path)
```

---

#### Step 4 — Discover Raster Files

All raster datasets are recursively collected:

```python
raster_files = glob.glob(os.path.join(raster_folder, "**", "*.tif"), recursive=True)
```

---

#### Step 5 — Clip Rasters

Each raster is:

* Opened with Rasterio
* Reprojected if necessary
* Clipped using Hungary geometry
* Saved with updated metadata

---

#### Step 6 — Filter Summer Months 🌞

The notebook extracts dates from raster filenames and retains only:

* May (`05`)
* June (`06`)
* July (`07`)
* August (`08`)
* September (`09`)

Filtered rasters are stored in:

```text
Summer_Rasters/
```

---

## 2️⃣ date_n_diss.ipynb

### Purpose

This notebook focuses on temporal analysis and exploratory processing of drought-related datasets.

The workflow supports:

* Time-series preparation
* Date-based filtering
* Statistical exploration
* Visualization of temporal drought patterns
* Data organization for further thesis analysis

### Main Tasks

* Parsing and formatting date fields
* Time-series aggregation
* Data cleaning and preprocessing
* Exploratory plotting and visualization
* Supporting drought trend interpretation

### Typical Libraries Used

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

---

# ⚙️ Requirements

Install the required dependencies before running the notebooks.

## Core Dependencies

```bash
pip install rasterio geopandas rioxarray xarray matplotlib seaborn pandas numpy scipy
```

## Additional Dependencies

```bash
pip install tqdm
```

---

# 🧪 Recommended Environment

The workflows were developed using:

* Python 3.11
* Jupyter Notebook
* Anaconda environment
* Windows operating system

Using a virtual environment or Conda environment is strongly recommended.

Example:

```bash
conda create -n drought_env python=3.11
conda activate drought_env
```

## ArcPy / ArcGIS Pro Requirement

The `date_n_diss.ipynb` workflow requires an **ArcGIS Pro Python environment** because it uses the `arcpy` library.

This notebook should therefore be run using:

* ArcGIS Pro
* ArcGIS Pro Jupyter Notebook
* or a cloned ArcGIS Pro Conda environment

Example kernel/environment:

```bash
arcgispro-py3
```

If the notebook is opened in a standard Anaconda or Jupyter environment without ArcPy installed, several cells will fail.

For users working outside ArcGIS Pro, it is recommended to:

1. Open ArcGIS Pro
2. Launch the notebook from within ArcGIS Pro
3. Or register the ArcGIS Pro Conda environment as a Jupyter kernel


---

# 📊 Outputs

## Clipped Raster Datasets

Location:

```text
output_folder/
```

Contains raster files clipped to the study area.

---

## Dated and Dissolved .shp files

Location:

```text
outh_folder/
```

Contains shapefiles previously processed from a GDB, data column added and poligons transferred to multipoligons.

---

# ⚠️ Notes & Assumptions

* Raster filenames are expected to contain dates in `YYYYMMDD` format
* CRS mismatches are automatically handled during clipping
* File paths are currently hardcoded in some notebook cells
* Input raster quality and naming consistency are assumed

Before running the notebooks on another machine:

✅ Update local file paths

✅ Verify dependency installation

✅ Ensure raster and shapefile datasets are available locally


# 📚 Use Cases

This repository may be useful for:

* Drought monitoring
* Environmental GIS workflows
* Raster preprocessing
* Seasonal environmental analysis
* Remote sensing studies
* Thesis and academic GIS projects

---

# 👤 Author

Created by Emese Lana Gojdár as part of a GIS thesis workflow focusing on drought analysis and geospatial data processing in Hungary.

