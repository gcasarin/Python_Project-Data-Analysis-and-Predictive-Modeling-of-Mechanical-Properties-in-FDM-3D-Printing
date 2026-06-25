# Python_Project-Data-Analysis-and-Predictive-Modeling-of-Mechanical-Properties-in-FDM-3D-Printing

### Table of Contents

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Libraries Used](#libraries-used)
- [Data Analysis](#data-analysis)
- [Data Predicition](#data-prediction)


### Project Overview


This study uses the "3D Printer Dataset for Mechanical Engineers" to investigate relationships between FDM printing parameters and the mechanical properties of PLA and ABS printed specimens. Statistical analysis, correlation assessment, and predictive models are developed to estimate surface roughness and tensile strength.

<p align="center">
  <img src="https://github.com/gcasarin/Python_Project-Data-Analysis-and-Predictive-Modeling-of-Mechanical-Properties-in-FDM-3D-Printing/blob/main/Project_charts/1.png" width="">
</p>

Link to the Project Notebook: [click here⮕](https://github.com/gcasarin/Python_Project-Data-Analysis-and-Predictive-Modeling-of-Mechanical-Properties-in-FDM-3D-Printing/blob/main/Data-Analysis-and-Predictive-Modeling-of-Mechanical-Properties-in-FDM-3D-Printing.ipynb)


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

<p align="center">
  <img src="https://github.com/gcasarin/Python_Project-Data-Analysis-and-Predictive-Modeling-of-Mechanical-Properties-in-FDM-3D-Printing/blob/main/Project_charts/2.png" width="45%" />
  <img src="https://github.com/gcasarin/Python_Project-Data-Analysis-and-Predictive-Modeling-of-Mechanical-Properties-in-FDM-3D-Printing/blob/main/Project_charts/3.png" width="45%" />
</p>

The univariate analysis of mechanical test results showed that PLA generally achieved better performance than ABS, exhibiting higher tensile strength and approximately 30% lower surface roughness. The influence of the infill pattern (grid or honeycomb) was found to be limited across all measured responses, including roughness, tensile strength, and elongation, although PLA appeared more sensitive to pattern selection in terms of surface finish.

<p align="center">
  <img src="https://github.com/gcasarin/Python_Project-Data-Analysis-and-Predictive-Modeling-of-Mechanical-Properties-in-FDM-3D-Printing/blob/main/Project_charts/4.png" width="45%" />
  <img src="https://github.com/gcasarin/Python_Project-Data-Analysis-and-Predictive-Modeling-of-Mechanical-Properties-in-FDM-3D-Printing/blob/main/Project_charts/5.png" width="45%" />
</p>

Correlation analysis revealed several significant relationships between process parameters and mechanical properties. Layer height showed a strong positive correlation with surface roughness (r ≈ 0.8), indicating that larger layer heights lead to poorer surface quality. 

<p align="center">
  <img src="https://github.com/gcasarin/Python_Project-Data-Analysis-and-Predictive-Modeling-of-Mechanical-Properties-in-FDM-3D-Printing/blob/main/Project_charts/8.png" width="500">
</p>

Tensile strength increased with both wall thickness (r ≈ 0.4) and infill density (r ≈ 0.36), confirming the positive effect of structural reinforcement on mechanical resistance. Material-dependent behaviors were also observed: PLA tensile strength was more sensitive to infill density, whereas ABS strength was more influenced by wall thickness. 

<p align="center">
  <img src="https://github.com/gcasarin/Python_Project-Data-Analysis-and-Predictive-Modeling-of-Mechanical-Properties-in-FDM-3D-Printing/blob/main/Project_charts/6.png" width="600">
</p>

Finally, elongation exhibited a moderate negative correlation with nozzle temperature and layer height (r ≈ -0.53) in ABS, highlighting a different thermomechanical responses compared to PLA which showed a slight positive correlation with both parameters.
  


### Data Prediction 

Predictive modeling was performed to estimate surface roughness and tensile strength from FDM printing parameters. 

1. For **surface roughness prediction**, an easy-to-use *linear regression model* was developed using the most relevant features identified during the correlation analysis (*layer height, nozzle temperature, wall thickness, and material type*). 

   <p align="center">
     <img src="https://github.com/gcasarin/Python_Project-Data-Analysis-and-Predictive-Modeling-of-Mechanical-Properties-in-FDM-3D-Printing/blob/main/Project_charts/10a.png" width="600">
   </p>
  
   The model trained on the single fold achieved good predictive performance (*R² = 0.81*), indicating that roughness can be effectively explained by a limited set of process parameters. The results, as you can see from the predictive linear equation below, confirmed layer height and nozzle temperature are the most influential variables.
  
   <p align="center">
     <img src="https://github.com/gcasarin/Python_Project-Data-Analysis-and-Predictive-Modeling-of-Mechanical-Properties-in-FDM-3D-Printing/blob/main/Project_charts/10.png" width="800">
   </p>
   <p align="center">
     <img src="https://github.com/gcasarin/Python_Project-Data-Analysis-and-Predictive-Modeling-of-Mechanical-Properties-in-FDM-3D-Printing/blob/main/Project_charts/10b.png" width="900">
   </p>

   However, *k-fold cross-validation revealed a significant reduction in performance*, suggesting **limited model generalization due to the small dataset size** (50 observations).


2. To **predict tensile strength**, a *Random Forest Regressor* was implemented in order to capture nonlinear relationships and interactions among process parameters. The model was trained using a reduced set of features, including layer height, wall thickness, infill density, nozzle temperature, material, and infill pattern.

   <p align="center">
     <img src="https://github.com/gcasarin/Python_Project-Data-Analysis-and-Predictive-Modeling-of-Mechanical-Properties-in-FDM-3D-Printing/blob/main/Project_charts/11a.png" width="720">
   </p>
  
   <p align="center">
     <img src="https://github.com/gcasarin/Python_Project-Data-Analysis-and-Predictive-Modeling-of-Mechanical-Properties-in-FDM-3D-Printing/blob/main/Project_charts/11b.png" width="720">
   </p>
  
   The obtained performance (*R² = 0.55 and MAE ≈ 5 MPa*) indicates a **moderate predictive capability, explaining approximately 55% of the variability in tensile strength**.
  
   Despite the limited amount of available data, repeated k-fold validation demonstrated good **model stability**, suggesting that the approach provides a *promising basis for future improvements with larger datasets*.


