
I downloaded the map from the [Natural Earth](http://www.naturalearthdata.com/). There were various map files and I chose the Mediam Scale Data - Cultural because it used the cities, states as the boundary and had enough details I needed. The file was the .shp so I had to conver it to a .json. 

Open the terminal and go to the desk

```
cd ~/desktop
```
Convert the .shp to .json
```
shp2json cb_2015_state_500k.shp -o us.json to convert your file. 
```

The code I used to draw the map in the d3 is

```
 var width = 1000;
    var height = 605;

 var projection = d3.geoAlbersUsa()
    .translate([width/2,height/2])
    .scale(width)
     ;
     
 // make a path generator
 var path = d3.geoPath()
    .projection(projection)
    ;

 //draw svg container
 var svg = d3.select("#viz").append("svg")
    .attr("width",width)
    .attr("height",height)
    .style("background-color","#FFFFFF")
    ;

 d3.json("map.json", function(err,geojson){
     svg.selectAll(".state")
       .data(geojson.features)
       .enter()
       .append("path")
       .attr("d",path)
       .attr("fill","#E4E4E4")
       .attr("stroke","#fff")
       ;
 })
 ```
 
 [Next Step](datamap.md)
    
