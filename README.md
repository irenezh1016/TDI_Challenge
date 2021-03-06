# Project: Wildfire Risk and Information System
## Motivation: 
Wildfire is one of the most destructive disasters that are often caused by human. Averagely, there are more than 100,000 wildfires in the US every year, clearing 4 to 5 million acres of land and causing huge economic loss. However, naturally occurred wildfires play an important role in the ecosystem. This project aims at providing insights on wildfire, its causes and behavior, therefore helps to make useful recommendations to increase public safety, minimize economic damage from future wildfires.

Some empirical work on wildfire modelling has been done in academia and multiple machine learning models on predicting wildfires have been tested and analyzed. This project will focus on transferring academic knowledge into practical use, especially on applying it to the case of United States. The project aims at providing an easy-to-understand web app which can help non-technical background people to learn more about how machine learning models can deepen general public’s understanding on wildfires and reduce future risks.

## Targeted problems: 
1)	Wildfires are costly, and firefighting is also costly.\
Analyzing the geographical information on where and when the wildfires occurred could provide useful information to identify high-risk areas that are vulnerable to wildfires, therefore help making better strategies on where fire-fighting forces are located and how to improve respond time to wildfires. At the same time, this will deepen public’s understanding on wildfires and alert them to avoid doing activities in high risky areas that can potentially cause a wildfire. 

2)	Reasons for many destructive wildfires are not identified.\
Reasons for lot of wildfires that burned millions of acres are missing or unidentified. Knowing the reasons for these wildfires could be crucial for future preventive measures on human-caused wildfires. Using machine learning models to predict the causes and risks of wildfires can help with planning preventive measures. 

This project aims at providing insightful information from analyzing historical data and utilizing appropriate machine learning techniques to solve above problems.

## Finishing product:
A dashboard that contains: 
1)	Interactive page where users can select a state and view relevant statistical analysis and data visualizations on historical data. 
2)	Deatiled breakdown of wildfire causes.
3)	Prediction of the causes and risks of wildfires.

Code for a dashboard made using Dash and Plotly can be found in the [app.py](https://github.com/irenezh1016/Project-Wildfire/blob/master/app.py) file. 

<img width="1005" alt="WRIS" src="https://user-images.githubusercontent.com/12699202/65459126-1dfc4280-de1d-11e9-8045-000696c9227d.PNG">
<img width="1090" alt="WRIS3" src="https://user-images.githubusercontent.com/12699202/65459127-1dfc4280-de1d-11e9-8f2e-f202161bbbf9.PNG">


## Structure of the project:
### Section I: Preparing Data
This section will focus on preparing data (including merging other necessary weather or geographical data to the main dataset), cleaning data, and generating necessary variables to the following exploratory analysis and data visualization. 

The main dataset for this project is from [USDA Forest Service](https://www.fs.usda.gov/rds/archive/Product/RDS-2013-0009.4/) (about 758 MB).
One caveat is that weather information is missing from the main dataset. Adding weather information could be very useful to analyze and predict wildfire causes. There are multiple sources for daily weather records by location published by [NOAA](https://www.ncdc.noaa.gov/cdo-web/) and earth observation data published by [NASA](https://earthdata.nasa.gov/earth-observation-data). 

Geographical information such as location of residential and camping areas is also important to understand the human-caused wildfires. This information can be accessed through google maps [API](https://developers.google.com/maps/documentation/).

Based on the fire date and location information in the main dataset, other information can be matched to each entry of the wildfire in the main dataset. In order to provide a deeper understanding on why wildfires occurred, geographical and weather information will be added based on data availability.

### Section II: Exploratory Analysis and Data Visualization
This section will focus on conducting statistical analysis on historical data to provide insights on when, where, and why wildfires occurred. This section will also identify the most destructive wildfires in the sample period and analysis their reasons, location, burning time, and, other environmental/geographical factors (e.g. weather, temperature, nearby camping sites, residential areas). This will provide a deeper understanding on where the most destructive wildfires are most likely to happen. 
Potential questions to answer:
-	Did most destructive wildfires happen on days with low humidity and high temperature?
-	What factor contributes the most to the burning time of a wildfire? (firefighting resources, fire size, or close to residential areas ??)
-	What kind of environment is most likely to trigger a wildfire? (especially human-caused wildfires)

### Section III: Modeling Wildfires
This section aims at exploring different machine learning techniques to:
-	Classify the causes of historically unclassified wildfires through other available information (weather, date, burning time, and so on). 

-	Construct algorithms to model the causes and predict probability of wildfires in the US. 

Models deployed: \
o	Logistic regression\
o	Random Forest\
o	Boosting regression trees (BRT)\
o	Support Vector Machines (SVM)

-	Test models and optimize processes.

After implementing all the ML models above, the conclusion here is that Random Forest and Gradient Boosting Trees perform the best among all the models. In addition, because of the highly imbalance nature of the dataset, meaning large scale wildfires are very rare, representing only about 2% of the whole dataset, and 85% of wildfires are caused by human instead of nature. I used SMOTE (Synthetic Minority Over-sampling Technique) to deal with imbalanced data, and found out the recall got improved by close to 50%. 

Code is here: [Machine Learning Models_Wildfire Prediction.ipynb](https://github.com/irenezh1016/Project-Wildfire/blob/master/Machine%20Learning%20Models_Wildfire%20Prediction.ipynb)

#### References: 
Castelli, M., Vanneschi, L., & Popovič, A. (2015). Predicting burned areas of forest fires: an artificial intelligence approach. Fire ecology, 11(1), 106-118.\
Kern, A. N., Addison, P., Oommen, T., Salazar, S. E., & Coffman, R. A. (2017). Machine learning based predictive modeling of debris flow probability following wildfire in the intermountain Western United States. Mathematical Geosciences, 49(6), 717-735.\
Rodrigues, M., & de la Riva, J. (2014). An insight into machine-learning algorithms to model human-caused wildfire occurrence. Environmental Modelling & Software, 57, 192-201.\
Vilar, L., Gómez, I., Martínez-Vega, J., Echavarría, P., Riaño, D., & Martín, M. P. (2016). Multitemporal modelling of socio-economic wildfire drivers in central Spain between the 1980s and the 2000s: comparing generalized linear models to machine learning algorithms. PLoS One, 11(8), e0161344.

