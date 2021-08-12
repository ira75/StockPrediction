# Stock Prediction

The aim is to create a Recurrent Neural Network model to predict stock prices.
The opening stock price for a day is predicted using the past 3 days Open, High, and Low prices and volume.

## Original Dataset

The data set "Data/q2_dataset.py" containg data for a stock for 5 years with one sample per day.

#Creating a Dataset

Dataset is created by using the latest 3 days as the features and the next day’s opening price as the target. The data is randomized and split into 70% training and 30% testing. The train data is saved as ‘train_data_RNN.csv’ and the test data is saved as ‘test_data_RNN.csv’.

## Preprocessing Data

* The python library Pandas is used to read and preprocess the data, along with Numpy library.
* Data is sorted using the date column.
* Two numpy arrays are created: data and target array.
* The data array contains 13 values in each row, one index value and 12 features representing volume, open, high, low values of the past three days. Index is added so that 
it can be later used to sort the array while plotting in test_RNN.py.
* The target array contains the open value of the fourth day, which is the value that is to be predicted using the data of previous three days.
* The data and target arrays are split into train and test sets using sklearn train_test_split function with shuffle=True, thus shuffling and splitting the data.
* The data_train and target_train values are merged into one numpy array “save_train_data” and are stored in train_data_RNN.csv file. Each row in the csv file 
contains the original index before shuffling, 12 features, target value i.e. 14 values total.
* The data_test and target_test values are merged into one numpy array “save_test_data” and are stored in test_data_RNN.csv file. Each row in the csv file contains the original 
index before shuffling, 12 features, target value i.e. 14 values total.

## RNN Model

* Unlike other RNN algorithms, Long Short-Term Memory (LSTM) has a high prediction capacity. LSTM has the property to remember the previous data values and effectively associate them to give a good prediction. LSTM model used in this question, has 4 LSTM layers each of 50 units, and each LSTM layer is followed by a dropout layer with 20% dropout. The output layer is a dense layer of one neuron.
* The type of optimizer used greatly effects the convergence of the network. The optimizer used is Adam.
* Loss function used for LSTM is mean squared error. The model is trained for 100 epochs, with a batch size of 32.



