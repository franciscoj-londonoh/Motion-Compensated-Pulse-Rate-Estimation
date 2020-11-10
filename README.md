# Motion compensated pulse rate estimation

## Project Overview
This project was part of the path to finish Udacity´s nanodegree: "AI for Healthcare", in which skills acquired in the "Applying AI to Wearable Device Data" course were applied to build a pulse rate estimation algorithm for a wrist-wearable device. This project produced a pulse rate estimation algorithm from signals obatined by a wearable device. Continuous pulse rate estimation can be informative for many aspects of a wearer's health, such as a measure of workout intensity during exercise and/or measure of overall cardiovascular fitness during resting heart rate. 

## Background
Pulse rate is typically estimated by using a photoplethysmogram (PPG) sensor. However, the heart beating is not the only phenomenon that modulates the PPG signal, and arm movement and exercise could add to the periodic signal in the PPG. Thus, a pulse rate estimator has to be careful not to confuse other periodic signals with the pulse rate. To this regard, an accelerometer signal, which only sense arm motion, could support the adequate identification of the pulse rate.

## Project Highlight
The development of this project resulted in an algorithm that:
* Estimates pulse rate from the PPG signal and a 3-axis accelerometer (ACCx, ACCy, ACCz)
* Assumes pulse rate will be restricted between 40BPM (beats per minute) and 240BPM
* Produces an estimation confidence. A higher confidence value means that this estimate should be more accurate than an estimate with a lower confidence value
* Produces an output at least every 2 seconds

## The Project at a glance
This project has 3 parts:
* Part 1: Exploratory Data Analysis [(EDA)](https://github.com/franciscoj-londonoh/Motion-Compensated-Pulse-Rate-Estimation/blob/main/Part1_EDA.ipynb)

The first part of this project involves an exploratory data analysis (EDA) to visualize the raw signals (PPG and 3D ACC) and the reference ("ground-truth") signal, and compare and pre-process them in the time domain. Then, a frequency domain analysis is performed to extract valuable information from the frequency content of each signal for improving the development of the algorithm in Part 2. 

![EDA](https://github.com/franciscoj-londonoh/Motion-Compensated-Pulse-Rate-Estimation/blob/main/Images/EDA_FFT.png)

* Part 2: [Pulse rate estimation algorithm](https://github.com/franciscoj-londonoh/Motion-Compensated-Pulse-Rate-Estimation/blob/main/Part2_PulseRateEstimation.ipynb)

This code is implemented to process files containing PPG and (3D) accelerometer signals, and use them to train a regression model for predicting the heart rate of a subject with an estimation error below 10 BPMs. The code is divided in functions to facilitate its implementation and use. The code includes an accessing and loading stage of the signals, a preprocessing to extract relevant features and identify the targets. Then, all data is used to train a regression model, which is saved. To evaluate the algorithm, a cycle is put in place and each signal is used to estimate the error of the model. To run the complete code it is necessary to call the Evaluate function with the sample frequency as an argument. As an output, the mean BPM error estimation is printed, and the regression model is available as 'regression_model.joblib'. The following sections describe in more depth the data used to train and test the model, each function included in the code to process the data, built the model and test its accuracy, and the method used to assess the performance of the model.


* Part 3: [Clinical application](https://github.com/franciscoj-londonoh/Motion-Compensated-Pulse-Rate-Estimation/blob/main/Part3_ClinicalApplication.ipynb)

The pulse rate algorithm, presented in Part 2, is adapted for a clinical application to compute more clinically meaningful features and discover healthcare trends. Specifically, 24 hours of heart rate data from 1500 samples are used to validate the well-known trend that average resting heart rate increases up until middle age and then decreases into old age, and to compare resting heart rates for women than men.

![ClinicalApp2](https://github.com/franciscoj-londonoh/Motion-Compensated-Pulse-Rate-Estimation/blob/main/Images/Clinical_App2.png)


Detailed description of the project proposal is provided in the [README](https://github.com/udacity/nd320-c4-wearable-data-project-starter) file of the Nanoprogram at Udacity's Github.



