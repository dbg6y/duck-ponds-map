# Duck Ponds Property Map

Interactive web map showcasing Francis Marion University's newly acquired 8,460-acre Duck Ponds property along the Great Pee Dee River, along with FMU's main campus and Freshwater Ecology Center.

**Live site:** https://dbg6y.github.io/duck-ponds-map/

## Features

- Full-screen Leaflet map with ESRI satellite imagery basemap
- Three property boundaries with distinct colors:
  - Duck Ponds (red)
  - FMU Main Campus (blue)
  - Freshwater Ecology Center (green)
- Left-side information panel with property context
- Responsive design (mobile panel collapses)
- FMU brand colors (navy blue, red, tan)

**Future Enhancements (optional):**
- Replace boundary with authoritative parcel data from OSI or Florence County GIS when available
- Add layer toggle, scale bar, or basemap switcher
- Add FMU branding/logo

## File Structure

```
duck-ponds-map/
├── index.html              # Main page (self-contained HTML/CSS/JS)
├── DuckPondsBoundary.geojson
├── FMUBoundary.geojson
├── FECBoundary.geojson
└── README.md
```

## Technical Notes

### Boundary Data
- Duck Ponds: Traced from OnX Backcountry, exported via QGIS
- FMU Campus & FEC: Exported from QGIS
- Format: GeoJSON (MultiPolygon)
- Coordinate system: WGS84 (EPSG:4326)

### Map Libraries
- Leaflet 1.9.4 (loaded from CDN)
- ESRI World Imagery basemap (free, no API key required)

### Fonts
- Libre Baskerville (headings) - Google Fonts
- Source Sans 3 (body) - Google Fonts

## Property Context

- **Size:** 8,460 acres (2nd largest university-owned forest in SC)
- **Location:** Florence & Darlington Counties, SC
- **River Frontage:** 8 miles along Great Pee Dee River
- **Distance from FMU:** ~15 minutes
- **Purpose:** Field site for new forestry program (launching August 2026)
- **Partners:** Open Space Institute, Florence County, SC Conservation Bank, SC Office of Resilience, Darla Moore Foundation

