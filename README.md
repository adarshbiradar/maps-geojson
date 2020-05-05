# maps
## Geojsons of India and States, union territories of India

checkout the maps ploted using these geojsons on https:/www.coronaindia.ml/

## Ploting maps using highmaps and geojson

```javascript
    var statename = "karnataka"
    var statekey = statename.toLowerCase().replace(/ /g,"")
    loadJson('/states/'+statekey+'.json',function(geojson){
        mapFunction(geojson);
    });
```
format of mapdata 
[['statename',value],['statename',value],....]
```javascript
    
    function mapFunction(geojson)
{
    
    var series = [{
        data: mapdata,
        name : 'Confirmed',
    }]
    console.log(series)
    Highcharts.mapChart('india-map', {
        chart: {
            map: geojson,
        },
        title: {
            text: ''
        },
        plotOptions: {
            map: {
                allAreas: false,
                keys: ['st_nm', 'value'],
                joinBy: 'st_nm',
                states: {
                    hover: {
                        color: 'black'
                    }
                },
                dataLabels: {
                    enabled: false,
                },
            }
        },
        colorAxis: {
            min: 0,
            max: 500,
            minColor: '#FFFFFF',
            maxColor: '#08306b',
            lineColor: 'white',
            lineWidth: 10,
        },
        legend: {
            enabled: false,
        },
        mapNavigation: {
            enabled: false,
        },
        tooltip: {
            pointFormat: '{point.st_nm}: <b>{point.value}</b> cases',
        },
        series: series,
    });
}
```
