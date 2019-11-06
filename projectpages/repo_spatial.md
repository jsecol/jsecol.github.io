## Create and manage geospatial data

**Project description:** Open source coding (R, Python, etc.) as a geographic information system (GIS).

### 1. Load spatial data using the sf (simple features) and raster R packages

Polygon features from a GeoJSON file and raster grid from an ASCII file. 

```javascript
epa01_cosub2018 <- 
  st_read("../../data/epa01_cosub2018.geojson", 
          stringsAsFactors = FALSE)

rpe_1d_1y <- raster("../../data/raster/asc/rpe_1d_1y.asc")		  
```

### 2. Plot them

```javascript
plot(rpe_1d_1y)
plot(st_geometry(epa01_cosub2018), add = TRUE)
```

<img src="../images/cosubs_rainfall_data_thumbnail.png?raw=true"/>


### 3. Extract raster data at the center of each polygon feature

```javascript
locations_rpe_1d_1y <-
  extract(x = rpe_1d_1y,
          y = epa01_cosub2018[, c("INTPTLON", "INTPTLAT")],
          method = "bilinear")
```

### 4. Join back to polygon features and visualize chloropleth

```javascript
epa01_cosub2018 <- epa01_cosub2018 %>% 
  left_join(., locations_rpe_1d_1y, by = "GEOID")
  
plot(epa01_cosub2018["rpe_1d_1y"], 
     main = "Extreme Precipitation Estimates (1 day/1 year)")
```

<img src="../images/cosubs_rainfall_thumbnail.png?raw=true"/>

### 5. Next steps

Use new data in an analysis. 

<br><br>

For more details see this [Spatial GitHub Repo](https://github.com/jsecol/spatial).
