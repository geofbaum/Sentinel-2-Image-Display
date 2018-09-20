```python
# connect to the API
# written using sentinelsat v0.12
from sentinelsat.sentinel import SentinelAPI, read_geojson, geojson_to_wkt #get_coordinates
from datetime import date
api = SentinelAPI('GeoffreyBa', 'scoob20003', 'https://scihub.copernicus.eu/dhus')

#f = open('output.txt','w')

# download single scene by known product id
#api.download(<product-id>)

area = geojson_to_wkt(read_geojson('map.geojson'))

# search by polygon, time, and SciHub query keywords
products = api.query(area,
                     date =('20180901', date(2018, 9, 20)),
                     platformname = 'Sentinel-2',
                     filename ='*T18TXR*',
                     cloudcoverpercentage=(0, 100))# \
                     #date = ('20170814', date(2017, 8, 14)),
                     #initial_date=('20170801', date(2017, 4, 1)),  \
                     #end_date=('20170829', date(2017, 4, 16)))#, \
                     #platformname = 'Sentinel-2') #, # \
                     #filename = '*_T18TXR_*')
                     #tileid = '18TXR')#,
                     #cloudcoverpercentage = (0 , 80))
#products.sort(key=lambda x: float(x["double"]["content"]))

# download all results from the search
#api.download_all(products)

# GeoJSON FeatureCollection containing footprints and metadata of the scenes
#api.get_footprints(products)

print(products)
#f.write(str(products))
#print('Available Products written to file.')
```
