# Data Directory

## Government Offices Shapefile (MC_UC_PS_N)

### Files Included
- `MC_UC_PS_N.shp` — Main shapefile (geometry)
- `MC_UC_PS_N.shx` — Shape index file
- `MC_UC_PS_N.dbf` — Attribute database
- `MC_UC_PS_N.prj` — Projection file (WGS84)
- `MC_UC_PS_N.cpg` — Code page file (UTF-8)

### Coordinate System
**WGS84 (EPSG:4326)** — Latitude/Longitude

### Data Contents
- **33 Government Office Locations** across North West Province, Sri Lanka
- Point geometries with attributes
- Office names and types
- Geographic coordinates

### Data Sources

#### Government Offices
- Source: [Specify your data source - e.g., Sri Lanka Survey Department, OpenStreetMap, Municipal Records]
- Collection Date: [Year]
- Last Updated: June 2026

#### Administrative Boundaries
- Available from: OpenStreetMap, Sri Lanka Survey Department
- Format: GeoJSON or Shapefile

#### Satellite Imagery
- **USGS Earth Explorer**: https://earthexplorer.usgs.gov/
  - Landsat 8/9
  - Sentinel-2
  - ASTER

- **ESA Copernicus**: https://scihub.copernicus.eu/
  - Sentinel-1 (SAR)
  - Sentinel-2 (Optical)

- **Google Earth Engine**: https://earthengine.google.com/
  - MODIS, Landsat, Sentinel imagery

- **Bing Maps**: https://www.bing.com/maps
  - Web tile service

### Data Quality
- Accuracy: ±[X meters]
- Completeness: [X%]
- Validation Status: [Validated/Pending]

### Usage Rights
[Specify licensing and usage terms]

### GeoJSON Conversion
Shapefile has been converted to GeoJSON format for web compatibility.
File: `government_offices.geojson`

### Updating Data
To add or update office locations:
1. Edit the shapefile using QGIS or ArcGIS
2. Update the GeoJSON export
3. Update layer in QGIS project
4. Commit changes to repository

---

For questions about data, please contact the project maintainer.
