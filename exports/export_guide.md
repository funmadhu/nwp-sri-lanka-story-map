# Export Guide: Publishing Your Story Map

## Overview

This guide provides step-by-step instructions for exporting your QGIS story map in various formats for web, print, and interactive platforms.

---

## Quick Export Options

### Export as Static Image (PNG/JPG)

**Best for**: Social media, presentations, quick sharing

1. In QGIS, go to **Project → Import/Export → Export as Image**
2. Choose location and filename
3. Select format (PNG recommended for quality)
4. Set resolution: 300 DPI for print, 72 DPI for web
5. Click Export

### Export as PDF

**Best for**: Print, documents, official reports

1. Go to **Project → Import/Export → Export as PDF**
2. Set page size (A4, A3, etc.)
3. Choose orientation (portrait or landscape)
4. Click Export
5. Open in PDF viewer to verify

### Export as GeoJSON

**Best for**: Web mapping, data sharing, interoperability

1. Right-click layer → Export → Save Features As
2. Choose format: GeoJSON
3. Enter filename (e.g., "government_offices.geojson")
4. Click OK
5. File saved to `data/` directory

---

## Web Publishing

### Option 1: GitHub Pages + Leaflet Map

**Steps**:

1. Create `web/index.html`:
```html
<!DOCTYPE html>
<html>
<head>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.7.1/leaflet.min.css" />
    <script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.7.1/leaflet.min.js"></script>
    <style>
        #map { height: 600px; }
    </style>
</head>
<body>
    <h1>NWP Government Offices Story Map</h1>
    <div id="map"></div>
    <script src="map.js"></script>
</body>
</html>
```

2. Create `web/map.js`:
```javascript
const map = L.map('map').setView([6.9, 80.5], 9);

L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png').addTo(map);

fetch('government_offices.geojson')
  .then(r => r.json())
  .then(data => L.geoJSON(data).addTo(map));
```

3. Push to GitHub and enable Pages

### Option 2: Mapbox Studio

1. Visit https://studio.mapbox.com
2. Create new project
3. Upload GeoJSON file
4. Style layers
5. Generate embed code
6. Share link or embed in website

### Option 3: ArcGIS Online

1. Sign in to ArcGIS Online
2. Create new Web Map
3. Add layer from GeoJSON file
4. Style and configure map
5. Publish as Story Map
6. Share via link

---

## Print Maps

### Create Print Layout in QGIS

1. **Go to**: Project → New Print Layout
2. **Name**: e.g., "NWP_Government_Offices_Print"
3. **Add map**: Insert → Map (set scale 1:100,000)
4. **Add title**: Insert → Text → "Government Offices - North West Province"
5. **Add legend**: Insert → Legend → Select government offices layer
6. **Add scale bar**: Insert → Scale Bar → Choose style
7. **Add north arrow**: Insert → North Arrow
8. **Add attribution**: Insert → Text → Data sources and credits

### Export for Print

1. **Layout → Export as PDF**
   - Page size: A3 or A4
   - Resolution: 300 DPI
   - Output: Print-ready PDF

2. **Layout → Export as Image**
   - Format: PNG or TIFF
   - Resolution: 300 DPI
   - Compression: Lossless

3. **Send to printer** or save for distribution

---

## Data Export

### Export as Shapefile

1. Right-click layer → Export → Save Features As
2. Format: ESRI Shapefile
3. Filename: government_offices.shp
4. All related files created (.shx, .dbf, .prj)

### Export as CSV

1. Open Attribute Table
2. Select all rows (Ctrl+A)
3. Right-click → Copy
4. Paste into spreadsheet (Excel, Google Sheets)
5. Save as .csv

### Export as KML

1. Right-click layer → Export → Save Features As
2. Format: Google KML
3. Filename: government_offices.kml
4. Import into Google Earth, Google Maps

---

## Interactive Story Maps

### ArcGIS Story Maps

1. Export GeoJSON from QGIS
2. Go to https://storymaps.arcgis.com
3. Create new Story Map
4. Choose template (Cascade, Series, etc.)
5. Add map with government offices layer
6. Write narrative text
7. Add images, captions, links
8. Publish and share

### Mapbox Story Builder

1. Create Mapbox account
2. Upload GeoJSON as source
3. Create map style
4. Use Mapbox Scrollytelling library
5. Add narrative text for each scene
6. Deploy to web server

### Knightlab Timeline + Map

1. Create CSV with dates and locations
2. Use Knightlab tools: https://timeline.knightlab.com
3. Generate interactive timeline
4. Embed map alongside
5. Share URL

---

## Social Media Sharing

### Create Map Preview Image

1. Export as PNG (300 DPI)
2. Size: 1200 x 630 pixels (Facebook/Twitter optimal)
3. Add title and key information as text overlay
4. Upload to social platform
5. Include caption and link to full map

### Sharing Checklist
- [ ] High-quality image exported
- [ ] Descriptive title included
- [ ] Attribution to data sources
- [ ] Link to full interactive map
- [ ] Relevant hashtags (#NWP #SriLanka #GIS)

---

## Performance Optimization

### Optimize GeoJSON

```bash
# Reduce file size
mapshaper government_offices.geojson -simplify 50% -o government_offices_simplified.geojson
```

### Create Vector Tiles

For large datasets, convert to vector tiles:
1. Use Tippecanoe: https://github.com/mapbox/tippecanoe
2. Create .mbtiles file
3. Serve via Maptiler or Mapbox

### Cache Satellite Imagery

For web maps:
1. Use XYZ tile services (cached by default)
2. Or: Create local tile cache
3. Reduces load times significantly

---

## Accessibility

### Make Maps Accessible

- [ ] Provide text alternative describing map
- [ ] Use colorblind-friendly palettes
- [ ] Include legend explaining symbols
- [ ] Add alt text to map images
- [ ] Provide data table as fallback
- [ ] Ensure keyboard navigation works

---

## Version Control

### Track Changes

```bash
git add exports/
git commit -m "Export high-resolution map for publication"
git push origin main
```

### Archive Old Versions

```
exports/
├── web/
│   └── government_offices_v1.2.geojson
├── print/
│   └── NWP_Government_Offices_2026_06_12.pdf
└── archive/
    └── government_offices_v1.1.geojson
```

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| GeoJSON file too large | Simplify geometries, reduce precision |
| Map not loading on web | Check file paths, CORS settings, coordinate system |
| Colors not displaying | Verify color codes in GeoJSON or QGIS symbology |
| Performance slow | Reduce detail, use tiles, cache data |
| Missing data on export | Verify layer is visible and selected |

---

## Next Steps

1. Choose export format for your audience
2. Follow steps above for your chosen platform
3. Test on desktop and mobile
4. Share feedback link
5. Update map as new offices are added

---

For more help, see QGIS export documentation or contact the project maintainer.
