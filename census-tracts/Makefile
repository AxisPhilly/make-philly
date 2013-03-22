all: tracts.zip tl_2012_42_tract.shp census-tracts.json census-tracts-topo.json

tracts.zip:
	curl -o tracts.zip 'http://www2.census.gov/geo/tiger/TIGER2012/TRACT/tl_2012_42_tract.zip'

tl_2012_42_tract.shp: tracts.zip
	unzip tracts.zip
	touch tl_2012_42_tract.shp

census-tracts.json: tl_2012_42_tract.shp
	ogr2ogr -f "GeoJSON" -t_srs "EPSG:4326" -where "COUNTYFP = '101'" census-tracts.json tl_2012_42_tract.shp

census-tracts-topo.json: census-tracts.json
		topojson -o census-tracts-topo.json --id-property NAME census-tracts.json