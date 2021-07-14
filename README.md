# Modelling-EEG-signals-using-polynomial-regression-

Table of Contents

									
1.	Introduction				                                    		
2.	Preliminary Data Analysis					  		
3.	Regression 									
4.	AIC and BIC										
5.	ABC
6.	Appendix
7.	References


Introduction
The main focus of this assignment is to fit and determine the best possible nonlinear regression model that can well relate the relationship among the input predictors (EEG signals). Through modelling and analysing the four input EEG time-series data 𝐗 = {𝐱1, 𝐱2, 𝐱3, 𝐱4}, and an output EEG signal 𝐲. All the input predictors and output response data is subject to additive noise with unknown variance along with a time.csv file containing sampling time in seconds for all EEG data.
Preliminary Data Analysis
The objective of data analysis is the determine whether the data is of categorical variables or continuous variables, Descriptive data statistics for continuous variables provide details regarding mean, skewness and standard deviation.
Time Series plot are the visualisation between the time and the input EEG signals.


<img width="428" alt="image" src="https://user-images.githubusercontent.com/48376708/125630332-3da00e84-cbc4-4ac4-be68-dd902b93e2f2.png">

Here we can infer that the time series plot are stationary.
Distribution
Using the histogram and density plot, we can analyse the input signals distribution and determine the skewness of the input signals or if is it normally distributed or not. It is very important to know the normality, skewness or kurtosis of the data before performing any modelling or regression.


<img width="452" alt="image" src="https://user-images.githubusercontent.com/48376708/125630403-08b405c0-d49f-4b50-8b22-9ff8735d9b84.png">

Conclusion, In Fig 2 it is visible by the smoothening line that input signals x1, x2 and x4 are normally distributed whereas, input signal x3 has a clustering of data sets at the left hand side therefore Positive Skewness.

Correlation and Scatter Plots
Another method of visualisation is scatter plot from which we can determine the relationship between the particular input signal with the output signal furthermore the trend showing the best fit to the data.

<img width="421" alt="image" src="https://user-images.githubusercontent.com/48376708/125630451-0b76c6c8-0600-48bc-b95f-57e1487bd27c.png">


Correlation is the strength measure of a linear relationship between two variables (input EEG signal , output EEG signal) there are two types of correlation positive and negative. If the value of the correlation is close to 1 then it is the most significant variable affecting the output.
Conclusion, From Fig. 3 we can learn that x1(r = 0.7288) input signal has the closest value to 1 therefore it has a strong positive correlation.
Regression 
Linear Regression is the most straight forward statistical techniques. Regression is used for two analysis forecasting and prediction. It can also determine the casual relationship between dependent variable and one or more independent variables. Like we have in the above example the input EEG signals x1, x2, x3, x4 are all independent & identically distributed and the output signal y. Here we have to find the best regression model to fit in and predict or forecast the best possible output for new observations. We are provided with 5 candidate non-linear polynomial regression models to find which is the best fit model for the data sets. 
Least square estimate of the unknown model parameters calculates regression parameters by minimizing SSE (Sum of Squared Error), The resulting line is known as regression line. Least Square Estimates the slope and intercept of the model, but for multi-linear polynomial equation there are multiple slopes because of more than one variables.
When computing least squares we will get same number of estimates that of variables and plus one for the bias parameter.  
Y hat is the predicted value of the output y in a regression equation it is also known as the response variable. It is the matrix multiplication between model matrix and parameters estimated.

Residual Sum of Errors (RSS) can be easily be determined based on the parameters computed above for each model to find which model has the least residual sum of errors. It is the measure of the discrepancy between the estimated model output and the data. If RSS is small for a given model then it indicates a good fit of the model to the data. It is used in model selection and parameter selection too. 
RSS is the difference of the square of true value and the predicted value. 
Model 1: 57.32927   Model 2: 351.4147  Model 3: 57.32536  Model 4: 57.46405  Model 5: 57.35923
Conclusion, Model 3 and 5 have the highest RSS value so we can reject the model as it would not be the good fit for regression whereas, Model 3 has the lowest RSS.
Log-Likelihood estimation also known as MLE ( Maximum Likelihood Error ) is a method used for parameter estimating for a given distribution, using some observed data sets. MLE method is also used to learn about the best model parameters of a linear regression model. MSE choses as estimates the values of the parameters which are most consistent with the data sets.
It is most of the times  easier to minimise the negative of the log-likelihood rather than minimise it. So we put a minus sign in front of log-likelihood to give us the negative log-likelihood. We use log-likelihood function instead of likelihood function because it is quite often easier to work on the log of the density mathematically.
Akaike information criterion (AIC) and Bayesian information criterion (BIC)
AIC and BIC both are the estimation of sample prediction error. They provide a measure of estimation for the model if it may be in its prediction if applied for the whole data set (population) that our training data aims to represent. The best model is that one which neither overfits nor underfits the population. So the lowest measurement of AIC/BIC for a model is to be selected
Both AIC/BIC get similar results mostly. They are an approach to find the balance between complexity and a good fit for a model.
 Model 1: 328.2626, 344.7791 | Model 2: 688.7068, 698.6168 | Model 3:  326.2489, 339.4621
 Model 4: 326.7346, 339.9478 | Model 5: -13308.77, -13295.56


