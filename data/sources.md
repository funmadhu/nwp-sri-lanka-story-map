# Data Sources

## Government Offices Data

### Primary Source
- **Source**: [Your data source - e.g., Sri Lanka Survey Department, Municipal Records, OpenStreetMap]
- **Collection Date**: [Year collected]
- **Last Updated**: June 2026
- **Accuracy**: ±[X meters]
- **Completeness**: [X% of offices covered]

### Data Format
- **Original Format**: Shapefile (MC_UC_PS_N.shp)
- **Alternative Formats**: GeoJSON (government_offices.geojson)
- **Coordinate System**: WGS84 (EPSG:4326)
- **Number of Records**: 33 government offices

### Data Fields
- Office Name
- Office Type (Pradeshiya Sabha, Municipal, District Secretariat)
- Location (Latitude/Longitude)
- District
- Contact Information (optional)
- Jurisdiction Area

---

## Administrative Boundaries

### District Boundaries
- **Source**: OpenStreetMap / Sri Lanka Survey Department
- **Format**: GeoJSON or Shapefile
- **Coverage**: Kurunegala & Puttalam districts
- **Update Frequency**: Annual

### Pradeshiya Sabha Divisions
- **Source**: Sri Lanka Ministry of Local Government
- **Format**: GeoJSON or Shapefile
- **Completeness**: [X% coverage]
- **Validation**: Verified as of [Date]

---

## Satellite Imagery

### USGS Earth Explorer
**URL**: https://earthexplorer.usgs.gov/

**Available Data**:
- Landsat 8 & 9 (30m resolution)
- Sentinel-2 MSI (10-60m resolution)
- ASTER (15-90m resolution)
- MODIS (250-1000m resolution)

**Access**: Free, registration required

**Coverage**: North West Province available

**Steps to Download**:
1. Go to USGS Earth Explorer
2. Search: "6.9, 80.5" (NWP center)
3. Select date range
4. Choose dataset (Landsat recommended)
5. Download GeoTIFF files
6. Import into QGIS

### ESA Copernicus
**URL**: https://scihub.copernicus.eu/

**Available Data**:
- Sentinel-1 SAR (10m resolution)
- Sentinel-2 Optical (10m resolution)
- Sentinel-3 Thermal

**Access**: Free, registration required

**Coverage**: Global, including NWP

**Steps to Download**:
1. Register for Copernicus account
2. Search area: NWP bounds
3. Filter by cloud coverage (<10%)
4. Download Level-1C products
5. Process in QGIS or SNAP

### Google Earth Engine
**URL**: https://earthengine.google.com/

**Available Data**:
- Landsat archive
- Sentinel imagery
- MODIS, ASTER
- Analysis-ready imagery

**Access**: Free, Python/JavaScript API

**Advantage**: Cloud processing, no download needed

**Code Example**:
```python
import ee

ee.Initialize()

nwp = ee.Geometry.Rectangle([79.5, 6.0, 81.5, 7.5])
image = ee.ImageCollection('LANDSAT/LC08/C01/T1_SR')\
    .filterBounds(nwp)\
    .filterDate('2020-01-01', '2020-12-31')\
    .median()

Map.addLayer(image, {'bands': ['B4', 'B3', 'B2'], 'max': 3000})
Map.centerObject(nwp, 9)
```

### Bing Maps
**URL**: https://www.bing.com/maps

**Data**: Satellite and aerial imagery

**Access**: Web-based tile layer

**QGIS Integration**: 
```
URL: http://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}
```

---

## Topographic Data

### SRTM Digital Elevation Model (DEM)
**Source**: USGS SRTM 90m DEM
**Resolution**: 90 meters
**Download**: https://earthexplorer.usgs.gov/
**Use**: Terrain visualization, accessibility analysis

---

## OpenStreetMap Data

### Roads Network
**URL**: https://www.openstreetmap.org/
**Format**: Shapefile, GeoJSON, OSM XML
**Coverage**: Complete for NWP
**Download Tools**: Overpass API, QGIS QuickOSM plugin

### Buildings & POIs
**URL**: https://www.openstreetmap.org/
**Coverage**: Partial for NWP (more urban areas)
**Extract**: Using OSM Overpass API

---

## Census & Population Data

### Sri Lanka Census of Population and Housing
**Source**: Department of Census and Statistics
**Data**: Population by administrative division
**Resolution**: Pradeshiya Sabha level
**Year**: Latest census (2012)
**Access**: Open Government License
**URL**: https://www.statistics.gov.lk/

---

## Licenses & Attribution

### Data Attribution Format
"Government Offices Layer: [Your source], Satellite Imagery: [USGS/ESA/Google/Bing], Administrative Boundaries: OpenStreetMap/Sri Lanka Survey Department"

### Required Attribution
- [ ] OpenStreetMap: "© OpenStreetMap contributors"
- [ ] USGS Landsat: "USGS Landsat"
- [ ] Sentinel: "Contains Copernicus Sentinel data"
- [ ] Bing: "© Microsoft"

---

## Data Updates & Maintenance

### Update Schedule
- Government offices: Annual or as needed
- Satellite imagery: As acquired (weekly for Sentinel-2)
- Administrative boundaries: As changed by government
- Roads: Weekly (OpenStreetMap community-maintained)

### Version Control
```
data/
├── MC_UC_PS_N_2026_06.shp    # Latest version
├── MC_UC_PS_N_2026_05.shp    # Previous version (archive)
└── sources.md                 # This file
```

---

## How to Update Data

### Add New Satellite Imagery Layer
1. Download from one of sources above
2. Import into QGIS: Layer → Add → Raster Layer
3. Drag to appropriate position in layer stack
4. Adjust transparency as needed

### Update Government Offices
1. Edit shapefile or GeoJSON
2. Add/remove features as needed
3. Update metadata (date, source)
4. Commit to Git

### Update Boundaries
1. Get latest administrative boundaries
2. Replace existing layer
3. Verify geometry accuracy
4. Update styling if necessary

---

## Recommended Readings

- USGS Earth Explorer User Guide: https://lta.cr.usgs.gov/EarthExplorer/
- Copernicus Open Access Hub Guide: https://scihub.copernicus.eu/twiki/
- OpenStreetMap Wiki: https://wiki.openstreetmap.org/
- Google Earth Engine Documentation: https://developers.google.com/earth-engine

---

For more information about specific data sources, see project README or contact maintainer.
