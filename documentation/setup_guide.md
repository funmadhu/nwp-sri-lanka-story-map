# Setup Guide: NWP Sri Lanka Government Offices Story Map

## Prerequisites

### Software Requirements
- **QGIS 3.16 or later** (download from https://qgis.org/)
- **Git** (for version control)
- **Text Editor** (for editing GeoJSON or markdown files)

### System Requirements
- 2GB+ RAM
- 500MB+ disk space
- Internet connection (for satellite imagery layers)

## Installation Steps

### 1. Clone the Repository

```bash
git clone https://github.com/funmadhu/nwp-sri-lanka-story-map.git
cd nwp-sri-lanka-story-map
```

### 2. Install QGIS

If not already installed:
- Visit https://qgis.org/download/
- Download version 3.16 or later
- Follow installation instructions for your OS

### 3. Open the QGIS Project

1. Launch QGIS
2. Go to **File → Open Project**
3. Navigate to `qgis/nwp_story_map.qgz`
4. Click **Open**

### 4. Verify Data Layers

Once project opens, verify these layers appear in the Layers panel:

- [ ] **Satellite Imagery** (base layer)
- [ ] **Administrative Boundaries** (districts, councils)
- [ ] **Government Offices** (33 point features)

### 5. Connect to Satellite Imagery

#### Option A: Add Web Tile Services (Recommended)

1. In QGIS, go to **Layer → Add Layer → Add XYZ Tile Layer**
2. Add popular satellite sources:

**Google Satellite**
```
https://mt1.google.com/vt/lyrs=s&x={x}&y={y}&z={z}
```

**Bing Satellite**
```
http://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}
```

#### Option B: Use USGS Earth Explorer

1. Visit https://earthexplorer.usgs.gov/
2. Search for area: North West Province, Sri Lanka
3. Download Landsat or Sentinel data
4. Import GeoTIFF into QGIS project

### 6. Configure Layer Styles

1. Right-click each layer in Layers panel
2. Select **Properties → Symbology**
3. Apply pre-built styles from `qgis/layer_styles/`
4. Adjust colors and transparency as needed

## Project Navigation

### Main Map Canvas
- **Pan**: Hold spacebar + drag, or use arrow keys
- **Zoom**: Scroll wheel, or + / - keys
- **Zoom to Layer**: Right-click layer → Zoom to Layer

### Layers Panel
- Toggle layer visibility: Click eye icon
- Reorder layers: Drag to reorder
- Access properties: Right-click → Properties

### Identify Features
1. Select **Identify Features Tool** (keyboard: i)
2. Click on a government office
3. View attributes in Identify Results panel

## Adding Your Data

### Add Government Offices Shapefile

1. Go to **Layer → Add Layer → Add Vector Layer**
2. Select `data/MC_UC_PS_N.shp`
3. Click **Add**
4. Layer appears in Layers panel

### Add Administrative Boundaries

1. Go to **Layer → Add Layer → Add Vector Layer**
2. Select GeoJSON file (e.g., `admin_boundaries.geojson`)
3. Click **Add**

## Working with Attributes

### View Attribute Table
1. Right-click layer → **Open Attribute Table**
2. View all 33 government offices and their properties
3. Edit cells directly or add new records

### Filter by Office Type
1. Open Attribute Table
2. Click **Advanced Filter** button
3. Enter query: `"office_type" = 'Pradeshiya Sabha'`
4. Click **Apply**

## Creating Map Layouts (Composer)

### Add Map Composer
1. Go to **Project → New Print Layout**
2. Name it (e.g., "NWP Government Offices Map")
3. Add elements:
   - **Map**: Insert → Map
   - **Title**: Insert → Text
   - **Legend**: Insert → Legend
   - **Scale Bar**: Insert → Scale Bar
   - **North Arrow**: Insert → North Arrow

### Export Map
1. In Print Layout, go to **Layout → Export as**
2. Choose format: PDF, PNG, or SVG
3. Set resolution (300 DPI for print)
4. Click **Export**

## Saving Your Work

### Save Project
```bash
File → Save  (or Ctrl+S)
```

### Commit Changes to Git
```bash
git add .
git commit -m "Updated government offices layer with new data"
git push origin main
```

## Troubleshooting

### Layers Not Appearing
- Check **View → Zoom to Full Extent**
- Verify layer is checked (eye icon visible)
- Check CRS matches (should be EPSG:4326)

### Satellite Imagery Not Loading
- Check internet connection
- Verify XYZ tile URL is correct
- Try alternative tile service

### Data Files Missing
- Ensure all files in `data/` directory are present
- Check file paths in layer properties
- Re-add layer if needed

### Performance Issues
- Reduce zoom level on satellite imagery
- Disable layers not in use
- Simplify vector features if needed

## Next Steps

1. ✅ Review `layer_guide.md` for detailed layer information
2. ✅ Check `story_structure.md` for narrative framework
3. ✅ See `export_guide.md` for publishing options
4. ✅ Update data as new offices are added

---

For support, visit the GitHub repository issues page or contact the project maintainer.
