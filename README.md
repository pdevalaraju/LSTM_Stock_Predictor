# LSTM_Stock_Predictor

![deep-learning.jpg](Resources/deep-learning.jpg)

Due to the volatility of cryptocurrency speculation, investors will often try to incorporate sentiment from social media and news articles to help guide their trading strategies. One such indicator is the [Crypto Fear and Greed Index (FNG)](https://alternative.me/crypto/fear-and-greed-index/) which attempts to use a variety of data sources to produce a daily FNG value for cryptocurrency. Let us build and evaluate deep learning models using both the FNG values and simple closing prices to determine if the FNG indicator provides a better signal for cryptocurrencies than the normal closing price data.

We will use deep learning recurrent neural networks to model bitcoin closing prices. One model will use the FNG indicators to predict the closing price while the second model will use a window of closing prices to predict the nth closing price.

Approach:
1. [Prepare the data for training and testing](#prepare-the-data-for-training-and-testing)
2. [Build and train custom LSTM RNNs](#build-and-train-custom-lstm-rnns)
3. [Evaluate the performance of each model](#evaluate-the-performance-of-each-model)

- - -
### Prepare the data for training and testing

We will slice the data using the window of time function for the n day window.

For the Fear and Greed model, We will use the FNG values to try and predict the closing price. 

For the closing price model, We will use previous closing prices to try and predict the next closing price.

We will use  70% of the data for training and 30% of the data for testing in each model

using MinMaxScaler we will scale X and y values for the model.

Finally, reshape the X_train and X_test values to fit the model's requirement of samples, time steps, and features. (*example:* `X_train = X_train.reshape((X_train.shape[0], X_train.shape[1], 1))`)

### Build and train custom LSTM RNNs

In the Jupyter Notebooks, we created the same custom LSTM RNN architecture. 
![Model Architecture](Resources/model.PNG)

In one notebook, we fit the data using the FNG values. In the second notebook, only closing prices are used.

In order to compare the models, we will use the same parameters and training steps for each model. 

### Evaluate the performance of each model

Finally, using the testing data to evaluate each model and compare the performance, we will answer the following:

> Which model has a lower loss?

Close price based on past closing prices model has a lower loss compared to the model which predicted using FNG
>
> Which model tracks the actual values better over time?
>
### Close price prediction based on past close prices bettter tracks the actual values than predicting using FNG.

<table> <tr><td>

![Prediction using 2day window close prices](Resources/close_2day.PNG) </td><td>


![Prediction using 2day FNG window](Resources/FNG_2.PNG) </td></tr> </table>

</td></tr></table>

> Which window size works best for the model?
### 2 day window size gave abgtter closing price prediction. <br>

Price Prediction using closing prices of different time windows

<table> <tr><td>

![Prediction using 5day window close prices](Resources/close_5day.PNG) </td><td>

![Prediction using 10day window close prices](Resources/close_10day.PNG)</td></tr>
 
<tr><td>
![Prediction using 2day window close prices](Resources/close_2day.PNG) </td><td>

![Prediction using 20day window close prices](Resources/close_20day.PNG)</td></tr> </table>


Price Prediction using FNG index over different time windows 
<table> <tr><td>
![Prediction using 10day FNG window](Resources/FNG_20.PNG) </td><td>

![Prediction using 20day FNG window](Resources/FNG_10day.PNG) </td><td></tr>

<tr><td>
![Prediction using 5day FNG window](Resources/FNG_5.PNG)</td><td>

![Prediction using 2day FNG window](Resources/FNG_2.PNG) </td></tr> </table>
- - -

