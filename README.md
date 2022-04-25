## KML and KMZ files to Geopackage files

Using a Xml streaming library to read the kml file and convert the hierarchal data into relational data that GeoPackages can store.

### Installation ###

[![NPM](https://img.shields.io/npm/v/@ngageoint/geopackage-kml-js.svg)](https://www.npmjs.com/package/@ngageoint/geopackage-kml-js)

```sh
$ npm install @ngageoint/geopackage-kml-js
```

### Usage

```sh
./cli /path/to/file/to/convert.kml /path/to/file/to/create.gpkg
```

---
### Currently Supports
- Placemark tags with and without coordinates
  Stored as features in a feature table with any additional tags stored in a column of the table.
    - Multigeometry tags
    - Polygon tags
        - inner and outer boundaries.
    - LineString tags
    - Point tags
- Most of Icon, Polygon and Line Style tags
    - color converted to rgba
- GroundOverlay tags
    - Image converision from EPSG: 4326 to EPSG: 3857 Web-mercator
        - Image manipulation preformed by [Jimp](https://github.com/oliver-moran/jimp).
        - Coordinate converision from [Proj4](https://github.com/proj4js/proj4js).
    - Creates a tile set at appropriate from the zoomlevels.
        - Starting at the zoomlevel where the GroundOverlay is covered by one tile.
        - Ending where the image resolution matches that of the tile.
        - This is done in steps of 2.
- Default Stylings of Google Earth.
- gx:altitudeMode
- ExtendedData
---
### Does not support but plan on supporting
- [ ] Network Links
- [ ] ScreenOverlays
- [ ] Folder and Document structure
- [ ] PhotoOverlays
- [ ] StyleMaps
    - currently only captures normal style
- [ ] Region
- [x] gx:x, gx:y, gx:h and gx:w

---
### Does not support and no plans to support currently
- lookAt tags
    - Current it is stored as a JSON string in a column of the feature table
- Most of gx extensions
- Models tags
- Camera
- colorMode
- gx:LatLonQuad
- Google Sky
- ListStyle
- NetworkLinkControl
