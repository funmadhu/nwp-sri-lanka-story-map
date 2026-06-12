# Data Schema: Government Offices Layer

## Field Definitions

### Government Offices (MC_UC_PS_N)

This document describes the attribute schema for the government offices layer.

#### Core Geometry

| Field | Type | Required | Description | Example |
|-------|------|----------|-------------|---------|
| geometry | Point | Yes | Geographic location (WGS84) | POINT(80.7789 6.9271) |
| latitude | Float | Yes | Y-coordinate (WGS84) | 6.9271 |
| longitude | Float | Yes | X-coordinate (WGS84) | 80.7789 |

#### Office Information

| Field | Type | Required | Description | Example |
|-------|------|----------|-------------|---------|
| name | String | Yes | Official office name | "Kurunegala Pradeshiya Sabha" |
| office_type | String | Yes | Type of office | "Pradeshiya Sabha", "Municipal", "District Secretariat" |
| district | String | Yes | District name | "Kurunegala" or "Puttalam" |
| jurisdiction | String | No | Jurisdiction area served | "Kurunegala Division" |

#### Contact Information

| Field | Type | Required | Description | Example |
|-------|------|----------|-------------|---------|
| telephone | String | No | Primary phone number | "+94 37 222 2222" |
| email | String | No | Email address | "kurunegala.ps@gov.lk" |
| address | String | No | Physical street address | "Main Street, Kurunegala" |
| postal_code | String | No | Postal code | "60000" |
| website | String | No | Office website | "https://example.gov.lk" |

#### Administrative

| Field | Type | Required | Description | Example |
|-------|------|----------|-------------|---------|
| established | Integer | No | Year office was established | 1980 |
| staff_count | Integer | No | Number of staff members | 45 |
| budget_allocation | Float | No | Annual budget (in LKR) | 5000000 |
| notes | String | No | Additional notes or comments | "Recently renovated office building" |

#### Demographic

| Field | Type | Required | Description | Example |
|-------|------|----------|-------------|---------|
| population_served | Integer | No | Population served by this office | 125000 |
| area_sqkm | Float | No | Area served in square kilometers | 150.5 |
| urban_rural | String | No | Classification | "Urban", "Rural", "Semi-Urban" |

#### Data Quality

| Field | Type | Required | Description | Example |
|-------|------|----------|-------------|---------|
| data_source | String | No | Where data came from | "Sri Lanka Survey Department" |
| last_verified | Date | No | Date information was last verified | "2026-06-01" |
| data_quality | String | No | Confidence level | "High", "Medium", "Low" |
| unique_id | String | Yes | Unique identifier for record | "GOV_001" |

---

## Data Types

- **String**: Text (max 255 characters)
- **Integer**: Whole numbers
- **Float**: Decimal numbers
- **Date**: YYYY-MM-DD format
- **Point**: Geographic coordinate (WGS84)

---

## Validation Rules

### Mandatory Fields
- `name`: Must not be empty
- `office_type`: Must be one of: "Pradeshiya Sabha", "Municipal", "District Secretariat"
- `district`: Must be "Kurunegala" or "Puttalam"
- `geometry`: Valid WGS84 point within NWP bounds
- `unique_id`: Must be unique and follow format GOV_XXX

### Coordinate Validation
- Latitude range: 6.0 to 7.5 (North West Province)
- Longitude range: 79.5 to 81.5 (North West Province)
- Both coordinates required

### Data Format Validation
- Phone numbers: +94 format or local format
- Email: Valid email format
- Dates: YYYY-MM-DD format
- Postal codes: 5-digit numeric

---

## Example Record

```json
{
  "type": "Feature",
  "geometry": {
    "type": "Point",
    "coordinates": [80.7789, 6.9271]
  },
  "properties": {
    "unique_id": "GOV_001",
    "name": "Kurunegala Pradeshiya Sabha",
    "office_type": "Pradeshiya Sabha",
    "district": "Kurunegala",
    "jurisdiction": "Kurunegala Division",
    "latitude": 6.9271,
    "longitude": 80.7789,
    "telephone": "+94 37 222 2222",
    "email": "kurunegala.ps@gov.lk",
    "address": "Main Street, Kurunegala",
    "postal_code": "60000",
    "website": "https://kurunegala.gov.lk",
    "established": 1980,
    "staff_count": 45,
    "budget_allocation": 5000000,
    "population_served": 125000,
    "area_sqkm": 150.5,
    "urban_rural": "Urban",
    "data_source": "Sri Lanka Survey Department",
    "last_verified": "2026-06-01",
    "data_quality": "High",
    "notes": "Recently renovated office building"
  }
}
```

---

## Adding New Records

### In GeoJSON Format
1. Add new feature object to `government_offices.geojson`
2. Include all mandatory fields
3. Validate coordinates are within NWP bounds
4. Assign unique ID (GOV_XXX)
5. Set data_quality and last_verified

### In QGIS
1. Open layer in edit mode (Ctrl+E)
2. Use Digitize Features tool
3. Click map to create new point
4. Fill in attributes in popup form
5. Save edits
6. Export to GeoJSON

### In Shapefile Editor
1. Open shapefile in QGIS or ArcGIS
2. Add new feature
3. Enter attributes in DBF file
4. Save changes
5. Reload in QGIS project

---

## Updating Existing Records

1. Identify record by `unique_id`
2. Update relevant fields
3. Update `last_verified` date to current date
4. Verify all mandatory fields are still populated
5. Save changes
6. Commit to Git repository

---

## Data Quality Indicators

- **High**: All mandatory and most optional fields populated, recent verification
- **Medium**: All mandatory fields, some optional fields missing
- **Low**: Only minimal fields populated, needs verification

---

## Coordinate System

**Projection**: WGS84 (EPSG:4326)
**Datum**: World Geodetic System 1984
**Format**: Decimal degrees (Lat, Long)

---

## Related Schemas

See also:
- `admin_boundaries.geojson` — Administrative division schema
- `sources.md` — Data source documentation

---

For questions about schema or data, contact the project maintainer.
