# Geospatial Data Formats and CRS in Python

A Jupyter notebook that explores how geospatial data is structured, stored and transformed, using Algeria and Gaza as study areas.

## What it covers

**1. GeoJSON**
- Builds GeoJSON `FeatureCollection` files by hand for Algerian cities (Algiers, Oran, Constantine) and Gaza cities (Gaza City, Khan Yunis, Rafah).
- Saves and reloads them, plots them with Matplotlib, and validates their structure with a custom validator.

**2. Coordinate transformations (PyProj)**
- Converts WGS84 (EPSG:4326) coordinates to UTM 31N (EPSG:32631) for Algeria and UTM 36N (EPSG:32636) for Gaza.
- The Algerian dataset also includes Sidi Bel Abbès coordinates, alongside Tlemcen, Blida, Setif and Batna.
- Computes Euclidean distances in UTM and compares them with geodesic distances (`pyproj.Geod`).
- Shows why UTM distances are unreliable across zones, using Algiers to Gaza City as the example.

**3. Vector data inspection (Fiona)**
- Downloads GADM administrative boundaries for Algeria and Palestine.
- Inspects driver, CRS, bounds, schema and features.
- Converts GeoJSON to GeoPackage and compares file sizes.

**4. Raster metadata (Rasterio)**
- Generates synthetic DEM GeoTIFFs for the Algiers area and the Gaza Strip.
- Reads metadata: dimensions, CRS, bounds, resolution, affine transform and band statistics.
- Visualizes the rasters and their elevation histograms.
- Reads pixel windows and converts between pixel and geographic coordinates.

## Requirements

- Python 3.11 or 3.12 recommended
- `numpy`, `matplotlib`, `pyproj`, `fiona`, `rasterio`, `notebook`

```
conda create -n gis python=3.12
conda activate gis
conda install -c conda-forge fiona rasterio pyproj matplotlib numpy notebook
```

## Usage

```
jupyter notebook lab3_geospatial_formats_crs.ipynb
```

Run the cells in order. Generated files (GeoJSON, GeoPackage, GeoTIFF, PNG figures) are written to a `data/` folder next to the notebook. Downloading the GADM boundaries requires an internet connection.
