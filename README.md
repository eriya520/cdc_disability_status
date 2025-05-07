# cdc_disability_status
This repo explore hidden correlations of disability prevalnce across different demographic groups via data analysis, and attempt to deveop multiclassifier model to predict both disability status and types based on demographic groups. The goal is to provide insights which enable policymakers, healthcare providers and advocacy organizations to tailor interventions, allocate resources more effectively, and design support services that address the specific challenges faced by different populations. 

# Data source
- Used Data published by CDC  `DHDS - Prevalence of Disability Status and Types by Demographic Groups, 2021` last updated on Jan. 29, 2025
- link: https://data.cdc.gov/Disability-Health/DHDS-Prevalence-of-Disability-Status-and-Types-by-/qjg3-6acf/about_data

# What's included in the repo?
- course_project.ipynb : notebook to data loading, processing, EDA and visualization, model selection and evaluation, feature importance
- cdc_2021_preventative_disability_status_type_demographic_data_one_hot_encoded.csv : meta data including `data_value`, `locationid` and one-hot-encoded features from `responseid`, `indicatorid`; null values in `data_value` are dropped; highly correlated binary features such as in sex, age and veteran status dropped one for each.
- Features in `cdc_2021_preventative_disability_status_type_demographic_data_one_hot_encoded.csv':
  - 'locationid', unique state/regions ID please refer to the cdc description
  - 'data_value', disabiliy prevalance in % 
  - 'stratificationid1_COGDIS', cognitive disability; binary in numeric(0/1 as in False/True)
  - 'stratificationid1_DISABL', any disability; binary in numeric(0/1 as in False/True)
  - 'stratificationid1_HEARDIS', hearing disability, binary in numeric(0/1 as in False/True)
  - 'stratificationid1_INDDIS',indepedent living disability, binary in numeric(0/1 as in False/True)
  - 'stratificationid1_MOBDIS', mobility disability, binary in numeric(0/1 as in False/True)
  - 'stratificationid1_SELFDIS',self care disability, binary in numeric(0/1 as in False/True)
  - 'stratificationid1_VISDIS', vision disability, binary in numeric(0/1 as in False/True)
  - 'responseid_AGE01', age 18-44, binary in numeric(0/1 as in False/True)
  - 'responseid_AGE03', age 65+, binary in numeric(0/1 as in False/True)
  - 'responseid_RACE01',White, non-Hispanic, binary in numeric(0/1 as in False/True)
  - 'responseid_RACE02',Black, non-Hispanic ,binary in numeric(0/1 as in False/True)
  - 'responseid_RACE03',Hispanic,binary in numeric(0/1 as in False/True)
  - 'responseid_RACE04',Other / Multirace, non-Hispanic,binary in numeric(0/1 as in False/True)
  - 'responseid_RACE05',Asian, non-Hispanic ,binary in numeric(0/1 as in False/True)
  - 'responseid_RACE06',Native Hawaiian or Other Pacific Islander, non-Hispanic,binary in numeric(0/1 as in False/True)
  - 'responseid_RACE07',American Indian or Alaska Native, non-Hispanic  ,binary in numeric(0/1 as in False/True)
  - 'responseid_SEX02', female,binary in numeric(0/1 as in False/True)
  - 'responseid_VET2', veteran, binary in numeric(0/1 as in False/True)
  - 'indicatorid_AGEIND',Disability status and types by age , binary in numeric(0/1 as in False/True)
  - 'indicatorid_RACEIND',Disability status and types by race/ethnicity , binary in numeric(0/1 as in False/True)
  - 'indicatorid_SEXIND', Disability status and types by sex , binary in numeric(0/1 as in False/True)
  - 'indicatorid_VETIND', Disability status and types by veteran status, binary in numeric(0/1 as in False/True)
 
 # Conclusion
 Through data anlysis, we observed some interesting trends:
 * **Age**:
    * Older adults have significantly higher disability rates compared to younger age groups. 
* **Race/Ethnicity**:
    * Some racial groups, including American Indian or Alaska Native and Other/Multirace, have higher disability prevalence. 
* **Socioeconomic Factors**:
    * Individuals with lower education levels and from minority racial backgrounds may experience higher disability severity. 
* **Sex**:
    * Women may be more likely to experience certain types of disabilities compared to men. 
* **Disability Types**:
    * Common types include difficulties with walking or mobility, independent living (errands alone), and cognitive difficulties.
* We have siginificantly less data for Asian and Native Hawaiian groups, which is likely due to being minority in US.

- The multiclassifier Random Forest classifier can predict disability status with 0.9 F1 score, but performs poorly in predicting disability types.