Distribution of model prediction errors

For distribution we can plot the histogram of residual values for the models given. This will help us understand the distribution if it is gaussian or not. 




<img width="449" alt="image" src="https://user-images.githubusercontent.com/48376708/125630509-ab1a3a5c-ab5b-483b-916a-a669264cbb36.png">


Q- Q Plot is a type of diagnostic of the residuals of the model, it plots quantiles of the data versus quantiles of a distribution. When we assess the plot we want the data points to be ideally clustered to the zero line which means smaller residuals. And what we don’t want is any pattern where the residual is increasing or decreasing  from the line with our predicted values Or any kind of pattern where the residual looks non-linear


<img width="491" alt="image" src="https://user-images.githubusercontent.com/48376708/125630582-79e695cc-6b77-41e1-a9de-ce16ed9b1104.png">



Normal Q-Q plot is to determine if our residual is normally distributed or not. If our data points are closely following the straight line in an upward trend and the data points are not deviating that looks like a S-shaped or bending at either end.
In Fig 5 we can clearly see that model 1, model 3 and model 4 are showing a normal distribution whereas, model 2 and model 5 we can see a S-Shaped pattern and a decreasing residual at the left side of the plot respectively.
Now, we have to find which has the least residual among the three models (1,3,4) which we can find by using boxplot, help us find the number of outliers and the model residual having less number of outliers. The Outliers affects the assumptions and results.
This type of plot helps us to easily detect outliers and tells us if our data is symmetrical or how tightly our data is grouped.



<img width="481" alt="image" src="https://user-images.githubusercontent.com/48376708/125630628-ea05fd6e-8e02-4d3b-b847-6d8b72530f8c.png">



Conclusion, From Fig 6 we can eliminate model 2 and 5 because they do not have a normal distribution and also there are too many outliers which affects our prediction if we use these models. Furthermore, they will result in underfitting model for the testing data.

Now, we have to select a model best fit for our population data using the AIC , BIC and distribution of residuals from the five models we were provided with.

We will use Statistical Approaches to estimate how complex a model is and how well it fits with a dataset.

o	Akaike Information Criterion (AIC)
o	Bayesian Information Criterion (BIC)
o	Model Residual Distribution

In AIC model selection approach, we simply select a model with the smallest AIC. Model 3 has the smallest value of all that is 326.2489 among all the other models.

In BIC the quantity calculated is different from that of AIC rather proportional to AIC, but for BIC the more complex model will have the worse (larger) value and hence it will not be selected. Model 3 has the smallest value of all that is 339.4621.
Model Residual Distribution shows us the normality and helps us find the outliers, from Fig 5 - model3 and the RSS value of model 3 (57.32536 ). we deduce that it is the most normal distribution among the other models.
Conclusion, Model 3 is the best model for our population data set and is a good fit for prediction because it has the lowest residual value and AIC and BIC values too. Because BIC value we can also compute that the model is not too complex and from AIC that it is not too simple to be used on testing data.
Now, Let’s create sample training data and testing data from our population data set used previously. Here we will be using 70% random data from population for training and 30% for testing.
From Model selection it is clear that we will be using model 3 for prediction and estimation. After we have split all the input EEG signals and output EEG signal into 70:30 proportion. Estimate the Model Parameters for the observations in training data using Least Squares.
Now to compute the model’s prediction on the testing data we just need to follow substitute the estimated parameter from the training data into the linear regression model generated for testing data sets. 
So, here we have used the slopes and intercept of training data and associated them with the testing data variables which gives us a predicted function.
We can also compute the Confidence interval for the testing data to check the residual error for each data point.
Here we will calculate the 95% CI for the testing data.
CI = 5.422729
ABC is used to estimate the posterior distribution of the model parameters. For complex models calculating likelihood is mere impossible. 
Now, for the selected best model we will perform the Approximation Bayesian Computation (ABC) Firstly lets, compute two largest absolute parameters from the least square estimation and fix all the other values as zero’s (constant).
Theta1 : 0.038109255  and  Theta bias: 0.448299550
We will be using runif() function to calculate the 100 uniform distribution values in the range of the parameters that is for theta1 (0 to 0.5) and for theta bias (0,0.1).
Now, we have to find the Y_Hat for the model 3 and parameters we have computed for the ABC. This will give us the residual error which is the difference between output values and Y_Hat of ABC.
After this we need to draw the samples for accepting the parameter or rejecting the parameter for this we run a for loop in residual error if the value of error is less than equal to epsilon value(0.1) then it will be accepted and if it is greater than epsilon it is rejected.
Now we will be using the 2D Contour plot to between the values of 2 parameters we have selected using contourPlot library here x axis is first parameter samples y axis is second parameter samples and z axis is the accepted values of residual error using ABC.














