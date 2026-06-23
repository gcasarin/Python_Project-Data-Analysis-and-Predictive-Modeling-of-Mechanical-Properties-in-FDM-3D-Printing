# Python_Project-Data-Analysis-and-Predictive-Modeling-of-Mechanical-Properties-in-FDM-3D-Printing


### Table of Contents

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Libraries Used](#libraries-used)
- [Data Analysis](#data-analysis)
- [Data Predicition](#data-prediction)
- [Conclusions](#conclusions)



### Project Overview

This study uses the "3D Printer Dataset for Mechanical Engineers" to investigate relationships between FDM printing parameters and the mechanical properties of PLA and ABS printed specimens. Statistical analysis, correlation assessment, and predictive models are developed to estimate surface roughness and tensile strength.





### Data Sources

This study uses the "3D Printer Dataset for Mechanical Engineers" from Kaggle ([Kaggle Dataset link](https://www.kaggle.com/datasets/afumetto/3dprinter/data?select=data.csv)), containing experimental data from PLA and ABS specimens produced with an Ultimaker S5 FDM printer under different process settings.


### Tools

- Python - Data Cleaning, Exploratory Data Analysis, Data Visualisation, Machine learning



### Libraries Used

- Pandas
- Numpy
- Matplotlib
- Seaborn
- Scikit-Learn



### Data Analysis

The data analysis was conducted on a dataset of 50 FDM-printed specimens, including 25 ABS samples (15 with *grid* infill pattern and 10 *honeycomb*) and 25 PLA samples (10 *grid* and 15 *honeycomb*). 

An exploratory analysis of the printing parameters highlighted consistent settings for layer height, bed temperature, print speed, and fan speed across materials, while nozzle temperature and infill density were adjusted according to material-specific requirements.

The univariate analysis of mechanical test results showed that PLA generally achieved better performance than ABS, exhibiting higher tensile strength and approximately 30% lower surface roughness. The influence of the infill pattern (grid or honeycomb) was found to be limited across all measured responses, including roughness, tensile strength, and elongation, although PLA appeared more sensitive to pattern selection in terms of surface finish.

Correlation analysis revealed several significant relationships between process parameters and mechanical properties. Layer height showed a strong positive correlation with surface roughness (r ≈ 0.8), indicating that larger layer heights lead to poorer surface quality. Tensile strength increased with both wall thickness (r ≈ 0.4) and infill density (r ≈ 0.36), confirming the positive effect of structural reinforcement on mechanical resistance. Material-dependent behaviors were also observed: PLA tensile strength was more sensitive to infill density, whereas ABS strength was more influenced by wall thickness. 
Finally, elongation exhibited a moderate negative correlation with nozzle temperature and layer height (r ≈ -0.53) in ABS, highlighting a different thermomechanical responses compared to PLA which showed a slight positive correlation with both parameters.
  


### Analysis Results 


