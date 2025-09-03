# Autopilot - Interactive Web Map Viewer

Autopilot is a minimal static web application that provides an interactive map interface using MapLibre GL JS, PMTiles, and Protomaps basemap styling. The entire application is contained in a single HTML file with no build process or dependencies.

Always reference these instructions first and fallback to search or bash commands only when you encounter unexpected information that does not match the info here.

## Working Effectively

### Repository Structure
```
autopilot/
├── docs/
│   └── index.html          # Complete map application (453KB)
├── README.md               # Project documentation  
└── LICENSE                 # CC0 1.0 Universal license
```

### Development Setup
- **No installation required** - Application runs directly in any modern web browser
- **No build process** - Single HTML file with inline CSS and JavaScript
- **No dependencies to install** - All libraries loaded from CDN
- **No tests** - No testing infrastructure exists

### Running the Application Locally
```bash
# Navigate to the docs directory
cd docs

# Start a local web server (choose one):
python3 -m http.server 8000
# OR
python -m http.server 8000  
# OR
npx serve .
# OR  
php -S localhost:8000

# Open browser to: http://localhost:8000
```

**Server startup time**: Instant (< 1 second)  
**Application load time**: 2-5 seconds (depends on CDN response)

### Technologies Used
- **MapLibre GL JS v5.6.1** - Open-source map rendering library
- **PMTiles v3.0.7** - Cloud-optimized map tile format  
- **Protomaps** - Open-source basemap data and styling
- **External Dependencies** (all loaded from CDN):
  - `https://unpkg.com/maplibre-gl@5.6.1/dist/maplibre-gl.js`
  - `https://unpkg.com/maplibre-gl@5.6.1/dist/maplibre-gl.css`
  - `https://unpkg.com/pmtiles@3.0.7/dist/pmtiles.js`

## Validation

### Manual Testing Requirements
**ALWAYS** test the following functionality after making any changes:

1. **Map Loading**: Verify the map displays with gray background and loads tile data
2. **Pan Controls**: Click and drag to move around the map
3. **Zoom Controls**: 
   - Use mouse wheel to zoom in/out
   - Click zoom buttons in navigation control
   - Use pinch gestures on mobile
4. **Rotation**: Right-click and drag to rotate the map
5. **Navigation Control**: Verify zoom +/- buttons and compass work
6. **Globe Control**: Click globe button to switch to 3D globe view
7. **URL Hash**: Verify map state (center, zoom, rotation) persists in browser URL
8. **Responsive Design**: Test on different viewport sizes

### Testing Commands
```bash
# Start local server for testing
cd docs && python3 -m http.server 8000

# Test server responds correctly
curl -I http://localhost:8000/
# Should return: HTTP/1.0 200 OK

# Validate HTML structure
curl -s http://localhost:8000/ | head -20
# Should show proper DOCTYPE and HTML structure
```

### Expected Behavior
- **Initial map view**: Displays world map with Protomaps light theme
- **Map style**: Comprehensive basemap with roads, water, buildings, labels
- **Performance**: Smooth interactions, fast tile loading via PMTiles
- **URL sharing**: Map state automatically saved to browser URL hash

### Known Limitations
- **CDN Dependencies**: Application requires internet access to load external libraries
- **No offline support**: Map tiles and fonts are fetched from remote servers
- **Browser compatibility**: Requires modern browser with WebGL support
- **No error handling**: Application may fail silently if CDN resources are blocked

## Development Workflows

### Making Changes
1. **Edit the single file**: `docs/index.html` contains everything
2. **Test locally**: Start web server and verify functionality
3. **Validate map features**: Test all interactive map controls work
4. **Check browser console**: Ensure no JavaScript errors
5. **Test URL hash persistence**: Verify map state saves to URL

### Code Structure in index.html
- **Lines 1-15**: HTML head with external dependencies
- **Lines 16-18**: CSS styling (minimal - just full viewport map)
- **Lines 19-11940**: Massive MapLibre style definition (roads, water, labels, etc.)
- **Lines 11941-11942**: Application initialization with controls

### Deployment
- **GitHub Pages**: Automatically deploys from `docs/` directory
- **Live URL**: https://hfu.github.io/autopilot/
- **Deployment time**: Instant on push to main branch
- **No build step required**: Static files are served directly

### Common Development Tasks

#### Updating Map Style
```javascript
// Find the style object around line 17
const style = {
    "version": 8,
    "sources": { ... },
    "layers": [ ... ]
}
```

#### Adding Map Controls  
```javascript
// Find map initialization around line 11935
map.addControl(new maplibregl.NavigationControl());
map.addControl(new maplibregl.GlobeControl());
// Add new controls here
```

#### Changing Initial Map View
```javascript
// Modify Map constructor around line 11935
const map = new maplibregl.Map({
  container: 'map', 
  hash: true, 
  style: style,
  center: [lng, lat], // Add initial center
  zoom: 10 // Add initial zoom
});
```

### Performance Notes
- **File size**: 453KB (large due to comprehensive map style definition)
- **Load time**: 2-5 seconds (primarily CDN resource loading)
- **Runtime performance**: Excellent (MapLibre GL JS is highly optimized)
- **Memory usage**: Minimal (single page application)

### Troubleshooting

#### Map doesn't load (black screen)
- Check browser console for CDN loading errors
- Verify internet connection
- Test with different browser
- Check if CDN URLs are accessible

#### JavaScript errors
- Most likely cause: CDN resources failed to load
- Solution: Refresh page, check network connectivity

#### Map tiles don't appear
- PMTiles protocol may not be registered correctly
- Check console for protocol registration errors
- Verify PMTiles CDN resource loaded successfully

## Working with External Dependencies

### CDN Resource Information
All external dependencies are loaded from UNPKG CDN:
- **Stable versions**: Specific version numbers are pinned
- **Update procedure**: Change version numbers in HTML head
- **Fallback**: No local fallback dependencies exist
- **Testing**: Always verify CDN resources load after version updates

### Data Attribution Requirements  
- **Map Data**: © OpenStreetMap contributors
- **Basemap Style**: © Protomaps
- **Fonts**: Noto Sans font family for international text support

**CRITICAL**: Always maintain attribution links in map style definition.

## File Locations Reference

### Primary Files
- **Main application**: `/docs/index.html` - Complete application
- **Documentation**: `/README.md` - Project overview and features
- **License**: `/LICENSE` - CC0 1.0 Universal (public domain)

### Generated/Build Files
- **None**: No build artifacts or generated files

### Configuration Files  
- **None**: No configuration files required

This project exemplifies extreme simplicity - everything needed is in one HTML file that runs directly in any web browser.