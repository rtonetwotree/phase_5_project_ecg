# phase_5_project
 flatiron school data science bootcamp phase 5 project

### Business Problem 

Task is to classify heart status based on ECG readings. Considering the relatively cheap and painless process of getting an EKG reading from a patient compared to the high cost and consequences
of heart disease in the US, early detection of potentially problematic heart status via EKG could save lives, money, and other medical resources.

### Data

Data is sourced from the MIT-BIH Arrhythmia Database, info here:

<a href="https://www.physionet.org/content/mitdb/1.0.0/mitdbdir/#files-panel">MIT-BIH</a>, 

specifically this subset of the original database hosted on Kaggle:

<a href="https://www.kaggle.com/datasets/shayanfazeli/heartbeat">Kaggle Data Page</a>

### Data Preparation

Data preparation for this problem was not grueling, and for my final model involved reshaping my timeseries data to fit the LSTM input requirements and converting my target to categorical data.
The LSTM is already well-suited to train on time-series data. 

### Modeling

I isitially started with a much simpler non-time-series model to predict heart status, using a different dataset, but eventually progressed to time series modelling. Initially I was using tsfresh
to extract features from the timeseries, followed by several different models built on PCA performed on those extracted features. Some of these models performed decently but it wasn't until I
moved to neural networks that I was able to attain my best results. My best model is a hyperparameter tuned neural network with one bidirectional LSTM layer and two Dense layers with Dropout layers
inbetween each. More complex models were sucessfully created, but they performed on par with the model just described. These models required the keras-tuner package, which is useful for neural network 
modelcreation and has useful hyperparamater tuning methods.

This model can be found in the notebook titled time_series_neural_network.ipynb in the "notebooks" folder on this GitHub page,

found <a href="https://github.com/rtonetwotree/phase_5_project_ecg/blob/master/notebooks/time_series_neural_network.ipynb">here</a>

 and is
designed to be run on Google Collab because of the high levels of computing power required to train the neural network. If you load 
the database "mitbih_train.csv" into your Google Drive folder on the main level, Google collab should be able to read the database
in the notebook and fully run the code yourself.

The rest of the notebooks can be run locally, with the appropriate databases (mainly "mitbih_train.csv") loaded into the "data" folder
locally.  

### Evaluation

My final model performed well, with aweighted average accuracy score of .99 across all classes.

My validation approach involved data splitting into a train-test split for fitting and evaluation. I used elements of column transformation and object oriented programming in my final model. I 
used PCA and feature extraction, as well as others, in my prior models.