all: Neighborhoods_Philadelphia.shp neighborhoods.json neighborhoods-topo.json

Neighborhoods_Philadelphia.shp:
	git clone git@github.com:azavea/geo-data.git
	touch geo-data/Neighborhoods_Philadelphia/Neighborhoods_Philadelphia.shp

neighborhoods.json: Neighborhoods_Philadelphia.shp
	ogr2ogr -f "GeoJSON" -t_srs "EPSG:4326" neighborhoods.json geo-data/Neighborhoods_Philadelphia/Neighborhoods_Philadelphia.shp

neighborhoods-topo.json: neighborhoods.json
	topojson -o neighborhoods-topo.json --id-property NAME neighborhoods.json
