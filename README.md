# Introduction:

Improving traffic safety is a major concern for any metropolitan city. In 2018 alone, there were 36,560 car crash related fatalities that occurred within the U.S. In order to counter and help eliminate car crash fatalities, initiatives such as Vision Zero have been taken up. A number of cities such as New York City and Chicago have followed this initiative within their cities to help promote traffic safety. The core concept behind this initiative is that traffic crashes are preventable and even one life lost is far too many.

My purpose in this project was to design a predictive model that would be able to analyze the primary causes for car crashes. Being able to design a model that can accurately predict the main cause for an incident occurring will allow the city to effectively act against it. If we know the cause for an incident, a city can then plan appropriately as to what measures should be taken to prevent them from happening again. In this project, I will be looking at car crash data from the city of Chicago in order to build a predictive model for their causes as well as identify a number of trends from the incidents.

# Data Setup and Cleaning:

The Traffic Crashes data comes from the Chicago Data Portal, an open data source maintained by the city of Chicago. The dataset contains all traffic crashes that were reported by the police within the city limits, going back to 2017. Linked to the crash dataset are two datasets corresponding to Vehicles and Persons involved in the crash. Each crash incident has a unique crash record ID and report number associated with it, which allows for cross-referencing on the dashboards provided for the datasets. 

The Crashes dataset contains a number of details related to the incident, such as location/time information, conditions of the road and traffic safety device functionality. The most important detail available is the primary contributory cause for the crash as determined by the office who reported the crash. However, there was a significant number of incidents (roughly 40,000) that did not have a primary cause attributed to them. I decided to only focus on incidents that had a definitive cause determined.

For the purpose of this project, I only focused on incidents that occurred between July 2019 and July 2020. I was left with roughly 65,000 car crash incidents to examine and use for modeling. The data was in relative good standing and did not require major cleaning before proceeding. A link to the main dataset can be found here: https://data.cityofchicago.org/Transportation/Traffic-Crashes-Crashes/85ca-t3if

# Data Exploration:

For my analysis, I decided to specifically look at the incidents that resulted in fatal injuries. Within our dataset, there were a total of 83 incidents that had fatal injuries.

I first wanted to look at what was the leading primary cause for these crashes. As we are trying to prevent traffic crashes from occurring, identifying the leading causes will allow the city to take appropriate counter measures. The datasets provide specific primary causes based on conditions such as the maneuvers each driver took and the physical condition of the driver. Four of the top five causes for fatal crashes were a result of a driver behaving in an aggressive and reckless manner while driving. Maneuvers such as failing to yield the right of way and and failing to reduce speed both resulted in the most number of deaths.

<img src="Images/Primary Cause of Death vs Number of Crashes.png">

In addition, I took a look at what times during the day that these incidents were occurring. Most major, non-fatal crashes occurred between 6-9 am and 3-7pm. This can be easily attributed to the amount of traffic that occurs during peak commuter hours. A higher number of cars on the road will no doubt result in a higher possibility of accidents occurring. The highest number of fatal crashes occurred between the hours of 6pm and 3am. These deaths can be attributed to instances in which the driver was impaired in some way, whether it was alcohol or drowsy driving.

<img src="Images/Hour and Severity of Crash vs Number of Crashes.png">

<img src="Images/Hour of Crash vs Number of Fatal Crashes.png">

# Data Modeling:

In order to generalize the various primary causes for a crash, I grouped the causes into three separate classes. The three classes were Improper/Aggressive Driving, Reckless Behavior, External Factors/ Others. Reckless behavior was deemed driving behavior that was done with known intent to harm or potentially harm others, such as driving drunk or disregarding traffic signals. Improper/Aggressive Driving denoted driving that was aggressive but not as dangerous as reckless driving, such as improper lane usage and . External Factors/Others was used to classify factors outside of the driver's immediate control such as weather and distractions from outside the vehicle.

Multiclass classification models were used in order to try to classify these incidents. Models such as K-Nearest Neighbors and Decision Trees were among those used. The model that had the best performance was XGBoost, which had an accuracy of roughly 70%. 

<img src="Images/Confusion Matrix.png">

# Conclusions and Future Work:

From my analysis, I believe that the promotion of slower and less aggressive driving will result in fewer major incidents occurring. In addition, promoting driver safety especially those active at night will be able to prevent late night car accidents from occurring. Continuing to test our model against historical and more current data will allow us to make adjustments to improve overall performance. In addition, collaboration with other cities such as New York City that maintain accessible traffic records will allow for more effective traffic safety programs to be developed.
