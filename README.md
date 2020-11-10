# Motion compensated pulse rate estimation

## Project Overview
This project was part of the path to finish Udacity´s nanodegree: "AI for Healthcare", in which skills acquired in the "Applying AI to Wearable Device Data" course were applied to build a pulse rate estimation algorithm for a wrist-wearable device. A core feature that many users expect from their wearable devices is pulse rate estimation. Continuous pulse rate estimation can be informative for many aspects of a wearer's health. Pulse rate during exercise can be a measure of workout intensity and resting heart rate is sometimes used as an overall measure of cardiovascular fitness. 

## Background
Pulse rate is typically estimated by using a photoplethysmogram (PPG) sensor. However, the heart beating is not the only phenomenon that modulates the PPG signal, and arm movement and exercise could add to the periodic signal in the PPG. Thus, a pulse rate estimator has to be careful not to confuse this periodic signal with the pulse rate. To this regard, an accelerometer signal, which only sense arm motion, could support the adequate identification of the pulse rate.

All estimators will have some amount of error. How much error is tolerable depends on the application. For a logistic regression, the predicted class probabilities can be used to quantify trust in the classification. A classification where one class has a very high probability is probably more accurate than one where all classes have similar probabilities. This estimation of the algorithm's error is named the confidence.

Building a confidence algorithm for pulse rate estimation is a little tricker than logistic regression because intuitively, there isn't some transformation of the algorithm output that can make a good confidence score. However, by understanding our algorithm behavior, we can come up with some general ideas that might create a good confidence algorithm. For example, if our algorithm is picking a strong frequency component that's not present in the accelerometer, we can be relatively confident in the estimate. T

## Project Highlight
The development of this project resulted in an algorithm that:
* Estimates pulse rate from the PPG signal and a 3-axis accelerometer (ACCx, ACCy, ACCz)
* Assumes pulse rate will be restricted between 40BPM (beats per minute) and 240BPM
* Produces an estimation confidence. A higher confidence value means that this estimate should be more accurate than an estimate with a lower confidence value
* Produces an output at least every 2 seconds

## The Project at a glance
This project has 3 parts:
* Part 1: Exploratory Data Analysis [(EDA)](https://github.com/franciscoj-londonoh/Motion-Compensated-Pulse-Rate-Estimation/blob/main/Part1_EDA.ipynb)

![EDA](https://github.com/franciscoj-londonoh/Motion-Compensated-Pulse-Rate-Estimation/blob/main/Images/EDA_FFT.png)

* Part 2: Pulse rate estimation algorithm. Develop a pulse rate algorithm on the given training data. Then test the algorithm and see that it has met the success criteria

Success criteria
The algorithm performance success criteria was if the mean absolute error (MAE) at 90% availability was less than 15 BPM on the test set. Put another way, the best 90% of the estimates, according to the confidence output, must have a MAE of less than 15 BPM.


Remember to bandpass filter all your signals. Use the 40-240BPM range to create your pass band.
Use plt.specgram to visualize your signals in the frequency domain. You can plot your estimates on top of the spectrogram to see where things are going wrong.
When the dominant accelerometer frequency is the same as the PPG, try picking the next strongest PPG frequency if there is another good candidate.
Sometimes the cadence of the arm swing is the same as the heartbeat. So if you can't find another good candidate pulse rate outside of the accelerometer peak, it may be the same as the accelerometer.
One option for a confidence algorithm is to answer the question, "How much energy in the frequency spectrum is concentrated near the pulse rate estimate?" can answer this by summing the frequency spectrum near the pulse rate estimate and dividing it by the sum of the entire spectrum.

Dataset
You will be using the [Troika](https://ieeexplore.ieee.org/document/6905737) dataset to build your algorithm. Find the dataset under datasets/troika/training_data. The README in that folder will tell you how to interpret the data. The starter code contains a function to help load these files.

* Part 3: Clinical application. Apply the pulse rate algorithm on a clinical application and compute more clinically meaningful features and discover healthcare trends.
Part 2: Clinical Application
Now that you have built your pulse rate algorithm and tested your algorithm to know it works, we can use it to compute more clinically meaningful features and discover healthcare trends.

Specifically, you will use 24 hours of heart rate data from 1500 samples to try to validate the well-known trend that average resting heart rate increases up until middle age and then decreases into old age. We'll also see if resting heart rates are higher for women than men. See the trend illustrated in this image:


Dataset (CAST)
The data from this project comes from the Cardiac Arrhythmia Suppression Trial (CAST), which was sponsored by the National Heart, Lung, and Blood Institute (NHLBI). CAST collected 24 hours of heart rate data from ECGs from people who have had a myocardial infarction (MI) within the past two years.[1] This data has been smoothed and resampled to more closely resemble PPG-derived pulse rate data from a wrist wearable.[2]

![ClinicalApp1](https://github.com/franciscoj-londonoh/Motion-Compensated-Pulse-Rate-Estimation/blob/main/Images/Clinical_App1.png)
![ClinicalApp2](https://github.com/franciscoj-londonoh/Motion-Compensated-Pulse-Rate-Estimation/blob/main/Images/Clinical_App2.png)

Detailed description of the project proposal is provided in the [README](https://github.com/udacity/nd320-c4-wearable-data-project-starter) file of the Nanoprogram at Udacity's Github.



