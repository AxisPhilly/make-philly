# make-philly

A collection of Makefiles to get and convert Philly geodata into web-friendly formats (i.e. GeoJSON and TopoJSON).

We were inspired to learn Make from [Mike Bostock](https://github.com/mbostock/)'s [Why Use Make](http://bost.ocks.org/mike/make/) article and to create this collection from his [us-atlas](https://github.com/mbostock/us-atlas) and [world-atlas](https://github.com/mbostock/world-atlas) projects.

### Dependencies

All of the Makefiles depend on [ogr2ogr](http://www.gdal.org/ogr2ogr.html) (which is part of [GDAL](http://www.gdal.org/), and most of the steps require [Node.js](http://nodejs.org/) and [Topojson](https://github.com/mbostock/topojson). On OS X, GDAL and Node can can be installed with [Homebrew](http://mxcl.github.com/homebrew/):

    $ brew install node
    $ brew install gdal

Once you have Node, you can install TopoJSON with [NPM](https://npmjs.org/):

    $ npm install -g topojson

### Usage

These Makefiles mostly do the following:

- Download a ZIP file or Shapefile
- Extract the ZIP file if need be
- Convert the Shapefile to GeoJSON
- Convert the GeoJSON to TopoJSON

Each Makefile is stored in a directory named after the data it retrieves and processes. 

First, `cd` into the directory for the data you want. Then, to run all of the steps of the Makefile:

    $ make all

If you only want the GeoJSON of the [Azavea](http://www.azavea.com) neighborhood [data](https://github.com/azavea/geo-data/tree/master/Neighborhoods_Philadelphia), for example, you can execute that task, and all of its dependent tasks:

    $ make neighborhoods.json

Data that is projected in [EPSG:2272](http://spatialreference.org/ref/epsg/2272/) is reprojected in [EPSG:4326](http://spatialreference.org/ref/epsg/4326/) for easy web-map compatiability. You can change which projection the data is reprojected in, or remove the reprojection step by editing or removing the `-t_srs` flag of steps that use `ogr2ogr`.

### Testing

For a quick preview and test of GeoJSON files, use [GeoJSONLint.com](http://geojsonlint.com/).