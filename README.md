# Autopilot

An interactive web map viewer built with MapLibre GL JS, featuring efficient tile delivery and high-quality basemap styling.

## Overview

This project provides a clean, fast-loading interactive map interface that can serve as a foundation for navigation, routing, or other geospatial applications. The map features a comprehensive style with detailed geographic layers and smooth interactions.

## Features

- **Interactive Map**: Pan, zoom, and explore with smooth animations
- **Navigation Controls**: Built-in zoom and rotation controls
- **Globe View**: 3D globe control for global perspective
- **Efficient Tiles**: Uses optimized vector tiles for fast tile delivery
- **Comprehensive Styling**: Detailed basemap with multiple data layers:
  - Land cover and land use
  - Water bodies (rivers, lakes, oceans)
  - Transportation networks (roads, railways, runways)
  - Buildings and urban areas
  - Administrative boundaries
  - Place labels and addresses
- **URL Hash**: Map state persists in browser URL for easy sharing

## Demo

The map is available at: [GitHub Pages](https://hfu.github.io/autopilot/)

## Technical Details

### Technologies Used

- **[MapLibre GL JS](https://maplibre.org/)** - Open-source map rendering library
- **[Protomaps](https://protomaps.com/)** - Open-source basemap data and styling

### Map Style

The map uses a custom light theme style with:
- Vector tiles served via HTTP
- Multi-language label support with fallbacks
- Zoom-dependent styling for optimal readability
- Comprehensive icon set for points of interest

### Data Attribution

- **Map Data**: © [OpenStreetMap](https://openstreetmap.org) contributors
- **Basemap Style**: © [Protomaps](https://github.com/protomaps/basemaps)
- **Fonts**: Noto Sans font family for international text support

## Usage

### Viewing the Map

Simply open `docs/index.html` in a web browser, or visit the GitHub Pages URL.

### Controls

- **Pan**: Click and drag to move around the map
- **Zoom**: Use mouse wheel, zoom buttons, or pinch gestures
- **Rotate**: Right-click and drag, or use the navigation control
- **Globe**: Click the globe button to switch to 3D globe view

### URL Sharing

The map state (center, zoom, rotation) is automatically saved to the browser URL, making it easy to share specific map views.

## Development

### File Structure

```
├── LICENSE                 # CC0 1.0 Universal license
├── README.md              # This file
└── docs/
    └── index.html         # Main map application
```

### Local Development

To run locally:

1. Clone this repository
2. Serve the `docs` directory with any web server
3. Open `index.html` in a browser

For example, using Python:
```bash
cd docs
python -m http.server 8000
# Open http://localhost:8000 in your browser
```

### Customization

The map style is defined inline in `docs/index.html`. You can modify:
- **Colors**: Update the paint properties for different layers
- **Data Source**: Change the tile source URL to use different map data
- **Fonts**: Modify the font stack in the style definition
- **Controls**: Add or remove map controls as needed

## License

This project is released under the [CC0 1.0 Universal](LICENSE) license, placing it in the public domain.

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests to improve the map or documentation.