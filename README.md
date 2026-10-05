# Spatial Lookup Prototype

An Arabic, right-to-left web map for exploring location-based district classifications in Alexandria. The application is contained in `index.html`; the GitHub repository retains its original name, `-`.

## Source-level features

- A Leaflet map with a draggable marker and click-to-select locations.
- Coordinate input, place-name search, and optional browser geolocation.
- District/classification results from an external spatial-query service.
- A client-side rent-estimate calculator and a printable result report.

## Architecture and dependencies

The frontend uses HTML, CSS, and vanilla JavaScript, with Leaflet, externally hosted fonts/icons, CARTO map tiles, and OpenStreetMap Nominatim place search. No package installation or build step is defined.

`CONFIG.apiUrl` in `index.html` points to the spatial-query backend. The backend and its dataset are not included in this repository. The frontend posts a selected latitude/longitude and expects a result containing `status`, `district`, and `type`. A local preview alone cannot reproduce that service.

## Local preview

Before running a copy, review its external-service settings and configure a backend you control, using synthetic or approved test data. Searches are sent to the geocoding provider; querying a marker sends its coordinates to the configured backend. Use manual sample coordinates if you do not want to share your device location.

With Python 3 installed, serve the repository directory:

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Then open `http://127.0.0.1:8000/`. Internet access is required for the external map, font, and library resources. Browser geolocation also requires a supported secure context and permission. This preview command was not run during the documentation review.

## Important limitations

This is a source-code prototype, not a verified official service. District boundaries, backend availability, and classification accuracy have not been validated here. The rent calculator uses rules hard-coded in the frontend; this README does not validate their legal applicability or currency. Do not use its output as legal advice, an authoritative valuation, a title document, or a permit. The print view itself notes that its output is not proof of ownership or an official licence.

Documentation is based on source inspection on October 5, 2026. No live location queries, backend calls, geolocation requests, or end-to-end tests were performed.
