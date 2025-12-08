# CMPINF0011-Final-Project-Group-2: Best Neighborhood in Pittsburgh for Retirement

## Team Information
**Team Name:** Jet2Holiday ✈

**Team Members:**
* Xiaoyue Yu - xiy249@pitt.edu
* Liangyu Zhao - liz294@pitt.edu
* Boyi Sun - bos69@pitt.edu

**Canvas Group Number:** Group 2

## Project Overview
This repository contains the final project for CMPINF 0011 - Group 2. We utilized data analysis techniques on multiple datasets from the Western Pennsylvania Regional Data Center (WPRDC) to quantitatively determine the **"Best Neighborhood for Retirees"** in Pittsburgh.

## Overall Metric
To accurately rank neighborhoods for retirement suitability, we established a composite index integrating three weighted sub-metrics:

1.  **Safety (Security):** Low crime rates, specifically focusing on crimes affecting the elderly.
2.  **Infrastructure (Convenience):** Availability of facilities relevant to seniors (parks, centers).
3.  **Air Quality (Health):** Clean air metrics based on AQI data.

---

## Individual Analysis & Implementation

### 1. Xiaoyue Yu - Safety Analysis
* **Notebook:** `personal_notebooks/xiaoyue_analysis.ipynb`
* **Dataset:** Monthly Criminal Activity (2024-2025) & 2020 Census Population
* **Methodology Implemented:**
    * **Data Cleaning:** Standardized neighborhood names to ensure accurate merging with population data.
    * **Filtering:** Filtered out minor offenses to focus on "Serious Crimes" that impact retirees' sense of safety (e.g., Assault, Burglary, Robbery).
    * **Normalization:** Calculated **Crime Rate per 1000 people** using 2020 Census data to correct for population size bias.
    * **Scoring:** Converted crime rates into a **Safety Index (0-100)** using Z-Score standardization, where a higher score indicates a safer neighborhood.

### 2. Liangyu Zhao - Air Quality Analysis
* **Notebook:** `personal_notebooks/Murphy_analysis.ipynb`
* **Dataset:** Daily Air Condition (2024–2025)
* **Methodology Implemented:**
    * **Aggregation:** Computed daily statistics (Median, P90) per monitoring site.
    * **Scoring Model:** Developed a composite "BNAS Score" (0-100) combining median daily AQI (50%), P90 spikes (30%), and healthy day rate (20%).
    * **Mapping:** Mapped monitoring site data to surrounding neighborhoods to assign air quality scores to specific residential areas.

### 3. Boyi Sun - Infrastructure Analysis
* **Notebook:** `personal_notebooks/BoyiSun_Analysis.ipynb`
* **Dataset:** City Facilities of Pittsburgh
* **Methodology Implemented:**
    * **Categorization:** Analyzed primary users of facilities and filtered for amenities relevant to retirees (e.g., Senior Centers, Citiparks).
    * **Weighting:** Applied weights to different facility types to prioritize those most beneficial for "senior" living.
    * **Scoring:** Calculated the density of facilities per neighborhood and normalized the data to produce a final Infrastructure Score.

---

## Final Data Integration & Methodology

The final integration is performed in `combined_notebook.ipynb`. To combine our three distinct sub-metrics into a single ranking, we employed a scientific weighting method rather than a simple average.

### 1. Analytic Hierarchy Process (AHP)
We used the AHP method to determine the weights for our three sub-metrics. Based on academic literature regarding the hierarchy of needs for the elderly (Acierno et al., WHO, Simoni et al.), we established the following priorities:
* **Safety** is the most critical fundamental need.
* **Infrastructure** is essential for daily mobility and activity.
* **Air Quality** is a long-term health factor but secondary to immediate physical safety.

### 2. Weighting Result
Based on our judgment matrix, the final calculated weights are:
* **Safety:** ~58.16%
* **Infrastructure:** ~30.90%
* **Air Quality:** ~10.95%

*(Consistency Ratio CR = 0.0032 < 0.1, confirming the matrix is logically consistent)*

### 3. Final Calculation
The final score for each neighborhood is calculated as:
$$Total Score = (0.5816 \times Safety Score) + (0.3090 \times Infrastructure Score) + (0.1095 \times Air Score)$$

---

## Conclusion

After analyzing data across all Pittsburgh neighborhoods, applying population normalization, and weighting based on retiree priorities:

**The Top Neighborhoods for Retirement in Pittsburgh are:**
*(See `outputs/Ranked_Neighborhoods_Pittsburgh.csv` for the full list)*

1.  **1st: Polish Hill**
2.  **2nd: Lincoln-Lemington-Belmar**
3.  **3rd: Perry North**

**Why they won:**
These neighborhoods achieved the highest composite scores because they offer the optimal balance of **high safety** (which carries the most weight) and **abundant community infrastructure**. While Air Quality varies, the dominant factors of low crime rates per capita and access to senior-friendly facilities make these areas the most suitable choices for retirement living in Pittsburgh.

---
*Data Source: [Western Pennsylvania Regional Data Center (WPRDC)](https://data.wprdc.org/)*