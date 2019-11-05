## Create and manage geospatial data

**Project description:** Open source coding (R, Python, etc.) as a geographic information system (GIS).

### 1. Creating spatial data using the sf (simple features) R package

Point, line, and polygon features created from scratch or from existing spatial data (e.g., shapefiles). 

```R
epa01_cosub2018 <- 
  st_read("../../data/epa01_cosub2018.geojson", 
          stringsAsFactors = FALSE)
```

### 2. Joining spatial data to external information

```javascript
if (isAwesome){
  return true
}
```

### 3. Visualizing results

<img src="../images/cosubs_rainfall_thumbnail.png?raw=true"/>

### 4. Summary and next steps

Creating spatial data and using data in an analysis. 

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
