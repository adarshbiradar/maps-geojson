# maps
## Geojsons of India and States, union territories of India


## Ploting maps using highmaps and geojson

```javascript
    var statename = "karnataka"
    var statekey = statename.toLowerCase().replace(/ /g,"")
    loadJson('/states/'+statekey+'.json',function(geojson){
        mapFunction(geojson);
    });
```
