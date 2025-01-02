
![Screenshot 2025-01-02 185203](https://github.com/user-attachments/assets/33a1fdd0-3ced-43cc-804c-421173b34d69)

*Air Quality Analysis: Data Cleaning, PM2.5 Forecasting, and PACF Insights*
---
### Introduction 

This report provides a comprehensive analysis of air quality data, focusing primarily on particulate matter (PM2.5) levels from 2010 to 2018. The objective is to clean and explore the dataset, uncover trends in PM2.5 concentrations, and draw insights from both time series analysis and geographical disparities. The dataset, which contains various air quality indicators and location-specific information, was cleaned to handle missing data and ensure robustness for further forecasting and analysis. 

### Data Cleaning  

#### Dataset Overview  

The dataset comprises 34 columns, capturing a wide range of air quality dimensions:  
- **Indicator-related fields**: Provide context for various air quality metrics (e.g., `IndicatorCode`, `Indicator`).  
- **Location information**: Includes geographic groupings and specific locations (`ParentLocation`, `Location`).  
- **Time-related fields**: Capture data over 2010-2018 (`Period`, `IsLatestYear`).  
- **Dimensional data**: Provide context for measurements (`Dim1`, `Dim2`, `Dim3`).  
- **Miscellaneous metadata**: Includes columns like `Language` and `DateModified`.  

#### Missing Data Analysis  

Initial analysis revealed systematic missingness, particularly in dimensional and measurement columns. A visualisation using a heatmap showed significant gaps (dark bands). The cleaning process addressed these gaps, leading to a dataset with fewer missing values and improved reliability for analysis.  

---

### PM2.5 Concentration (µg/m³): Temporal Trends  

#### Global Trend Observations  

Analysis of average PM2.5 concentration (µg/m³) from 2010 to 2018 revealed:  
- **2010 to 2011**: A peak at ~24.2 µg/m³ due to industrial recovery post-recession.  
- **2012 to 2014**: A decline (~23 µg/m³), attributed to stricter regulations.  
- **2015 to 2016**: A spike (~23.8 µg/m³), driven by urbanisation and seasonal pollution.  
- **2017 to 2018**: A sharp decline (~22.2 µg/m³), reflecting global environmental efforts.  
---
### Disparities in Regional Trends 

Even though the overall global trend shows a decrease in PM2.5 levels, certain continents and countries have experienced rising trends during the same period. These disparities are largely driven by rapid industrialisation, urbanisation, and population growth in specific regions, particularly in developing countries. For example: 

- **South-East Asia and the Eastern Mediterranean** have seen rising PM2.5 levels, primarily due to increased emissions from transportation, industrial activities, and limited implementation of environmental regulations. 

- In contrast, regions like **Europe and the Americas** have demonstrated significant improvements, driven by stringent air quality standards, the adoption of cleaner technologies, and public awareness campaigns. 

This divergence underscores the complexity of global air quality trends and highlights the need for tailored strategies to address regional challenges. 

---

### FactValueNumeric Analysis  

#### Average PM2.5 Concentration (µg/m³) by Area Type  

- **Cities**: Highest (~26 µg/m³), reflecting dense traffic and industrial activities.  
- **Urban areas**: ~24 µg/m³, slightly lower than cities.  
- **Towns and rural areas**: ~23 µg/m³ and ~21 µg/m³, respectively, due to fewer industrial and vehicular emissions.  

#### Lower Bound Analysis (FactValueNumericLow)  

- **Cities**: ~18.5 µg/m³, highest baseline pollution.  
- **Rural areas**: ~14.5 µg/m³, lowest baseline.  

#### Upper Bound Analysis (FactValueNumericHigh)  

- **Cities**: ~40 µg/m³, reflecting peak pollution events.  
- **Rural areas**: ~32 µg/m³, lowest upper bounds.  

These variations underscore urbanisation's role in air quality disparities. 
- **Urbanisation**: the process of making an area more urban.
"he saw nature being destroyed by urbanization"


---

### Regional Analysis  

#### Parent Location Trends  

Average PM2.5 concentration (µg/m³) by region:  
- **Eastern Mediterranean**: ~38 µg/m³, highest due to industrialisation and agriculture.  
- **South-East Asia**: ~32 µg/m³, driven by urbanisation.  
- **Europe and the Americas**: Lowest (~19 µg/m³ and ~15 µg/m³), reflecting regulatory success.  

#### Country-Specific Trends  

- **Highest levels**: Tajikistan (~65 µg/m³), Afghanistan (~58 µg/m³).  
- **Lowest levels**: Peru (~30 µg/m³), driven by lower industrialisation.  

---

### Time Series Analysis  

#### Augmented Dickey-Fuller Test  

Initial tests showed non-stationarity (p > 0.05). After first-order differencing, the series became stationary (p < 0.05).  

#### Seasonal Decomposition  

Four components were extracted:  
- **Observed**: Raw data showed clear trends with minimal seasonality.  
- **Trend**: Highlighted the gradual decline over the years.  
- **Seasonal**: Almost flat, indicating negligible seasonality.  
- **Residuals**: Minimal random noise, validating the trend’s dominance.  

---

### SARIMA Modelling  

#### Global PM2.5 Concentration Forecast  

The SARIMA model used parameters (1,1,0) for ARIMA and (0,0,0,0) for seasonality:  
- **Forecast (2020-2026)**: Predicted a decline from ~22.2 µg/m³ to ~18 µg/m³.  
- **Confidence Intervals**: Widened over time, indicating increasing uncertainty.  

#### Lower Bound PM2.5 Concentration  

- **Historical data**: ~15.8 µg/m³ in 2018.  
- **Forecast**: Decline to ~12 µg/m³ by 2026, with improved stationarity after first-order differencing.  

#### Upper Bound PM2.5 Concentration  

- **Historical data**: ~36 µg/m³ in 2018.  
- **Forecast**: Decline to ~28 µg/m³ by 2026. Second-order differencing achieved better stability.  

---

### Autocorrelation (ACF) and Partial Autocorrelation (PACF) Analysis  

#### ACF Insights  

- **Original data**: Gradual decay of positive correlations, indicating non-stationarity.  
- **Differenced data**: Significant reduction in temporal dependencies, validating stationarity.  

#### PACF Insights  

- **Original data**: Strong positive lag-1 correlation (~0.5).  
- **Differenced data**: Strong negative lag-1 correlation (~-0.35), supporting AR(1) selection.  
- **Upper Bound**: Required second-order differencing, showing intensification of negative correlations for early lags.  

---

### Conclusion  

This analysis revealed substantial temporal and geographical disparities in PM2.5 concentrations. Despite global declines, certain regions exhibit rising trends due to rapid urbanisation and limited regulatory enforcement. SARIMA modelling provided reliable forecasts, but uncertainties remain for long-term predictions.  
While the overall global trend in PM2.5 levels is declining, significant regional disparities remain. Industrialisation and urbanisation are key contributors to rising PM2.5 levels in developing regions like South-East Asia and the Eastern Mediterranean, whereas strict environmental policies and technological advancements have driven improvements in Europe and the Americas. 

The findings underscore the importance of region-specific strategies to address air pollution, as global averages often obscure localised challenges. Moving forward, tailored interventions focusing on high-risk areas can help bridge the gap between global and regional air quality goals, ultimately improving health outcomes and environmental sustainability. 

---

