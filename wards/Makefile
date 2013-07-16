all: PhiladelphiaPoliticalWards201302.shp wards.json wards-topo.json

wards.zip:
	curl -o wards.zip http://www.pasda.psu.edu/philacity/data/PhiladelphiaPoliticalWards201302.zip

PhiladelphiaPoliticalWards201302.shp: wards.zip
	unzip wards.zip
	touch PhiladelphiaPoliticalWards201302/PhiladelphiaPoliticalWards201302.shp

wards.json: PhiladelphiaPoliticalWards201302.shp
	ogr2ogr -f "GeoJSON" -t_srs "EPSG:4326" wards.json PhiladelphiaPoliticalWards201302/PhiladelphiaPoliticalWards201302.shp

wards-topo.json: wards.json
	topojson -o wards-topo.json --id-property WARD_NUM wards.json
