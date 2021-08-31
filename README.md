# Geovisto Themes Tool
Extension of the [Geovisto core library](https://github.com/geovisto/geovisto) which provides support for custom style themes.

This repository is a snapshot of Geoviosto ``tools/themes`` derived from the development repository: [geovisto/geovisto-map](https://github.com/geovisto/geovisto-map).

## Usage

![sample](https://user-images.githubusercontent.com/1479229/131548390-5fae5b11-b7d3-47ca-83b4-5e74859fd245.png)

```js
import {
    GeovistoThemesTool
} from 'geovisto-themes';

// ,,,

// create instance of map with given props
const map = Geovisto.createMap({
    // ...
    tools?: Geovisto.createMapToolsManager([
        // instances of Geovisto tools (extensions) which will be directly used in the map
        // ...
        GeovistoThemesTool.createTool({
            id: "geovisto-tool-themes",
            manager: GeovistoThemesTool.createThemesManager([
                  // manager of style themes
                  GeovistoThemesTool.createThemeBasic(),
                  // ...
            ]),
            theme?: IMapTheme // optional default theme
        }),
    ])
});

// rendering of the map
map.draw(Geovisto.getMapConfigManagerFactory().default({
  // initial settings of the map can be overriden by the map config - JSON structure providing user settings 
  // ...
  tools?: [
    // config of Geovisto tools (extensions) used in the map
    {
      "type?": "geovisto-tool-themes", // type of the tool (in the case the id of a tool instance is not specified)
      "id?": "geovisto-tool-themes", // id of the tool instance, else new instance is created (this tool is singleton)
      "enabled?": true, // tool is enabled/disabled by default
      "theme?": "basic" // id of default theme (needs to exist in the theme manager)
    },
  ]
}));
```

## Installation

```
npm install --save geovisto-themes
```

Peer dependencies:
```
npm install --save geovisto leaflet
```

This package serves as an extension of Geovisto core using the API for Geovisto tools (extensions). Follow Geovisto core on [Github](https://github.com/geovisto/geovisto).

## Extensions

New custom themes can be implemented by implementing the [``IMapTheme``](https://github.com/geovisto/geovisto-themes/blob/master/src/model/types/theme/IMapTheme.ts) interface.

## License

[MIT](https://github.com/geovisto/geovisto-themes/blob/master/LICENSE)

Note that the style themes allows to refer URL of [tile layer providers](https://github.com/leaflet-extras/leaflet-providers) ([examples](http://leaflet-extras.github.io/leaflet-providers/preview/index.html)). Make sure you use them with respect to license of the tiles providers.