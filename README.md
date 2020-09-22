# Deep Learning

__Title__: Application of deep learning recurrent neural networks to model to bitcoin prices using combination of sentiment and timeseries techniques <br />
__Submitted by__: Amar Munipalle <br />

## 1. Introduction

The LSTM network has an input , output and two hidden layers. One model uses sentiment from the FNG index, and the other uses a timeseries of past prices (ten past) to predict price at t(n).

To ensure consistency between two networks and an 'apples to apples' comparison, identical hyper-parameters are used specifically batch size. Different batch sizes are tested out and finally a size of 1 is used as this yields the highest accuracy score (for FNG model). The same is replicated for the 'AR' model.

![Batchsize Tuning](images/LSTM_BatchSize_Test.png)



### Evaluate the performance of each model

A visual evaluation of the Predicted vs Actual prizes confirms the superior performance of the closing price / 'AR' model

![FNG](images/FNG_RealvsPredicted.png)
![Closing Price](images/AR_Closing_RealvsPredicted.png)

Histogram of the respective error functions are also plotted
![FNG](images/FNG_PredictionHistogram.png)
![Closing Price](images/AR_PredictionHistogram.png)

However a more comprehensive mathematical comparison is acheived by printing statistical components including
mean_forecast_error,mean_absolute_error,mean_square_error,rmse

Use the above to answer the following:

> Which model has a lower loss?
This is an open ended question and difficult to answer. While the FNG model has lower mean error, the total loss as defined by MSE and RMSE is lower for the Closing Price model.
>
> Which model tracks the actual values better over time?
Closing Price Model as illustrated by lower RMSE error which is directly related to the loss function
>
> Which window size works best for the model?
Batch size =1


| Metric     |Mean Error |MAE      |MSE       |RMSE        |
| -------    | --------- |---------|----------|------------|
|FNG         | 919       | 2352    |  7935967 |  2817      |
|Last Price  |  1194     | 1284    |  3061112 |  1749      |

### Closing Comments

Both the models are not perfect. The residual noise is not white noise and can be further differentiated as it demonstarted both trend and seasonality. This is mathematically confirmed by application of the Ljung-Box test which permits us to reject the null hypothesis that the residual is white noise.
