# 🗺️ NWP Sri Lanka Government Offices Story Map

A QGIS-based geographic story map visualizing local government offices across the North West Province (Kurunegala & Puttalam districts), Sri Lanka, with satellite imagery backdrop.

## 📍 Project Overview

This story map tells the story of local government infrastructure in Sri Lanka's North West Province through:
- **Interactive QGIS maps** with satellite imagery
- **33 Government office locations** (Pradeshiya Sabha, Municipal councils, District offices)
- **Administrative boundaries** and jurisdictions
- **Exportable visualizations** for web and print

## 📁 Project Structure

```
nwp-sri-lanka-story-map/
├── README.md                          # Project overview
├── qgis/
│   ├── nwp_story_map.qgz            # Main QGIS project file
│   ├── nwp_story_map.qmd            # QGIS metadata
│   └── layer_styles/                 # QGIS layer style files (.qml)
├── data/
│   ├── MC_UC_PS_N.shp               # Government offices shapefile
│   ├── MC_UC_PS_N.shx               # Shapefile index
│   ├── MC_UC_PS_N.dbf               # Shapefile attributes
│   ├── MC_UC_PS_N.prj               # Projection info (WGS84)
│   ├── MC_UC_PS_N.cpg               # Code page (UTF-8)
│   ├── government_offices.geojson   # GeoJSON version of shapefile
│   ├── admin_boundaries.geojson     # District & local authority boundaries
│   ├── sources.md                   # Data source documentation
│   └── README.md                    # Data guide
├── exports/
│   ├── export_guide.md              # Instructions for exporting maps
│   └── web/                         # Web-ready exports
└── documentation/
    ├── story_structure.md           # Narrative flow & story beats
    ├── layer_guide.md               # Layer descriptions & usage
    ├── setup_guide.md               # How to set up this project
    └── data_schema.md               # Data structure & fields
```

## 🗺️ Data Layers

### Government Offices Layer (33 locations)
- **Type**: Point features
- **Includes**:
  - Office name & type
  - Location (WGS84 coordinates: latitude/longitude)
  - Jurisdiction coverage
  - Contact information (if available)

### Administrative Boundaries
- **District boundaries** (Kurunegala, Puttalam)
- **Pradeshiya Sabha divisions**
- **Municipal council areas**

### Satellite Imagery
- Base layer from public sources (USGS, ESA, Google Earth Engine)
- High-resolution satellite imagery for geographic context

## 🚀 Quick Start

### Prerequisites
- QGIS 3.16+ (latest stable version recommended)
- Git for version control

### Setup
1. Clone this repository:
   ```bash
   git clone https://github.com/funmadhu/nwp-sri-lanka-story-map.git
   cd nwp-sri-lanka-story-map
   ```

2. Open `qgis/nwp_story_map.qgz` in QGIS

3. Ensure all data files are in the `data/` directory

4. Check `documentation/setup_guide.md` for detailed instructions

## 📖 Story Narrative

The story map follows this journey:

1. **Introduction**: Geographic overview of NWP (North West Province)
2. **Government Infrastructure**: Location and distribution of 33 government offices
3. **Office Types**: Categorization (Pradeshiya Sabha, Municipal, District Secretariat)
4. **Service Coverage**: Jurisdictional areas served by each office
5. **Accessibility**: Distance and connectivity analysis
6. **Conclusion**: Summary of government office network in NWP

See `documentation/story_structure.md` for detailed narrative beats.

## 🛰️ Satellite Imagery Integration

Satellite imagery layers available in the QGIS project:
- **USGS Earth Explorer**: Free Landsat & Sentinel data
- **ESA Copernicus**: Sentinel satellite imagery
- **Google Earth Engine**: High-resolution imagery
- **Bing Maps**: Web-based satellite tiles

Access instructions in `data/sources.md`

## 💾 Exporting the Story Map

Export for:
- **Web publication**: Interactive maps, GeoJSON exports
- **Print**: High-resolution PDFs, Maps
- **Story Map platforms**: ArcGIS Story Maps, Mapbox Studio

See `exports/export_guide.md` for step-by-step instructions.

## 📝 Adding/Updating Government Offices

To add new offices:
1. Edit `data/MC_UC_PS_N.shp` (or convert to `government_offices.geojson`)
2. Add point feature with required fields
3. Reload layer in QGIS
4. Save project

See `documentation/data_schema.md` for field requirements.

## 🔗 Coordinate System

**Projection**: WGS84 (EPSG:4326)
- Latitude/Longitude format
- Ideal for web mapping and global datasets

## 📄 License

[Specify your license - e.g., CC-BY-4.0, MIT, Open Government License]

## 👤 Project Lead

- **funmadhu** — Project Creator & Maintainer

## 📧 Support

For questions, contributions, or data updates, please open an issue on GitHub.

---

**Last Updated**: June 2026
**QGIS Version**: 3.16+
**Data Format**: Shapefile (SHP) + GeoJSON
**Coordinate System**: WGS84 (EPSG:4326)
**Number of Offices**: 33
**Coverage**: North West Province, Sri Lanka