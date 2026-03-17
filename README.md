# 🌍 Drought Raster Processing & Analysis (Hungary)

## 📌 Overview

This project processes raster data from the **European Drought Observatory (EDO)** and clips it to the geographic boundary of Hungary (previously extended with a 50 km buffer). It then filters the dataset to retain only **summer months (May–September)** for further analysis.

The workflow is implemented in a Jupyter Notebook and focuses on:

* Batch processing of `.tif` raster files
* Spatial clipping using a country shapefile
* Coordinate Reference System (CRS) alignment
* Seasonal filtering of raster datasets

---

## 🗂️ Project Structure

```
.
├── drought_test.ipynb        # Main processing notebook
├── data/
│   ├── EuropeanDroughtObservatory/   # Raw raster files (.tif)
│   ├── hungary_shape/                # Hungary shapefile
│   ├── Clipped/                      # Output: clipped rasters
│   └── Summer_Rasters/               # Output: summer-only rasters
```

---

## ⚙️ Requirements

Install the required Python libraries:

```bash
pip install rasterio geopandas
```

### Dependencies

* `rasterio` – raster data processing
* `geopandas` – vector data handling
* `glob` / `pathlib` – file handling
* `os` – directory management

---

## 🚀 Workflow

### 1. Load Libraries

The notebook starts by importing required geospatial and file-handling libraries.

---

### 2. Define File Paths

Set paths for:

* Input raster folder
* Hungary shapefile
* Output directories

```python
raster_folder = "path/to/raster/data"
shapefile_path = "path/to/hungary_shapefile.shp"
output_folder = "path/to/output/clipped"
```

---

### 3. Load Shapefile

The Hungary boundary is loaded using GeoPandas:

```python
gdf = gpd.read_file(shapefile_path)
```

---

### 4. Discover Raster Files

All `.tif` files are recursively collected:

```python
raster_files = glob.glob(os.path.join(raster_folder, "**", "*.tif"), recursive=True)
```

---

### 5. Clip Rasters to Hungary

For each raster:

* Open file using `rasterio`
* Ensure CRS matches the shapefile
* Clip using `rasterio.mask`
* Save output raster

Key steps:

* CRS alignment (`gdf.to_crs`)
* Geometry masking
* Metadata update

---

### 6. Filter Summer Months 🌞

After clipping, rasters are filtered based on filename date:

* Expected filename format includes `YYYYMMDD`
* Extract month from filename
* Keep only:

  * May (`05`)
  * June (`06`)
  * July (`07`)
  * August (`08`)
  * September (`09`)

Example logic:

```python
date_str = fname.split("_")[3]
month = date_str[4:6]
```

Filtered rasters are saved into:

```
Summer_Rasters/
```

---

## 📊 Outputs

### 1. Clipped Rasters

* Location: `Clipped/`
* Content: All rasters clipped to Hungary

### 2. Summer Rasters

* Location: `Summer_Rasters/`
* Content: Subset of rasters for summer months only

---

## ⚠️ Notes & Assumptions

* Raster filenames must contain a date in `YYYYMMDD` format
* CRS mismatches are automatically handled
* NoData values are preserved during clipping
* Paths in the notebook are currently hardcoded (Windows format)

👉 You should update paths before running on a different system.

---

## 🔧 Potential Improvements

If you want to level this up (recommended):

* Replace hardcoded paths with a config file or arguments
* Add logging instead of print statements
* Validate filename structure before parsing dates
* Parallelize raster processing for large datasets
* Add visualization (e.g., matplotlib)

---

## 📚 Use Case

This workflow is useful for:

* Drought monitoring
* Seasonal environmental analysis
* Preprocessing raster datasets for GIS or machine learning

---

## 👤 Author

Created by Emese Lana Gojdár as part of a GIS thesis workflow focusing on drought analysis in Hungary, 2026.

---


## 🤝 Contributions

Pull requests and suggestions are welcome!
