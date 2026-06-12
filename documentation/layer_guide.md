# Layer Guide: NWP Government Offices Story Map

## Overview

This guide describes each layer in the QGIS project and how to interact with them.

## Layer Structure

### 1. Satellite Imagery (Base Layer)

**Purpose**: Geographic context and reference

**Data Source**: 
- Google Satellite, Bing Maps, USGS Landsat, or ESA Sentinel imagery
- See `data/sources.md` for access details

**Properties**:
- Format: XYZ Tile Layer or GeoTIFF raster
- Resolution: Variable (typically 10-30m per pixel)
- CRS: WGS84 (EPSG:4326)
- Opacity: 100% (adjustable)

**Interactions**:
- Right-click layer → Properties → Transparency to adjust opacity
- Enable/disable by clicking eye icon
- Satellite imagery provides visual context for office locations

**Tips**:
- Use high-resolution imagery (Sentinel-2, Landsat 8/9) for detail
- Adjust transparency to show layers beneath
- Consider temporal imagery to show change over time

---

### 2. Administrative Boundaries

**Purpose**: Show jurisdictional areas and administrative divisions

**File**: `admin_boundaries.geojson` or shapefile

**Feature Types**:
- **District Boundaries**: Kurunegala & Puttalam districts
- **Pradeshiya Sabha Divisions**: Village council boundaries
- **Municipal Council Areas**: City/town boundaries

**Properties**:
- Geometry Type: Polygons
- CRS: WGS84 (EPSG:4326)
- Styling: Boundary lines with fill color

**Attributes**:
| Field | Description | Example |
|-------|-------------|---------|
| name | Boundary name | "Kurunegala District" |
| type | Administrative level | "District", "Pradeshiya Sabha", "Municipal" |
| population | Population count | 1234567 |
| area_sqkm | Area in square kilometers | 4726.2 |

**Interactions**:
- Click feature to identify in map
- Open Attribute Table to view all boundaries
- Filter by type to show only specific administrative levels

**Tips**:
- Use different colors for different administrative levels
- Add labels for boundary names
- Adjust opacity to see underlying satellite imagery

---

### 3. Government Offices Layer (Main Layer)

**Purpose**: Display 33 government office locations across NWP

**File**: `MC_UC_PS_N.shp` (Shapefile) or `government_offices.geojson`

**Feature Type**: Point features (33 offices)

**Geometry**:
- Coordinates in WGS84 (Latitude/Longitude)
- Accuracy: ±X meters
- Collection Date: [Year]

**Attributes**:
| Field | Description | Example |
|-------|-------------|---------|
| name | Office name | "Kurunegala Pradeshiya Sabha" |
| type | Office type | "Pradeshiya Sabha", "Municipal", "District Secretariat" |
| latitude | Y-coordinate | 6.9271 |
| longitude | X-coordinate | 80.7789 |
| district | District name | "Kurunegala" |
| telephone | Contact number | "+94 37 222 2222" |
| email | Email address | "kurunegala.ps@gov.lk" |
| address | Physical address | "Main Street, Kurunegala" |
| established | Year established | 1980 |

**Styling**:
- **Symbology**: Different symbols for different office types
  - Pradeshiya Sabha: Blue circle
  - Municipal: Red square
  - District Secretariat: Green triangle
- **Size**: Medium (adjustable)
- **Label**: Office name (optional)

**Interactions**:
- Click office to view attributes in Identify Results
- Right-click → Properties → Symbology to change symbol style
- Open Attribute Table to view all 33 offices

**Filtering**:

**Show only Pradeshiya Sabha offices**:
1. Right-click layer → Filter
2. Enter: `"type" = 'Pradeshiya Sabha'`
3. Click OK

**Show offices in Kurunegala district**:
1. Right-click layer → Filter
2. Enter: `"district" = 'Kurunegala'`
3. Click OK

**Tips**:
- Use different colors for office types to quickly identify
- Add layer labels for office names
- Use graduated symbols for additional attribute display
- Create separate layers for each office type if needed

---

### 4. Optional Layers

#### Roads Network
**Purpose**: Show connectivity and accessibility
- Source: OpenStreetMap
- Type: Line features
- Styling: Different colors for road types

#### Population Density
**Purpose**: Show demographic context
- Source: Raster data (WorldPop, GeoDataset)
- Type: Raster layer
- Styling: Heat map colors

#### Accessibility Analysis
**Purpose**: Show travel time/distance to offices
- Source: Network analysis from roads
- Type: Raster or polygon features
- Styling: Concentric rings or color gradient

---

## Layer Management

### Visibility Control
- Click eye icon to toggle layer visibility
- Shift+Click to hide all other layers
- Ctrl+Click to show only that layer

### Layer Order
- Drag layers to reorder in Layers panel
- **Best Practice Order**:
  1. Satellite Imagery (bottom)
  2. Administrative Boundaries
  3. Government Offices (top)

### Opacity/Transparency
1. Right-click layer → Properties
2. Go to Transparency tab
3. Adjust opacity slider (0-100%)

### Layer Symbology
1. Right-click layer → Properties
2. Go to Symbology tab
3. Choose symbol type:
   - **Single Symbol**: All features same style
   - **Categorized**: Different colors by attribute
   - **Graduated**: Size/color based on numeric value
   - **Rule-based**: Custom rules for styling

---

## Layer Interactions

### Identify Tool
1. Select Identify Features tool (keyboard: i)
2. Click on any feature
3. View attributes in Identify Results panel

### Attribute Table
1. Right-click layer → Open Attribute Table
2. View all features and attributes
3. Edit cells directly
4. Sort or filter using controls

### Spatial Query
1. Use Select by Rectangle tool
2. Draw box around features to select
3. Selected features highlight in yellow
4. View selection count in status bar

### Measurement
1. Select Measure tool (Toolbar or keyboard: m)
2. Click to create line or polygon
3. Distance/area displays in status bar

---

## Styling Examples

### Example 1: Color by Office Type

```
Right-click layer → Properties → Symbology
Select "Categorized"
Column: "type"
Classify: Click "Classify"
Result: Each office type gets different color
```

### Example 2: Size by Population Served

```
Right-click layer → Properties → Symbology
Select "Graduated"
Column: "population_served"
Method: "Natural Breaks (Jenks)"
Size range: 5-15 mm
Result: Larger symbols = more people served
```

### Example 3: Show Labels

```
Right-click layer → Properties → Labels
Enable Labels: Check
Label field: "name"
Font: Arial, 10pt
Placement: Above point
```

---

## Performance Tips

- Disable satellite imagery when zoomed in
- Simplify boundaries at large scales
- Use filters to show only relevant offices
- Reduce number of layers active at once
- Use pre-built rasters instead of on-the-fly rendering

---

For more information, see the main README and QGIS documentation.
