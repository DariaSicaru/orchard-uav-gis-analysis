# Orchard UAV GIS Analysis

## Overview

This project presents a GIS-based analysis of a small orchard using RGB imagery acquired by a UAV. The workflow combines photogrammetric processing, GIS analysis, point-cloud processing, RGB vegetation indices and spatial analysis to characterize individual trees and evaluate different approaches for estimating tree height.

The project was developed as a practical study in UAV-based environmental monitoring, photogrammetry, GIS and 3D point-cloud analysis.

A particular focus of the project was the comparison between three different tree-height estimation approaches, using direct field measurements as reference data.

## Study Area and Data

The study area is a private garden in Blejoi, Prahova County, Romania, covering approximately 600 m².

### UAV survey

- **Survey date:** 11 July 2026
- **Survey time:** approximately 11:30
- **Weather:** clear sky
- **Temperature:** approximately 24 °C
- **Wind speed:** approximately 7 km/h
- **Data type:** RGB aerial imagery
- **Flight altitude:** 30 m
- **Camera orientation:** nadir (90°)
- **Target overlap:** approximately 70–72%
- **GSD:** approximately 1 cm

The RGB imagery was processed photogrammetrically to obtain spatial data products used in the subsequent GIS and 3D analysis.

## Objectives

The main objectives of the project were:

- to generate photogrammetric products from UAV RGB imagery;
- to generate and analyze a photogrammetric point cloud;
- to identify and characterize individual trees;
- to estimate tree height using three different approaches;
- to validate the height estimation methods using direct field measurements;
- to calculate canopy area;
- to calculate RGB-based vegetation indices, GLI and VARI;
- to perform selective field validation of trees with pronounced spectral anomalies.
- to investigate relationships between tree characteristics and RGB vegetation indices;
- to analyze the spatial distribution of GLI and VARI;
- to produce thematic maps and interpret the obtained results.

## Methodology

The workflow consisted of the following main stages:

1. UAV image acquisition;
2. photogrammetric processing in WebODM;
3. generation of an orthophoto, DSM, DTM and photogrammetric point cloud;
4. digitization of individual trees in QGIS;
5. estimation of tree height using three different approaches;
6. direct field measurements for validation;
7. classification of the point cloud into ground and non-ground points using the CSF algorithm in CloudCompare;
8. generation of an independent DTM from classified ground points;
9. generation of an independent DSM from the complete point cloud;
10. generation of a CHM from the CloudCompare-derived DSM and DTM;
11. calculation of canopy area;
12. calculation of GLI and VARI from RGB imagery;
13. statistical analysis of the obtained variables;
14. spatial interpolation using the IDW method;
15. production of thematic maps;
16. comparison and interpretation of the results.

## Tree Characterization

A total of 15 individual trees were digitized and analyzed.

For each tree, the analysis included:

- tree ID;
- species;
- canopy geometry;
- estimated height;
- canopy area;
- GLI;
- VARI.

### Tree Height Estimation

Three approaches were evaluated:

#### 1. CHM — WebODM

The first method used the difference between the photogrammetric DSM and DTM:

`CHM = DSM - DTM`

The resulting CHM was used to estimate tree height within the digitized crown polygons.

#### 2. Buffer-DSM

The second method used the maximum DSM elevation within each tree crown.

A surrounding buffer was used to estimate the local ground elevation from the DSM. Tree height was then calculated as the difference between the maximum DSM elevation within the crown and the estimated local ground elevation.

#### 3. CHM — CloudCompare

The third method was based directly on the photogrammetric point cloud.

The point cloud was classified into ground and non-ground points using the Cloth Simulation Filter (CSF) algorithm in CloudCompare.

The classified ground points were used to generate an independent DTM at 0.1 m resolution.

A second raster was generated from the complete point cloud using the maximum Z value within each raster cell, producing an independent DSM.

The difference between the two models was then used to generate a second CHM:

`CHM = DSM_CloudCompare - DTM_CloudCompare`

This workflow provided an independent 3D-derived height estimation approach compared with the products generated automatically by WebODM.

## Field Validation

Direct field measurements were performed to evaluate the accuracy of the three photogrammetric approaches.

Tree heights were measured manually using a tape measure, with an estimated measurement uncertainty of approximately ±10 cm.

The comparison included:

- detection rate;
- RMSE (Root Mean Square Error);
- MAE (Mean Absolute Error);
- mean bias.

A minimum height threshold of 0.3 m was used to determine whether a tree was detected by each method.

For the accuracy metrics, only the 11 trees detected by all three methods were included, ensuring that the methods were compared using the same sample.

## RGB Vegetation Indices

Two vegetation indices based on RGB imagery were calculated:

### GLI — Green Leaf Index

GLI was used to characterize the relative contribution of the green channel in the RGB imagery and to investigate variation in vegetation appearance between individual trees.

### VARI — Visible Atmospherically Resistant Index

VARI was calculated as an additional RGB-based indicator and analyzed in relation to tree characteristics.

The indices were calculated at the individual-tree level using representative mean values for each crown.

The relationships between GLI, VARI and structural characteristics were investigated using descriptive statistics and Pearson correlation.

