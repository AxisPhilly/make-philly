all: city-limits.zip city_limits.shp city-limits.json city-limits-topo.json

city-limits.zip:
	curl -o city-limits.zip http://www.pasda.psu.edu/philacity/data/phila-city_limits_shp.zip

city_limits.shp: city-limits.zip
	unzip city-limits.zip
	touch city_limits.shp

city-limits.json: city_limits.shp
	ogr2ogr -f "GeoJSON" -t_srs "EPSG:4326" city-limits.json city_limits.shp

city-limits-topo.json: city-limits.json
	topojson -o city-limits-topo.json city-limits.json
