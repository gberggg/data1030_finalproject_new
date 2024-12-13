
# Project overview

This project, completed for the Brown U course DATA1030, explores ML calibration schemes for a low-cost NO2 sensor that is part of the Breathe Providence monitoring network. Low-cost electrochemical gas measurements are biased by meteorological factors (such as temperature) and pollutant cross-sensitivities. Sensors can also drift over time. The objective of this project to improve the accuracy of a Breathe Providence low-cost sensor co-located with a reference measurement. The low-cost sensor is an Alphasense NO2-B434 and it is co-located at the East Providence, RI reference site at Myron J. Francis Elementary. 

# Packages
Python version 3.12.5; 
numpy version 1.26.4; 
matplotlib version 3.9.2; 
sklearn version 1.5.1; 
pandas version 2.2.2; 
xgboost version 2.1.1; 
shap version 0.45.1; 
plotly version 5.23.0; 
scipy version 1.14.1 

# Data

Features: I accessed raw hourly measurements from the co-located Breathe Providence Alphasense sensor (NO2, NO, O3) and BME sensor (T, RH) for 2023. Target: hourly NO2 measurements from the East Providence site accessed via the EPA Air Quality System for 2023. 

# Approach

Missing data (all features, 1.6%) are due to the low-cost sensor being unplugged or losing power. This project tests three types of interpolation (linear, quadratic, and spline) to fill in missing data and the uncertainty introduced by these approaches is assessed. A time counter was also added as a feature to account for drift. For preprocessing, interaction terms were generated for the original 6 features. All features were then standard scaled. A splitter was created that stratifies on decile bins of the target variable, and Kfold cross validation was used across 5 random states. Root Mean Squared Error (RMSE) was used as the evaluation metric for 5 models: ordinary least squares, ridge regression, random forest, XGBoost, and nearest neighbors. 

# Results
XGBoost outperformed all other models, with an average test set RMSE ranging from 1.19 - 1.3 ppb across interpolation methods. R^2 was 0.95 - 0.96 across interpolation methods. At high temperatures, when the low-cost sensor is known to be biased, XGBoost continued to outperform all other models. 

# Future work
In the future I hope to evaluate model performances across seasons, where features vary due to changing meteorology and emission sources. I also hope to explore methods of calibrating field sensors, using the results from this project as one step of the process.  

