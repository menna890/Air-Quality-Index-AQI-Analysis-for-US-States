# EPA Air Quality Analysis - Sampling & Statistical Inference

## Overview
This Jupyter notebook provides a comprehensive analysis of EPA air quality data with a focus on sampling techniques, statistical inference, confidence intervals, and hypothesis testing. The analysis examines carbon monoxide measurements across multiple states to help inform regional air quality improvement strategies.

## Dataset
The analysis uses EPA air quality data (`c4_epa_air_quality.csv`) containing carbon monoxide measurements from monitoring sites across the United States.

### Key Features
- **date_local**: Date of measurement (2018-01-01)
- **state_name**: State where monitoring site is located
- **county_name**: County of the monitoring site  
- **city_name**: City of the monitoring site
- **local_site_name**: Specific monitoring station name
- **parameter_name**: Pollutant measured (Carbon monoxide)
- **units_of_measure**: Measurement units (Parts per million)
- **arithmetic_mean**: Mean pollutant concentration
- **aqi**: Air Quality Index value

## Key Findings

### Data Overview
- **Total measurements**: 260
- **Unique states**: 52
- **Most frequent state**: California (66 measurements)
- **Population mean AQI**: 6.76
- **AQI range**: 0 to 50

### Sampling Distribution Analysis
Using the Central Limit Theorem with 10,000 random samples (n=50 each):
- **Mean of sample means**: 6.74 (closely matching population mean of 6.76)
- **Standard error**: 0.74
- The sampling distribution approximates a normal distribution as predicted by CLT

### Confidence Intervals
For **California** (95% confidence level):
- **Sample mean**: 12.12
- **Standard error**: 0.90
- **Margin of error**: 1.76
- **95% Confidence Interval**: (10.36, 13.88)

### Hypothesis Tests

#### Test 1: Los Angeles vs. Rest of California
- **Null hypothesis (H₀)**: No difference in mean AQI between Los Angeles County and rest of California
- **Alternative hypothesis (Hₐ)**: There is a difference
- **Result**: Reject H₀ (p-value = 0.049 < 0.05)
- **Conclusion**: Los Angeles County has significantly different air quality compared to other California counties

#### Test 2: New York vs. Ohio
- **H₀**: Mean AQI of New York ≥ mean AQI of Ohio
- **Hₐ**: Mean AQI of New York < mean AQI of Ohio
- **Result**: Reject H₀ (p-value = 0.030 < 0.05, t-statistic = -2.026)
- **Conclusion**: New York has significantly lower AQI than Ohio

#### Test 3: Michigan Policy Impact Assessment
- **H₀**: Mean AQI of Michigan ≤ 10
- **Hₐ**: Mean AQI of Michigan > 10
- **Result**: Fail to reject H₀ (p-value = 0.940 > 0.05, t-statistic = -1.74)
- **Conclusion**: Insufficient evidence that Michigan's mean AQI exceeds 10; Michigan likely won't be affected by policies targeting states with mean AQI ≥ 10

## Technical Implementation

### Libraries Used
```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import statsmodels.api as sm
from scipy import stats
import seaborn as sns
```

### Key Statistical Methods

1. **Descriptive Statistics**: Mean, standard deviation, frequency counts
2. **Sampling Techniques**: Random sampling with replacement
3. **Central Limit Theorem**: Demonstration with 10,000 sample means
4. **Confidence Intervals**: 95% confidence interval calculation
5. **Hypothesis Testing**: 
   - Two-sample t-tests (independent samples)
   - One-sample t-test
   - Alternative hypothesis testing (less/greater/two-tailed)

## Visualizations
- Box plots comparing AQI distributions across selected states
- Histograms of sampling distributions
- Normal distribution overlay demonstrating CLT

## How to Run

### Prerequisites
- Python 3.x
- Required packages: numpy, pandas, matplotlib, statsmodels, scipy, seaborn

### Installation
```bash
pip install numpy pandas matplotlib statsmodels scipy seaborn
```

### Execution
1. Ensure the dataset file `c4_epa_air_quality.csv` is in the `00-dataset` directory
2. Run the Jupyter notebook cells sequentially
3. Review statistical outputs and visualizations

## Business Implications

### Regional Office Selection
- **New York** shows significantly lower AQI than Ohio, making it a potentially better location for regional operations from an air quality perspective

### Policy Targeting
- **Los Angeles County** stands out as an area with distinct air quality characteristics requiring targeted interventions
- **Michigan** likely falls below the policy threshold (mean AQI < 10) and may not require immediate policy interventions

