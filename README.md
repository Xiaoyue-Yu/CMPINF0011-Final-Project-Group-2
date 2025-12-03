# CMPINF0011-Final-Project-Group-2



##### Team name：
xxx


##### Team members and their email addresses：

* Xiaoyue Yu - xiy249@pitt.edu
* Boyi Sun - bos69@pitt.edu
* Liangyu Zhao



##### Canvas group number：

Group 2



##### A one-sentence overview of the repository：

This repository contains the work for CMPINF 0011 Final Project - Group 2, where we analyze data to determine the best neighborhood in Pittsburgh using various datasets and metrics.

##### Overall Metric

Our team's overarching metric is to find the "Best Neighborhood for Retirement". We are combining three sub-metrics to determine this:

Safety: (Low crime incidents)

Infrastructure:

Air Condition: Air Quality Cleanliness(AQI per site)

Individual Analysis & Datasets
As required, each team member's individual analysis is in the personal_notebooks folder.

1. Xiaoyue Yu - Safety Analysis
Notebook: personal_notebooks/xiaoyue_analysis.ipynb

- Sub-metric: Safety, measured by the number of police-reported crime incidents.
- Dataset: Monthly Criminal Activity (2024-2025)
- File Used: data/2024-October 31, 2025 Monthly Criminal Activity Dataset.xlsx

Work Completed (Check-in):

- Loaded the 2024-2025 Monthly Criminal Activity dataset using pandas.
- Performed data cleaning and verification.
- Calculated the total number of crime incidents for every neighborhood.

Generated two visualizations:

- Top 20 neighborhoods with the most crime incidents (least safe).
- Top 20 neighborhoods with the fewest crime incidents (most safe).

Future Work:

- Normalize Data: The current analysis uses raw counts. I plan to merge this data with a population dataset (like the 2020 Census) to calculate a crime rate per capita. This is a fairer metric, as larger neighborhoods naturally have more incidents.

- Filter Crime Types: Not all crimes are equal for retirees. I will filter the data to focus on specific NIBRS_Offense_Category types (e.g., "Assault Offenses", "Burglary") and exclude minor ones, creating a more targeted "Safety Score".

- Final Metric: Produce a final ranked list of neighborhoods based on this "Safety Score".

Key Findings:

- Crime data shows significant variation across Pittsburgh neighborhoods
- Some neighborhoods consistently show lower crime rates making them potentially safer for retirees
- Data normalization will provide more accurate safety assessments
- Filtering by crime type will help focus on safety concerns most relevant to retirees

2. Liangyu Zhao - Air Condition Analysis
Notebook: personal_notebooks/Murphy_analysis.ipynb

- Sub-metric: Air Quality Cleanliness (daily), using each site’s worst-of-day AQI (the maximum AQI across pollutants per day) as that day’s overall exposure.
- Dataset: Daily Air Condition (2024–2025)
- File Used:    data/2024-October 31, 2025 Monthly Criminal Activity Dataset.xlsx
                (Mapping) Official neighborhood boundaries: data/Neighborhoods_.shp

Methodology:

- Time window: 2024-01-01 → 2025-10-31 (right-open at 2025-11-01).
- Cleaned and verified fields; standardized column names.
- Daily aggregation: for each site × day, take the maximum AQI across pollutants as the daily aqi.
- Site-level metrics:
        median_daily_aqi (typical exposure, lower is better), 
        p90_daily_aqi (tail/peak risk, lower is better),
        healthy_rate (share of days with AQI ≤ 100, higher is better)
- Scoring (BNAS, 0–100): Min–Max normalization on the three metrics with weights:
        median 0.6, p90 0.3, healthy-rate 0.1
        Inverted scaling for median/p90 (lower → higher score), positive scaling for healthy-rate.
- Neighborhood level: assign each neighborhood the score of its nearest monitor.

<<<<<<< Updated upstream
<<<<<<< Updated upstream
Generated two visualizations:

- Air Quality Ranking by Site (daily) for 2024–2025.
- 
=======

Results:
>>>>>>> Stashed changes

=======

Results:

>>>>>>> Stashed changes
- Ranking table: personal_notebooks/outputs/air_quality_site_metrics_daily_2024_2025.csv
- Ranking chart: personal_notebooks/outputs/site_air_quality_ranking_daily_2024_2025.png
- Neighborhood map: personal_notebooks/outputs/neighborhood_air_quality_map.png
- The notebook includes an auto-render Key Findings cell that prints the current top site and stats (BNAS, Median, P90, Healthy-day share) after execution, ensuring text stays consistent with tables/plots.

Key Findings:

- Air quality varies substantially across sites; top sites generally show lower typical exposure and a higher share of healthy days.
- Using worst-of-day AQI ensures peaks in any pollutant are reflected in the daily exposure and final score.
<<<<<<< Updated upstream
=======

### 3. Boyi Sun - Infrastructure Analysis

- Sub-metric: The number of a specific facility in the neighborhood(e.g., park facilities)
- Dataset: City_facilitis_of_Pittsburgh
- File used: `data/City_Facilities_of_Pittsburgh.csv`

Work Completed (Check-in):

- Loaded the city facilities data of Pittsburgh using pandas
- Analyzed the primary users of city facility 
- Counted the facility number and the citipark number by neighborhood respectively
- Visualization :
    - Primary_user of facilities
    - Top 20 neighborhoods by the number of facilities
    - Top 20 neighborhoods by the number of park facilities

Future Work:

- Add a reasonable weight on different type of citypark facilities. For example, give a lager weight to the citypark facilities in the type "senior", making it more reasonable for our overall metric: Best neighborhood for **retirees**.
- Take ertra relavent data into considertaion.
- Exclude the data point that may not be suitable for analysis on a specific population(retirees), such as the facilities in the playgound for the children.

Key Findings:

- The top three primary users in the dataset is `Department of Public Work`, `Citiparks`, and `Department of Public Safety`.
- The number of facilities is varied from neighborhood to neighborhood.
- The number of park facilities is not much different. Adding a weight on different types may make the analysis more strict to retirees.
>>>>>>> Stashed changes


