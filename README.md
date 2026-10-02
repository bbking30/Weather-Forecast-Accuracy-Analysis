# Weather Forecast Accuracy Analysis

A statistical analysis of weather forecast accuracy using regression and classification methods. This project examines factors associated with temperature prediction error and investigates conditions under which weather forecasts are more likely to be inaccurate.

## Project Overview

Weather forecasting is inherently challenging due to the complexity and variability of atmospheric systems. This project uses historical weather forecast data from multiple cities and states in the United States to investigate factors that influence forecast accuracy.

The analysis focuses on three research questions:

1. Does forecast lead time affect temperature prediction error?
2. Which observed variables influence the forecast outlook?
3. What factors predict when a forecast has a large error (>5°F)?

The project applies linear regression, multinomial classification, and logistic regression to examine these questions.

## Dataset

The dataset, weathers.csv, contains weather forecast and observation data collected between January 30, 2021 and June 1, 2021 across multiple U.S. cities and states.

### Relevant variables include:

* Forecast temperature
* Observed temperature
* Forecast lead time
* Observed precipitation
* Forecast outlook
* High/low temperature designation
* Location information
* Potential sources of forecast error

During preprocessing, missing values and duplicate records were removed, dates were standardized, categorical text variables were cleaned, and temperature prediction error features were constructed.

## Research Questions & Methods

1. Forecast Lead Time and Temperature Error

   Question: Does forecast lead time affect temperature prediction error?

   Temperature error was defined as: temperature error = observed temperature - forecast temperature

   A simple linear regression was used to model temperature error as a function of forecast lead time.

   The analysis found no statistically significant linear relationship between forecast lead time and temperature error in this dataset (p = 0.471).

2. Forecast Outlook Classification

   Question: How do observed features affect the forecast outlook?

   A multinomial classification model was used to predict forecast outlook from:

   * High/low temperature designation
   * Forecast lead time
   * Observed temperature
   * Forecast temperature
   * Observed precipitation
   
   Categorical predictors were converted to indicator variables, predictors were standardized, and light L1 regularization was applied. The resulting model achieved a pseudo-(R^2) of 0.1598.

   The analysis found that some observed features helped distinguish clearly different weather conditions, while distinguishing between similar conditions such as rain, showers, and thunderstorms was more difficult.

3. Predicting Large Forecast Errors

   Question: What factors predict when a forecast has a large error (>5°F)?

   A binary outcome was created:
   * large error = 1 if |temperature error| > 5°F
   * large error = 0 otherwise

   A logistic regression model was then used with:
   * Forecast lead time
   * Forecast temperature
   * Forecast outlook
   * High/low designation
   * State
   
   The model achieved:
   * Accuracy: 0.625
   * Precision: 0.135
   * Recall: 0.623
   * F1 Score: 0.221
   * ROC-AUC: 0.673
   * PR-AUC: 0.157

   Because large forecast errors were relatively uncommon, recall was emphasized when evaluating the model’s ability to identify large errors.

   The analysis found that longer forecast lead times, certain complex weather conditions, and geographic differences were associated with a higher likelihood of large forecast errors.

## Key Findings

Overall, the analysis suggests that forecast accuracy is influenced by a combination of environmental and contextual factors rather than a single predictor.

### Key observations include:

* Forecast lead time alone did not show a statistically significant linear relationship with temperature error.
* Forecast lead time was associated with a higher likelihood of large errors in the logistic regression analysis.
* Certain weather conditions were more difficult to classify or predict accurately.
* Geographic differences were associated with variation in the likelihood of large forecast errors.
* The classification model had more difficulty distinguishing between similar weather conditions than clearly different conditions.
* Additional features and more nuanced modeling approaches could potentially improve predictive performance.


## Authors

* Thomas Hyunh
* Sarju Patel
* Brooks Kahsai
* Ethan Tandio

## Course

STAT 391 — Final Project
March 18, 2026

## Reference

Harmon, Jon. weather forecasts.csv. GitHub, 20 Dec. 2022.
