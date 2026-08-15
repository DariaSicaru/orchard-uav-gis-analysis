# Orchard UAV GIS Analysis

## Overview

This project presents a GIS-based analysis of a small orchard using RGB imagery acquired by a UAV. The workflow combines photogrammetric processing, spatial analysis and vegetation indices to characterize individual trees and investigate their spatial variability.

## Study Area

- Location: Blejoi, Prahova, Romania
- Area: approximately 600 m²
- UAV survey date: 11 July 2026
- Weather: clear sky
- Temperature: 24 °C
- Wind speed: approximately 7 km/h
- UAV data: RGB imagery

## Objectives

The main objectives of the project were:

- to generate photogrammetric products from UAV imagery;
- to identify and characterize individual trees;
- to estimate tree height using two different approaches;
- to calculate canopy area;
- to derive RGB vegetation indices, GLI and VARI;
- to investigate relationships between tree characteristics and vegetation indices;
- to analyze the spatial distribution of the calculated indices using IDW interpolation;
- to produce thematic maps for the study area.

## Methodology

The workflow included:

1. UAV image acquisition;
2. photogrammetric processing;
3. generation of orthophoto, DSM and DTM products;
4. creation of a Canopy Height Model (CHM);
5. digitization of individual tree crowns;
6. estimation of tree height using two methods;
7. calculation of GLI and VARI from RGB imagery;
8. statistical analysis of the obtained variables;
9. spatial interpolation using IDW;
10. production of thematic maps and interpretation of the results.

## Results

The analysis produced:

- individual tree measurements;
- canopy area estimates;
- tree height estimates;
- GLI and VARI values for individual trees;
- statistical relationships between tree characteristics and vegetation indices;
- thematic maps of tree height and species;
- interpolated GLI and VARI surfaces.

## Tools

- QGIS
- WebODM
- Microsoft Excel
- UAV RGB imagery
- Photogrammetric products: orthophoto, DSM and DTM

## Project Documentation

The complete project report is available in the `documentation` folder.

## Future Development

The current project represents a foundation for further development. Possible extensions include the use of multispectral imagery, automated geospatial analysis with Python, 3D analysis of photogrammetric point clouds and the development of more advanced decision-support workflows.

## Author

**Daria Sicaru**  
Applied Informatics in Environmental Engineering
