# STAC Browser

This is a [Spatio-Temporal Asset Catalog
(STAC)](https://github.com/radiantearth/stac-spec) browser for static catalogs.
It attempts to surface all included data in a user-centric way (an approach
which can inform how data is represented in the evolving spec). It is
implemented as a single page application (SPA) for ease of development and to
limit the overall number of catalog reads necessary when browsing (as catalogs
may be nested and do not necessarily contain references to their parents).

## Examples

* [planet.stac.cloud](https://planet.stac.cloud) ([catalog on GitHub](https://github.com/cholmes/pdd-stac/))
* [CBERS](https://cbers.stac.cloud) ([catalog tools on GitHub](https://github.com/fredliporace/cbers-2-stac))
* [Google Earth Engine](https://gee.stac.cloud)
* [sat-api.stac.cloud](https://sat-api.stac.cloud) ([sat-api on GitHub](https://github.com/sat-utils/sat-api))

For a longer list of examples, checkout out [stac.cloud](http://stac.cloud).

## Running

By default, stac-browser will browse the [testbed Planet
catalog](https://raw.githubusercontent.com/cholmes/sample-stac/master/stac/catalog.json)
([GitHub](https://github.com/cholmes/sample-stac/)). To browse your own, set
`CATALOG_URL` when building.

```bash
npm install
CATALOG_URL=http://path/to/catalog.json npm start -- --open
```

Validation will happen againt the version of stac defined in the Catalog, Collection or Item
`stac_version` property. If you are running against an older STAC version where the objects
do not conatin a `stac_version` property, you'll need to set the `STAC_VERSION` environment
variable e.g.:

```
STAC_VERSION=0.6.0 CATALOG_URL=http://path/to/catalog.json npm start -- --open
```

## Building

```bash
CATALOG_URL=http://path/to/catalog.json npm run build
```

## Publishing

After building, `dist/` will contain all assets necessary to
host the browser. These can be manually copied to your web host of choice.

## Contributing

STAC Browser uses [Vue](https://vuejs.org/).

Catalogs and collections are rendered using the
[`Catalog`](src/components/Catalog.vue) component in
[`src/components/`](src/components/). Items are rendered using the
[`Item`](src/components/Item.vue) component. Common functionality across both
components exists in [`src/components/common.js`](src/components/common.js).
Mappings between property keys (e.g. `eo:platform`) are defined in
[`src/properties.js`](src/properties.js).

## Alternate Implementations

If you're interested in experimenting with a STAC browser built with different
JS frameworks, check out:

* [GravityLabGeo/stacjs](https://github.com/GravityLabGeo/stacjs) - a
  jQuery-based viewer
* [alkamin/stac-gdalsj-browser](https://github.com/alkamin/stac-gdaljs-browser) -
  an Ember-based viewer
