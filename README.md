# Orchard UAV GIS Analysis

## Overview

This project presents a GIS-based analysis of a small orchard using RGB imagery acquired by a UAV. The workflow combines photogrammetric processing, GIS analysis, vegetation indices and spatial interpolation to characterize individual trees and investigate their spatial variability.

The project was developed as a practical study in UAV-based environmental monitoring and geospatial analysis.

## Study Area and Data

The study area is a private garden in Blejoi, Prahova County, Romania, covering approximately 600 m².

### UAV survey

- **Survey date:** 11 July 2026
- **Survey time:** approximately 11:30
- **Weather:** clear sky
- **Temperature:** 24 °C
- **Wind speed:** approximately 7 km/h
- **Data type:** RGB aerial imagery

The RGB imagery was processed photogrammetrically to obtain spatial data products used in the subsequent GIS analysis.

## Objectives

The main objectives of the project were:

- to generate photogrammetric products from UAV RGB imagery;
- to identify and characterize individual trees;
- to estimate tree height using two different approaches;
- to calculate canopy area;
- to calculate RGB-based vegetation indices, GLI and VARI;
- to investigate relationships between tree characteristics and vegetation indices;
- to analyze the spatial distribution of GLI and VARI;
- to produce thematic maps and interpret the obtained results.

## Methodology

The workflow consisted of the following main stages:

1. UAV image acquisition;
2. photogrammetric processing;
3. generation of an orthophoto, DSM and DTM;
4. creation of a Canopy Height Model (CHM);
5. digitization of individual trees;
6. estimation of tree height using two approaches;
7. calculation of canopy area;
8. calculation of GLI and VARI from RGB imagery;
9. statistical analysis of the obtained variables;
10. spatial interpolation using the IDW method;
11. production of thematic maps;
12. interpretation of the spatial and statistical results.

## Tree Characterization

A total of 15 individual trees were digitized and analyzed.

For each tree, the analysis included:

- tree ID;
- species;
- estimated height;
- canopy area;
- GLI;
- VARI.

Tree height was estimated using two approaches:

- **DSM–DTM difference**, using the Canopy Height Model;
- **DSM-based estimation**, using the maximum DSM elevation within the crown and a local ground reference estimated from an external buffer.

The comparison of the two approaches was used to investigate the limitations of photogrammetric height estimation for small or poorly reconstructed tree crowns.

## RGB Vegetation Indices

Two vegetation indices based on RGB imagery were calculated:

### GLI — Green Leaf Index

GLI was used to describe the relative contribution of the green channel in the RGB imagery and to investigate spatial differences in vegetation appearance.

### VARI — Visible Atmospherically Resistant Index

VARI was calculated as an additional RGB-based indicator of vegetation conditions.

Both indices were analyzed at the individual-tree level and subsequently interpolated spatially using the IDW method.

## Statistical Analysis

The relationship between tree characteristics and RGB vegetation indices was investigated using descriptive statistics and correlation analysis.

The analysis included relationships between:

- tree height and GLI;
- canopy area and GLI;
- tree species and mean GLI;
- corresponding variables related to VARI.

The statistical results were used together with the spatial analysis to better understand the variability observed within the study area.

## Spatial Analysis

Spatial analysis was performed in QGIS.

The project included thematic maps representing:

- tree height;
- tree species;
- GLI;
- VARI.

IDW interpolation was subsequently applied to the GLI and VARI point values to visualize their spatial distribution across the study area.

The interpolated surfaces provide a continuous spatial representation of the variation observed at the sampled trees.

## Results

The project resulted in:

- a photogrammetric orthophoto;
- DSM and DTM products;
- a CHM derived from DSM and DTM;
- a spatial database of 15 individual trees;
- tree height and canopy area measurements;
- GLI and VARI values for individual trees;
- statistical relationships between tree characteristics and vegetation indices;
- thematic maps;
- IDW interpolation maps for GLI and VARI.

One important observation was the presence of trees for which the CHM provided values close to zero. These cases were associated with crowns that were not sufficiently reconstructed in the DSM. The alternative DSM-based approach was able to recover useful height information in at least some of these cases.

This highlights an important limitation of RGB photogrammetry when working with small, sparse or partially visible tree crowns.

## Project Outputs

### Documentation

The complete project report is available in the [documentation](documentation/) folder.

### Maps

The final thematic and interpolation maps are available in the [maps](maps/) folder.

### Results

The statistical analysis and comparison of height estimation methods are available in the [results](results/) folder.

## Tools and Technologies

- QGIS
- WebODM
- Microsoft Excel
- UAV RGB imagery
- Photogrammetry
- GIS spatial analysis
- IDW interpolation

## Limitations and Future Development

The project is based exclusively on RGB imagery and therefore does not provide direct access to multispectral vegetation information.

Future development could include:

- multispectral UAV imagery;
- automated geospatial processing using Python;
- 3D analysis of photogrammetric point clouds;
- automated extraction of tree characteristics;
- integration of additional environmental measurements;
- development of more advanced spatial analysis and decision-support workflows.
  
## Author

**Daria Sicaru**  
Applied Informatics in Environmental Engineering
