# MIST 4610 Project 2

# Team Name
47114 Group 7

## Team Members:
- Leif Hurdal ([@leifhurdal](https://github.com/leifhurdal))
- Amy Morales ([@amymorales](https://github.com/amyfrmorales))
- Dung Nguyen ([@dungnguyen](https://github.com/den50791))
- Vivian Pham ([@vivianpham](https://github.com/vivianxpham))
- Ben Williams ([@benwilliams](https://github.com/bendeanwilly))

## Dataset Description:

### Dataset 1: California Hospital Performance Ratings
  - **Source**: [Data.gov/Dataset1](https://catalog.data.gov/dataset/california-hospital-performance-ratings-91d9b/resource/7ac54225-fb51-40c3-b2fb-9979a4bbc620)  
  - **Dimensions**: 25974 rows X 13 columns
  
  - **Columns**: 
  
    - Year: Year of the performance rating data.
    - County: County where the hospital is located.
    - Hospital: Name of the hospital.
    - OSHPD-ID: Identifier for the hospital from OSHPD (Office of Statewide Health Planning and Development).
    - System: Type of healthcare system the hospital belongs to.
    - Type of Report: Type of performance report.
    - Performance Measure: Specific measure of hospital performance being reported.
    - Number of Adverse Events: Number of adverse events recorded.
    - Number of Cases: Number of cases or procedures evaluated.
    - Risk-Adjusted Rate: Performance rate adjusted for risk factors.
    - Hospital Ratings: Rating assigned to the hospital based on performance.
    - Longitude: Longitude coordinates of the hospital location.
    - Latitude: Latitude coordinates of the hospital location.
  
  - **Data Types**: Numeric (Integer), Text (String), and Numeric (Float)

### Dataset 2: California Hospital Inpatient Mortality Rates and Quality Ratings
  - **Source**: [Data.gov/Dataset2](https://catalog.data.gov/dataset/california-hospital-inpatient-mortality-rates-and-quality-ratings-c11e9)  
  - **Dimensions**: 53216 rows X 11 columns
  
  - **Columns**:
  
    - Year: Year of the mortality rate and quality rating data.
    - County: County where the hospital is located.
    - Hospital: Name of the hospital.
    - OSHPD-ID: Identifier for the hospital from OSHPD (Office of Statewide Health Planning and Development).
    - Procedure/Condition: Medical procedure or condition evaluated for mortality rate.
    - Risk-Adjusted Mortality Rate: Mortality rate adjusted for risk factors. The Risk-Adjusted Mortality Rates (RAMR) presented here adjusts the observed mortality rates. This statistical methodology takes into account preexisting health problems that put some patients at greater risk of death to “level the playing field” and allow fair comparisons across hospitals.
    - Number of Deaths: Number of deaths recorded for the procedure/condition.
    - Number of Cases: Number of cases or procedures evaluated.
    - Hospital Ratings: Rating assigned to the hospital based on quality metrics.
    - Longitude: Longitude coordinates of the hospital location.
    - Latitude: Latitude coordinates of the hospital location.
    
  - **Data Types**: Numeric (Integer), Text (String), and Numeric (Float)

### Dataset 3: Poverty Across California
  - **Source**: [ppic.org](https://www.ppic.org/data-set/poverty-across-california/)  
  - **Dimensions**: 60 rows X 2 columns

  - **Columns**: 
    - County: Name of the county.
    - CPM Poverty Rating: Poverty rating based on the County.
  
  - **Data Types**: Text (String) and Float (Decimal)

## Team Questions:

1. How do hospital ratings in California affect the average risk-adjusted mortality rate for different procedures? Which procedure was performed "worse" by hospital rating based on the highest risk-adjusted mortality rate?
   - Importance: The question is important because it allows one to analyze the impact of hospital performance on mortality rates for different medical procedures. This brings significance for the hospitals in the state of California as well as patients looking for appropriate medical care. By evaluating the relationship between hospital ratings and mortality rates, hospitals can identify where there may be issues concerning quality control and allocate additional resources for better patient care. From this, incoming patients can make informed decisions when deciding where to receive medical treatment based on their medical condition/procedure. 
   - Tie to Dataset: This relates to the second dataset because it provides information on hospital ratings, risk-adjusted mortality rates, and procedure/conditions allowing us to come up with this visual model. 
    
2. What is the relationship between poverty rates and the average risk-adjusted mortality rates by county?
   - Importance: The question is important because it reflects on the understanding of how one's financial situation can affect the outcome of one's health, specifically mortality rates. Economically, there may be costs or threats to the economy as a state or by county for poverty-related inequalities. From this, authorities in the state of California may use this insight to hold accountability and implement policies to target possible health disparities regardless of one's income. However, if there is no clear relationship, officials would be encouraged to investigate other factors besides poverty rates to determine the overall health outcomes of the people.
   - Tie to Dataset: This relates to the second and third datasets because it provides information on the risk-adjusted mortality rates, county, and CPM poverty ratings with some data manipulation.
   
## Data Manipulations:
   - Manipulation 1: Initially, when comparing the poverty rate to RAR, many hospitals were causing the poverty rate by the county to appear multiple times. We created the following calculated field to consolidate the RAR into counties instead of hospitals. {FIXED [County] : AVG([Risk-adjusted Rate])}
   - Purpose: The purpose of this manipulation was to create a more accurate representation of risk-adjusted mortality rates across different counties in California. By consolidating the RAR at the county level, we aimed to eliminate the impact of individual hospitals that may appear multiple times in the dataset, allowing us to understand better the relationship between the poverty rates and mortality rates at a broader geographic scale. This approach helped us focus on regional patterns and variations in mortality rates, independent of specific hospital-level factors. 

## Analysis and Results:
  - Our first question explores how hospital ratings in California influence the average risk-adjusted mortality rate (RAMR) for various medical procedures using data from the California Hospital Inpatient Mortality Rates and Quality Ratings dataset. This investigation is crucial for understanding the impact of hospital performance on patient outcomes, aiding hospitals in identifying areas for quality improvement, and empowering patients to make informed healthcare decisions. Through a geographic visualization, we observed that certain procedures had higher risk-adjusted mortality rates in hospitals with lower ratings, highlighting the significance of hospital quality in healthcare delivery.
  - Our second question showed that the poverty rate by county in California and its respective average risk-adjusted rate showed an R-squared value of 0.0061 and a P-value of 0.5797, indicating that 0.061% of the variability observed in the risk-adjusted mortality rate is explained by the regression model. The P-value of 0.57 is high and not statistically significant, suggesting that the poverty rate by county does not determine RAMR. The p-value indicates that there is a 57% chance we would get the results of the observation if poverty rate and RAMR were not correlated.
   - Visualizations:
     ![IMG_3839](https://github.com/den50791/MIST4610-Group-7-Project-2/assets/163002845/6fd34b03-c833-4269-92f7-b22f0fb21ae3)
     <img width="1063" alt="Screenshot 2024-04-28 at 9 09 53 PM" src="https://github.com/den50791/MIST4610-Group-7-Project-2/assets/163002845/97552681-dae0-44e1-b360-140cb02071ff">
     ![image](https://github.com/den50791/MIST4610-Group-7-Project-2/assets/163002845/a6d9b112-2c1e-4138-9ef7-303e93f2adca)
   - Limitations: From the California datasets, we concluded that only disease type and hospital rating were indicative of risk-adjusted mortality rates in California, not the poverty rate. However, it should not be assumed that impoverished areas receive the same amount of medical care as affluent areas. This was a limitation of our analysis, as it is possible and very likely that impoverished individuals suffer from a lack of healthcare. What can be deduced from our analysis is that if a person is able to receive medical care in an impoverished area, they should not notice a significant difference from the care that they would receive in affluent areas.
