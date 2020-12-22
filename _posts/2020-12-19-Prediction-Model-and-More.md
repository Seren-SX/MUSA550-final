---
published: true
date: 2020-12-19T00:00:00.000Z
tags:
  - Predictive policing
  - Philadelphia
  - Random forest
  - Machine learning
excerpt: >-
  We decided to build a machine learning model to help predict crimes more
  accurately and effectively than traditional police methods....
read_time: true
---
## Data Processing


Through the previous data processing, we got a dataset contains 933353 observations. The amount of data is far too large that the operation continues to crash, so we use the `groupby` function to reduce the data size. We calculated the frequency of crimes per tract, the average temperature, humidity, visibility, etc. on a monthly basis.

We filtered the outliers, as well as removed the NA value of potential features. The final dataset contains 26624 observations.

## Correlation

We created a correlation matrix to examined the correlation between those numerical variables.
![]({{site.baseurl}}/assets/images/corr.png)

## Modeling
After correlation analysis, we used a 70/30% training/test split and built an randomforest regression model. the result of testing score is as follows:


The test score is 0.73, indicating that the algorithm can be used as a relatively ideal predictive model.Then, We produced a bar  plot of feature importance, the top 3 important features is entire home/apt dummy variable, LaggedPrice and logDisAttr.



## More than This
Policing is at a critical juncture in American after many publicly reported cases of police violence against unarmed African Americans, calls for more-equitable law enforcement are growing. 

But is predictive policing just? Proponents argue that predictive policing can help predict crimes more accurately and effectively than traditional police methods. Today, with growing awareness that Black Lives Matter and that policing resources in America are allocated in part, by way of systematic racism, critics increasingly charge that Predictive Policing is harmful. They say that attempts to forecast crime with algorithmic techniques would reinforce existing racial biases in the criminal justice system.





Due to the large amount of data, the calculation took a very long time
