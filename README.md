* The information about Google stock prices is given during the span of 4 years between 2012-2016 in the form of csv file and in test dataset Google stock prices data of 2017 january month is given
Now after loading train data csv file using 'pd.read_csv' of pandas, we will do Normalization on all the columns except the date column as normalization is best to use when output layer has sigmoid activation
Now we will initialize empty lists X_train,y_train and in case of X_train we will append 1st element as a list of previous 60 previous closing prices and 2nd element is another list of 60 previous closing day prices like this we will do till the last example in training set and we will get X_train as list with shape [1198,60]
We performed above step as in this RNN we assume closing price of stock on a day will depend on closing prices of past 60days so thats why we created X_train in that way
Also Y_train is just closing price on that day.Later we will convert X_train a 2D array of shape (1198,60) to (1198,60,1)
Now we will import required libraries like LSTM,Dense,Dropout,Sequential.Here the purpose of Dropout ingeneral is this controlls overfitting.
Now we will initialize our RNN,which will have LSTM units inside and as mentioned Dropout helps in controlling overfit
Here the important thing to note is LSTM units inside each layer has to be given a proper values(proper parameter tuning has to be done)else our predictions may become wrong
After adding LSTM layers finally we will add a dense layer which has 1 output unit(as it is not a classification problem) as values has to be predicted here
Then we will use optimizer as adam and loss as 'mean_squared_error'.Choosing proper optimizer and loss function is necessary for optimization of model
Now using above model we will make predictions on test dataset(2017 January data after Normalization)
After making predictions using inverse_transform we can convert back the normalized prediction values to proper values
Now we will make a plot stock_value vs Financial day on test dataset and we will draw 2 plots one is with original stock_values and other is predicted stock_values and then we can compare them visually
Even though the predictions maynot be exactly accurate but the predicted graph has guessed the trend(wheather prices will increase or decrease) in correct way
