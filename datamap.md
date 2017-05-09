
I made a [adoption.csv](adoption.csv) file to contain adoption and euthanasia data. I used this data to decide the color of each states.

Next thing is to draw the map

```
//prepare choropleth adoption
    var laws = d3.map();

    d3.queue()
        .defer(d3.json, "map.json")
        .defer(d3.csv, "adoption.csv", function(d) { laws.set(d.STATE, + d.ADOPT); })
        .await(ready);

    console.log(laws);

    //draw the no data states
    d3.json("map.json", function(err,geojson){
        svg.selectAll(".state")
          .data(geojson.features)
          .enter()
          .append("path")
          .attr("d",path)
          .attr("fill","#353535")
          ;
    })

    //draw the adoption rate map and make a class named astate
    function ready(error, map, data) {
      if (error) throw error;
      d3.json("map.json", function(err,geojson){
        svg.selectAll(".astate")
          .data(geojson.features)
          .enter()
          .append("path")
          .attr("d",path)
          .attr("fill","#4CEEEF")
          .attr("fill-opacity", function(d){
            var state1 = d.properties.STUSPS;
            return(laws["$" + state1]*0.012);
          })
          .attr("stroke","#fff")
          .classed("astate", true)
          ;
      })
    };
```

[Next Step](circle.md)
