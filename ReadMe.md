# Exploratory Data Analysis (EDA)

## 1. Introduction

The objective of this analysis is to understand the behavior of weather variables and evaluate the performance of the LDAPS (Local Data Assimilation and Prediction System) model. The focus of this EDA is to identify patterns, relationships, and conditions under which the model produces higher prediction errors.

---

## 2. Data Overview

The dataset consists of meteorological and geographical features such as temperature, humidity, wind speed, cloud cover, precipitation, and terrain-related variables. It also includes LDAPS model predictions and actual observed temperatures for the next day.

Key variables include:

* Present_Tmax and Present_Tmin (current day temperatures)
* LDAPS features (model predictions for weather conditions)
* Next_Tmax and Next_Tmin (target variables)

No missing values were observed in the dataset, indicating clean and reliable data for analysis.

---

## 3. Univariate Analysis

The distribution of Present_Tmax and Present_Tmin shows approximately normal behavior. Most temperature values lie within a moderate range, with no significant outliers.

Humidity variables (LDAPS_RHmin and LDAPS_RHmax) are within the valid range of 0–100%. RHmin follows a near-normal distribution, while RHmax is left-skewed, with most values concentrated at higher humidity levels.

Precipitation variables (LDAPS_PPT1–4) are highly skewed with a large proportion of zero values, indicating that rainfall events are infrequent.

---

## 4. Bivariate and Correlation Analysis

Correlation analysis reveals strong relationships between current and future temperatures:

* Present_Tmax is strongly correlated with Next_Tmax
* Present_Tmin is strongly correlated with Next_Tmin

Humidity variables show a negative relationship with temperature, suggesting that higher humidity is associated with lower temperature values.

Cloud cover and precipitation variables exhibit multicollinearity, indicating redundancy among these features.

---

## 5. Error Analysis of LDAPS Model

To evaluate model performance, error terms were defined as the difference between actual and predicted temperatures.

The error distributions for both Tmax and Tmin are approximately normal, indicating that the errors are mostly random. However, a slight positive bias suggests that the model tends to underestimate temperature values.

Tmax shows a wider spread of errors compared to Tmin, indicating that the model is less stable when predicting maximum temperature.

---

## 6. Error vs Feature Analysis

### 6.1 Error vs Temperature

A clear pattern is observed where prediction error increases with higher temperature values. The model tends to underestimate temperatures at higher ranges, and the variance of error also increases. This indicates the presence of heteroscedasticity.

---

### 6.2 Error vs Humidity

Error also increases with higher humidity levels. Under high humidity conditions, the model shows greater deviation from actual values, suggesting that humidity significantly affects prediction performance.

---

## 7. Feature Engineering Insights

An interaction feature combining temperature and humidity (Temp_Humidity) shows stronger correlation with error compared to individual variables. This indicates that extreme conditions (hot and humid) play a major role in prediction inaccuracies.

On the other hand, temperature range (difference between Tmax and Tmin) shows weak correlation with error, suggesting that daily variation is less important than absolute conditions.

---

## 8. Segmentation Analysis

Temperature values were grouped into categories (Low, Medium, High) to analyze error behavior.

The analysis shows:

* Lowest error in low temperature conditions
* Moderate error in medium range
* Highest error and variability in high temperature conditions

This confirms that the LDAPS model performs poorly under extreme temperature scenarios.

---

## 9. Key Findings

* The dataset is clean with no missing values.
* Temperature variables follow a normal distribution.
* Humidity and precipitation exhibit skewed distributions.
* LDAPS errors are approximately normally distributed but show slight bias.
* Error increases significantly under high temperature and high humidity conditions.
* Interaction between temperature and humidity is a major factor influencing model performance.
* The model exhibits heteroscedasticity, with increasing variance at higher temperatures.

---

## 10. Conclusion

The EDA reveals that the LDAPS model struggles to accurately predict temperatures under extreme weather conditions, particularly when both temperature and humidity are high. The presence of non-linear relationships and increasing error variance suggests that more advanced modeling techniques are required to improve prediction accuracy.

This analysis provides a strong foundation for further modeling and optimization.
