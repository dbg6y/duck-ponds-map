# Duck Ponds Property Map

Interactive web map showcasing Francis Marion University's newly acquired 8,460-acre Duck Ponds property along the Great Pee Dee River.

## Project Status

**Working:**
- Full-screen Leaflet map with ESRI satellite imagery basemap
- Left-side information panel with property stats and context
- Responsive design (mobile panel collapses)
- GeoJSON boundary loading via fetch()
- Gold/tan boundary styling visible against satellite imagery

**Needs Fixing:**
- `boundary.geojson` - The main parcel (DuckPonds1) has a tracing error causing diagonal lines across the polygon. The coordinates jump to non-adjacent points somewhere in the sequence. Drew will re-export from OnX Backcountry.

**Future Enhancements (optional):**
- Replace boundary with authoritative parcel data from OSI or Florence County GIS when available
- Add layer toggle, scale bar, or basemap switcher
- Add FMU branding/logo

## File Structure

```
duck-ponds-map/
├── index.html        # Main page (self-contained HTML/CSS/JS)
├── boundary.geojson  # Property boundary (2 features: main + secondary parcel)
└── README.md
```

## Deployment

This will be hosted as a GitHub Pages project site under Drew's existing domain:

1. Create new repository: `duck-ponds-map`
2. Push these files to `main` branch
3. Enable GitHub Pages (Settings → Pages → Source: main branch)
4. Access at: `drewgower.com/duck-ponds-map/`

## Technical Notes

### Boundary Data
- Original source: Drew traced from OnX Backcountry
- Format: KML exported from OnX, converted to GeoJSON
- Two non-contiguous parcels (main parcel ~1800 vertices, secondary ~450 vertices)
- Coordinate system: WGS84 (EPSG:4326)

### KML to GeoJSON Conversion
If you need to re-convert KML files from OnX:

```python
import json
import re

def parse_kml_coordinates(kml_content):
    match = re.search(r'<coordinates>(.*?)</coordinates>', kml_content, re.DOTALL)
    if not match:
        return None
    coord_string = match.group(1).strip()
    coords = []
    for point in coord_string.split():
        parts = point.split(',')
        lon = float(parts[0])
        lat = float(parts[1])
        coords.append([lon, lat])
    return coords

# KML uses lon,lat order (same as GeoJSON), so no transformation needed
# Wrap in GeoJSON Polygon: {"type": "Polygon", "coordinates": [coords]}
```

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

## Original Conversation

Full planning discussion available at:
`/mnt/transcripts/2025-12-18-13-23-25-fmu-forest-website-planning.txt`

Topics covered:
- GIS data acquisition strategies (Florence County REST services, qPublic, Regrid)
- REST API concepts and ArcGIS query syntax
- Web mapping architecture decisions
- GitHub Pages hosting options
