# 🌍 Geospatial Drought Analysis & Time-Series Processing (Hungary)

## 📌 Project Overview

This repository contains Jupyter Notebook workflows developed as part of a GIS thesis project focusing on drought-related geospatial data processing in Hungary.

The project combines:

* Raster preprocessing from the European Drought Observatory (EDO)
* Temporal data preparation and analysis
* Spatial–temporal dataset structuring for visualization

---

# 📂 Repository Structure

```text
.
├── README.md
├── drought_clip.ipynb
├── date_n_diss.ipynb
├── append_edo_shapefiles_to_geojson.ipynb
```

---

# 📘 Notebook Descriptions

## 1️⃣ drought_clip.ipynb

**Purpose:**
Processes raster datasets from the European Drought Observatory and clips them to Hungary.

**Main steps:**

* Load raster datasets (`.tif`)
* Clip to Hungary boundary
* Harmonize CRS
* Filter summer months (May–September)
* Export processed rasters

---

## 2️⃣ date_n_diss.ipynb

**Purpose:**
Handles temporal preprocessing and exploratory analysis of drought datasets.

**Main steps:**

* Date parsing and formatting
* Time-series preparation
* Data cleaning
* Basic visualization

---

## 3️⃣ append_edo_shapefiles_to_geojson.ipynb

**Purpose:**
Combines multiple date-based shapefiles into a single time-enabled dataset.

**Main steps:**

* Select shapefiles with `_diss` suffix
* Append all features into a single layer
* Preserve attributes (date, category, values)
* Export to GeoJSON

**Use case:**

* Preparing data for:

  * ArcGIS Pro Time Slider
  * Web mapping (e.g. Leaflet)

---

# ⚙️ Requirements

## Core Python libraries

```bash
pip install rasterio geopandas pandas numpy matplotlib seaborn
```

## Optional

```bash
pip install tqdm
```

---

## ArcGIS Pro / ArcPy

The notebook:

```text
date_n_diss.ipynb
append_edo_shapefiles_to_geojson.ipynb
```

requires:

* ArcGIS Pro Python environment (`arcpy`)

Run it using:

* ArcGIS Pro Notebook
* or ArcGIS Pro Conda environment (`arcgispro-py3`)

---

# 📊 Outputs

## Raster outputs

Clipped and filtered raster datasets.

## Vector outputs

* Processed `.shp` files
* Final merged **GeoJSON** with time attributes

---

# ⚠️ Notes

* File paths are hardcoded → update before running
* Input filenames must contain dates (`YYYYMMDD`)
* CRS mismatches are handled during processing
* GeoJSON export is optimized for time-based visualization

---

# 📚 Use Cases

* Drought monitoring
* Environmental GIS workflows
* Time-series geospatial analysis
* Web mapping preparation
* Thesis and academic GIS projects

---

# 👤 Author

Emese Lana Gojdár
GIS thesis project – drought analysis and geospatial processing
