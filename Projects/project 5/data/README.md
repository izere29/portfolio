### Problem Statement
​
The Food and Agriculture Organization of the United Nations is a specialized agency of the United Nations that leads international efforts to defeat hunger and improve nutrition and food security. Increases in surface air temperature associated with rising greenhouse gas concentrations threaten plant growth and yield, putting millions of farmers and communities at risk throughout the world. Together with changes in precipitation and increases in extreme events such as flooding and droughts, climate change threatens countries’ food security, and their ability to eradicate poverty and achieve sustainable development.
​
This project will focus on building a Time series model that will predict and forecast the Temperature change for the next 15 years using a dataset from FAOSTAT on temperature change . This model will shows the trends and will allow an understanding of impacts of climate change challenges on Agriculture.
​
### Background
​
The dataset is a combination of a dataset of temperature change from Kaggle (https://www.kaggle.com/sevgisarac/temperature-change) and a dataset of countries with regional codes from (https://github.com/lukes/ISO-3166-Countries-with-Regional-Codes/blob/master/all/all.csv).
​
The FAOSTAT Temperature Change domain disseminates statistics of mean surface temperature change by country, with annual updates. The current dissemination covers the period 1961–2020. Statistics are available for monthly, seasonal and annual mean temperature anomalies, i.e., temperature change with respect to a baseline climatology, corresponding to the period 1951–1980. The standard deviation of the temperature change of the baseline methodology is also available. Data are based on the publicly available GISTEMP data, the Global Surface Temperature Change data distributed by the National Aeronautics and Space Administration Goddard Institute for Space Studies (NASA-GISS).
​
Content Statistical concepts and definitions
​
Statistical standards: Data in the Temperature Change domain are not an explicit SEEA variable. Nonetheless, country and regional calculations employ a definition of “Land area” consistent with SEEA Land Use definitions, specifically SEEA CF Table 5.11 “Land Use Classification” and SEEA AFF Table 4.8, “Physical asset account for land use.” The Temperature Change domain of the FAOSTAT Agri-Environmental Indicators section is compliant with the Framework for the Development of Environmental Statistics (FDES 2013), contributing to FDES Component 1: Environmental Conditions and Quality, Sub-component 1.1: Physical Conditions, Topic 1.1.1: Atmosphere, climate and weather, Core set/ Tier 1 statistics a.1.
​
Statistical unit: Countries and Territories.
​
Statistical population: Countries and Territories.
​
Reference area: Area of all the Countries and Territories of the world. In 2019: 190 countries and 37 other territorial entities.
​
Code - reference area: FAOSTAT, M49, ISO2 and ISO3 (http://www.fao.org/faostat/en/#definitions). FAO Global Administrative Unit Layer (GAUL National level – reference year 2014. FAO Geospatial data repository GeoNetwork. Permanent address: http://www.fao.org:80/geonetwork?uuid=f7e7adb0-88fd-11da-a88f-000d939bc5d8.
​
Code - Number of countries/areas covered: In 2019: 190 countries and 37 other territorial entities.
​
Time coverage: 1961-2020
​
Periodicity: Monthly, Seasonal, Yearly
​
Base period: 1951-1980
​
Unit of Measure: Celsius degrees °C
​
Reference period: Months, Seasons, Meteorological year
​
Region of countries and territories
​
Subregion of countries and territories
​
### Data Import and Cleaning
​
From the Temperature Change dataset , we did some cleaning and removed the data from 3 months period and the meteorological year so that we can have the data for every month.
​
Next, we looked at the missing values in the columns of months and found missing values. We decided to remove the row without the months and where the value is missing replace it with 0. We combined the month and year columns to create a new column date.
​
After the cleaning process, we removed the unnecessary columns and combined the new data frame with the dataset that has region and subregion to a single data frame. We saved the Data frame to a new .csv file.
​
​
### Exploratory Data Analysis
​
We plotted time series plots for global and all regions, as well as 12 month rolling averages, and autocorrelation and partial autocorrelation plots.
​
Additionally we did a seasonal decomposition.
​
Key Observations:
​
Trends Observation: With the trend decomposition we saw that globally the Temperature change is rising to 1.2°C.If we look at each region we saw that Europe is having the highest Temperature change because it is almost at 1.8°C. Another observation is that the highest Temperature in Antarctica occurred around 2009 to 2011 at 0.9°C in temperature change.
​
Seasonal Observation: With the seasonal decomposition we saw that the same temperature change reoccurs after some time almost around 2 years which gives it seasonality. It is slightly different from region to region.
​
​
### Modeling
​
In this part we built a SARIMAX model to predict and forecast the temperature change for the next 15 years. We choose to use SARIMAX because the model take into account the seasonality of our dataset.
​
SARIMA models include extra parameters related to the seasonal part.  Therefore, a SARIMA(p,d,q)(P,D,Q,S) model has (p,d,q) that are non-seasonal parameters and P,D,Q,S that are the seasonal parameters.
​
Non-seasonal orders
​
p: Autoregressive order. d: Differencing order. q: Moving average order.
​
Seasonal orders
​
P: Seasonal autoregressive order. D: Seasonal differencing order. Q: Seasonal moving average order S: Length of the seasonal cycle.
​
​
An Augmented Dickey-Fuller test was done to check if our time series are stationary using a confidence interval of 95%.
​
We interpret this result using the p-value from the test. A p-value below a threshold of 5% suggests we reject the null hypothesis (stationary). Otherwise a p-value above the threshold suggests we fail to reject the null hypothesis (non-stationary).
​
According to the p-value we can say that our data are stationary.
​
Based on that result our initial d in the SARIMAX parameters was 0.
​
​
We used AIC (Akaike information criterion) metric to find the best value of p and q for non-seasonal orders . The best_aic was (4,0,3).
​
​
We used a for loop function to go through different value of P,D,Q which are seasonal orders to be used by the SARIMAX model in order to find the best seasonal parameters. S, the length of the seasonal cycle, was determined by analyzing partial autocorrelation plots by region and testing for the best value.
​
The best seasonal orders found was (2,2,2,S)
​
​
RESULTS:
​
From doing a train test split of 75% train size, we ran the SARIMAX model globally and for each region and plotted the results and plotted a forecast for the next 15 years.
​
The forecasting models picked up the increasing trends and seasonality of the data.
​
Using Root Mean Squared Error, we found that Oceania and the Americas had the lowest errors and Antarctica and Europe had the highest.
​
RMSE values:
​
Global - 0.32
Asia -   0.61
Americas - 0.26
Antarctica - 2.30
Africa - 0.36
Europe - 1.26
Oceania -  0.20
​
​
### Conclusions and Recommendations
​
AS conclusion , the SARIMAX model we built is a starting point. It picked up the trend and seasonality in the predictions and forecast. To improve it we can look more on subregions and those regions with high RMSE for outliers.
​
### Link to Jupyter Workbook:
​
 [`Temperature_Change_Time_Series`](./project5.ipynb)