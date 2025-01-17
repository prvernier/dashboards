### 1. Data preparation

The main objective of the data preparation component is to create an analysis-ready database consisting of caribou locations, landscape and climate covariates, and attributes identifying seasons and migration periods.

**Telemetry data:**

- Import data directly from movebank.org (YT)
- Import shapefile data from BC Government [Can we get access to movebank project?]
    - Select individuals and years to use (see below re. overlap)
- For BC and YT data:
    - Acquire, clean, and save caribou location data [Has this been done for either datasets?]
    - Identify and remove duplicate observations
    - Identify and remove outliers
    - Assess telemetry errors
    - Thin data by space and/or time
    - Save as RDS objects, CSV files, and Shapefiles
- Combine BC and YT data [How will this be done and who will do it?]
    - Ensure there is no spatial or temporal overlap
- Define seasons and migration periods
- Which seasons are of interest?
    - Early winter, late winter, fall rut, spring, summer
    - Spring and fall migration
    - Snow and snow-free seasons
- Review segmentation methods for evaluating seasons e.g., expert knowledge, Migration-Mapper
- Apply selected method to define seasons

**Covariate data:**

- Acquire and prepare a set of covariate rasters that have the same resolution, extent, project, and are aligned
    - Topography: elevation, slope, aspect, ruggedness, easting (eastness), northing (northness)
    - Landcover: forest (conifer, deciduous, mixedwood), shrubland, grassland, wetland, barren/snow/ice
    - Anthropogenic: linear and areal disturbances (occurrence, distance to, neighbourhood)
    - Natural disturbances: fire polygons, burn areas
- Acquire and prepare normal and projected bioclimate data from climateNA
    - Bioclimate normals [1990-2020?] and selected scenarios [projected to 2050, 2080?]

**Extract values**

- Extract raster values using caribou location data using `terra` package
- Save as CSV and GPKG files