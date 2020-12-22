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

Then we filtered the outliers, as well as removed the NA value of potential features. The final dataset contains 26673 observations.

## Correlation

We created a correlation matrix to examined the correlation between those numerical variables.
![]({{site.baseurl}}/assets/images/corr.png)

## Modeling
After correlation analysis, we used a 70/30% training/test split and built an randomforest regression model and a k-nearest neighbors regression model.

The randomforest regression model result:

```python
{'min_samples_split': 10, 'n_estimators': 100}
MAPE:0.018253739045780787
R2:0.9999975544060441
MSE:1.0383249638706494e-11
RMSE:3.2223050195018e-06
```
The k-nearest neighbors regression model result:   

```python
{'n_neighbors': 3}
MAPE:7.077931006636971
R2:0.9719636609702775
MSE:1.1903378580030773e-07
RMSE:0.0003450127328089613
```

The random forest model result shows R2 as 0.99, indicating that this algorithm can be used as a relatively ideal predictive model.Then, We produced a bar  plot of feature importance of the random forest model, it can be seen that the total population per tract and proportion of white residents has a significant impact on our predictive value-- the number of cases per population.

![importance.png]({{site.baseurl}}/assets/images/importance.png)


## More than This
Policing is at a critical juncture in American after many publicly reported cases of police violence against unarmed African Americans, calls for more-equitable law enforcement are growing. 

But is predictive policing just? Proponents argue that predictive policing can help predict crimes more accurately and effectively than traditional police methods. Today, with growing awareness that Black Lives Matter and that policing resources in America are allocated in part, by way of systematic racism, critics increasingly charge that Predictive Policing is harmful. They say that attempts to forecast crime with algorithmic techniques would reinforce existing racial biases in the criminal justice system.   
   
Although there are constant controversies about predicting policing, it is obvious that it will be helpful for residents to know more about the inner-workings of the predicting policing product, and use it more carefully to prevent increased bias and unwarranted surveillance.