## Statistical Analysis

The statistical analysis included:

- comparison of the three tree-height estimation methods;
- detection rate for each method;
- RMSE;
- MAE;
- mean bias;
- Pearson correlation between GLI and tree height;
- Pearson correlation between VARI and tree height;
- Pearson correlation between GLI and VARI;
- comparison of mean GLI and VARI values between species.

The height validation showed that the CloudCompare-derived CHM provided the best performance among the three tested approaches for the analyzed dataset.

## Spatial Analysis

Spatial analysis was performed in QGIS.

The project included thematic maps representing:

- tree height;
- tree species;
- GLI;
- VARI.

IDW interpolation was applied to the GLI and VARI values associated with the 15 analyzed trees in order to visualize their estimated spatial distribution across the study area.

The interpolated surfaces were interpreted as exploratory spatial representations rather than direct measurements of vegetation condition.

## Results

The three height estimation methods produced different levels of performance.

| Method | Detection rate | RMSE | MAE | Mean bias |
|---|---:|---:|---:|---:|
| CHM | 73% | 1.85 m | 1.75 m | -1.75 m |
| Buffer-DSM | 80% | 0.55 m | 0.47 m | -0.42 m |
| CHM-CloudCompare | **87%** | **0.40 m** | **0.33 m** | **-0.25 m** |

The CloudCompare-derived CHM achieved both the highest detection rate and the lowest estimation error among the three tested approaches.

The results also showed a systematic tendency toward underestimation for all three methods. The bias was smallest for the CloudCompare-derived CHM.

The comparison demonstrated that direct control over ground/non-ground classification and the independent generation of the DTM and DSM improved the performance of the height estimation workflow for this dataset.

The RGB indices produced values approximately between:

- **GLI:** 0.12–0.27
- **VARI:** 0.10–0.33

Pearson correlation coefficients indicated:

- **GLI vs. tree height:** r = 0.402
- **VARI vs. tree height:** r = 0.672
- **GLI vs. VARI:** r = 0.664

These relationships indicate associations within the analyzed dataset, but the RGB indices were not treated as independent measures of tree health.

Field verification of trees with pronounced spectral anomalies (low GLI/VARI values) revealed observable canopy stress symptoms in two cases. For one tree, severe foliage desiccation and browning were observed, consistent with (though not laboratory-confirmed as) a bacterial disease pattern. For another tree, despite a dense canopy (reflected in a normal GLI value), the foliage showed visible chlorosis, which was reflected specifically in a low VARI value — illustrating that GLI and VARI can respond differently depending on whether the anomaly is structural (canopy density) or biochemical (pigment degradation).

## Project Outputs

The project resulted in:

- UAV RGB imagery;
- photogrammetric orthophoto;
- WebODM DSM and DTM;
- photogrammetric point cloud;
- ground/non-ground classification using CSF;
- CloudCompare-derived DTM;
- CloudCompare-derived DSM;
- CloudCompare-derived CHM;
- spatial database of 15 individual trees;
- tree-height estimates using three different methods;
- direct field measurements;
- quantitative validation results;
- GLI and VARI values;
- statistical analysis;
- thematic maps;
- IDW interpolation maps for GLI and VARI;
- final project documentation.

### Documentation

The complete project report is available in the [documentation](documentation/) folder.

### Maps

The final thematic and interpolation maps are available in the [maps](maps/) folder.

### Results

The statistical analysis, field measurements and comparison of the three height estimation methods are available in the [results](results/) folder.

## Tools and Technologies

- QGIS
- CloudCompare
- WebODM
- Microsoft Excel
- UAV RGB imagery
- Photogrammetry
- Point-cloud processing
- CSF ground classification
- Raster analysis
- GIS spatial analysis
- IDW interpolation

## Limitations and Future Development

The project is based exclusively on RGB imagery and therefore does not provide direct multispectral information.

The validation dataset consisted of 15 trees, with accuracy metrics calculated on the 11 trees detected by all three methods. Field measurements were performed manually and have an estimated uncertainty of approximately ±10 cm.

The photogrammetric reconstruction also presented limitations for small, sparse or partially reconstructed tree crowns. Such cases resulted in low or missing height estimates for some trees.

The GLI and VARI analyses were primarily exploratory. For trees with notably low index values, field verification was performed to assess whether the spectral anomaly corresponded to an observable biological condition. This verification was selective (performed only for trees with clear spectral anomalies), not systematic across all 15 trees; consequently, the possibility of undetected anomalies or false positives among the remaining trees cannot be excluded. Any biological interpretations (e.g., suspected disease symptoms) are based on macroscopic field observation only, without laboratory confirmation, and should be considered indicative rather than diagnostic.
Future development could include:

- multispectral UAV imagery;
- LiDAR data integration;
- automated point-cloud classification;
- 3D analysis of individual tree crowns;
- automated extraction of tree characteristics;
- Python-based geospatial processing;
- integration of environmental sensor measurements;
- development of advanced decision-support workflows.

## Author

**Daria Sicaru**  
Applied Informatics in Environmental Engineering
