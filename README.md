# maps
## Geojsons of India and States, union territories of India

#### India map
![India map](https://github.com/adarshbiradar/maps/blob/master/etc/indiamap.png?raw=true)

#### Karnataka map
![Karnataka map](https://github.com/adarshbiradar/maps/blob/master/etc/karnatakamap.png?raw=true)

## Ploting maps using highmaps and geojson

# html
```html
<html>
    <head>
        <title>Document</title>
    <head>
    <body>
        <div class='india-map'></div>
    <body>
    <script src="http://code.highcharts.com/maps/highmaps.js"></script>
<html>
```

# JS
```javascript
    var statename = "India"
    var statekey = statename.toLowerCase().replace(/ /g,"")
    loadJson(statekey+'.json',function(geojson){
       mapFunction(geojson);
    });
```
format of mapdata 
[['statename',value],['statename',value],....]

for statemaps change 
1. keys: ['st_nm', 'value'], to ['district','value'] 
2. joinBy: 'st_nm' to 'district'
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

# CSS
```css
.india-map {
    height: 700px;
    width: 700px;
}
```
