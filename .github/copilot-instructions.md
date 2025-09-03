# Autopilot - Interactive Web Map Viewer

**ALWAYS follow these instructions first and fallback to additional search and context gathering only if the information in these instructions is incomplete or found to be in error.**

Autopilot is a simple, static interactive web map viewer built with MapLibre GL JS that displays maps using PMTiles format. It consists of a single HTML file with no build system, dependencies, or complex setup requirements.

## Working Effectively

### Quick Start
- **NO BUILD REQUIRED**: This is a static HTML application that runs directly in web browsers
- **NO DEPENDENCIES**: All libraries (MapLibre GL JS, PMTiles) are loaded via CDN
- **NO PACKAGE MANAGERS**: Do not run `npm install`, `pip install`, or any dependency installation commands

### Local Development
To run the application locally, serve the `docs` directory with any web server:

#### Option 1: Python HTTP Server (Recommended)
```bash
cd docs
python3 -m http.server 8000
# Application will be available at http://localhost:8000
```

#### Option 2: Node.js HTTP Server
```bash
cd docs
npx http-server -p 8000 -c-1
# Application will be available at http://localhost:8000
```

#### Option 3: Any Other Web Server
Any web server that can serve static files will work. Simply serve the `docs` directory.

### Timing Expectations
- **Server startup**: Instant (< 1 second)
- **Application load**: 2-5 seconds (depending on network for CDN resources)
- **Map rendering**: 3-10 seconds (depending on network for tile data)

## Validation

### Manual Testing Scenarios
After making any changes, ALWAYS test these scenarios:

1. **Basic Map Load Test**:
   - Open http://localhost:8000 in a browser
   - Verify the map loads and displays the world view
   - Check browser console for JavaScript errors

2. **Map Interaction Test**:
   - **Pan**: Click and drag to move around the map
   - **Zoom**: Use mouse wheel or zoom buttons to zoom in/out
   - **Rotate**: Right-click and drag to rotate the map
   - **Globe**: Click the globe button to switch to 3D globe view

3. **Navigation Controls Test**:
   - Test zoom in/out buttons work
   - Test compass rotation control works
   - Test globe control toggles 3D view

4. **URL Hash Test**:
   - Navigate to a specific location
   - Verify URL updates with map coordinates
   - Refresh page and verify map returns to same location

### Validation Commands
```bash
# Start local server
cd docs && python3 -m http.server 8000

# Test server responds
curl -I http://localhost:8000

# Open in browser and manually test map functionality
```

## Repository Structure

```
/
├── LICENSE              # CC0 1.0 Universal license
├── README.md           # Project documentation
└── docs/
    └── index.html      # Main application (single file)
```

## Key Technologies

- **[MapLibre GL JS](https://maplibre.org/)**: Open-source map rendering library (v5.6.1 via CDN)
- **[PMTiles](https://github.com/protomaps/PMTiles)**: Cloud-optimized map tile format (v3.0.7 via CDN)
- **[Protomaps](https://protomaps.com/)**: OpenStreetMap-based basemap data and styling

## Common Tasks

### Making Code Changes
- Edit `docs/index.html` directly
- No compilation or build step required
- Refresh browser to see changes immediately

### Modifying Map Style
- Map style is defined inline in `docs/index.html` starting around line 17
- Modify paint properties, colors, or layer definitions directly
- No external style files or build process

### Changing Map Data Source
- Modify the PMTiles URL in the style definition (around line 23)
- Currently uses: `https://data.source.coop/protomaps/openstreetmap/v4.pmtiles`

### Adding Map Controls
- Add controls using MapLibre GL JS API
- Example: `map.addControl(new maplibregl.NavigationControl());`
- Controls are added at the bottom of the script section

### Debugging
- Open browser developer tools
- Check Console tab for JavaScript errors
- Check Network tab for failed resource loads
- Map loads external resources from CDN, network issues may affect functionality

## Deployment

- **Production**: Automatically deployed to GitHub Pages from the `docs` directory
- **URL**: https://hfu.github.io/autopilot/
- **No build step**: Direct deployment of static files

## Limitations and Notes

- **Internet Required**: Application loads MapLibre GL JS and PMTiles libraries from CDN
- **CORS Restrictions**: Some local testing scenarios may require proper web server (not file:// protocol)
- **External Dependencies**: Map tiles and fonts are loaded from external services
- **No Backend**: This is a purely client-side application with no server-side components
- **No Testing Framework**: No automated tests exist; rely on manual validation
- **No Linting**: No code style checks or linting configured

## Troubleshooting

### Map Doesn't Load
1. Check browser console for JavaScript errors
2. Verify internet connection (CDN resources required)
3. Try different web server (Python vs Node.js)
4. Check if CDN resources are accessible
5. **Note**: In restricted environments, external CDN resources may be blocked - this is expected in sandboxed environments

### Performance Issues
1. Check network connection speed
2. Verify PMTiles server is responsive
3. Consider caching CDN resources locally for development

### Development Environment
- **Any modern web browser** (Chrome, Firefox, Safari, Edge)
- **Any web server** capable of serving static files
- **Text editor** for editing HTML/CSS/JavaScript

## Example Commands Reference

```bash
# Repository setup (fresh clone)
git clone https://github.com/hfu/autopilot.git
cd autopilot

# Start development server
cd docs
python3 -m http.server 8000

# Test application is running
curl http://localhost:8000

# Open in browser
# Navigate to http://localhost:8000
# Test map functionality manually

# Make changes
# Edit docs/index.html
# Refresh browser to see changes
```

Remember: This is a simple static web application. No complex build systems, dependency management, or deployment processes are required.