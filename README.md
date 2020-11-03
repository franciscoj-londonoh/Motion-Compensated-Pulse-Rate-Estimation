# Motion compensated pulse rate estimation

## Project Overview
A core feature that many users expect from their wearable devices is pulse rate estimation. Continuous pulse rate estimation can be informative for many aspects of a wearer's 
health. Pulse rate during exercise can be a measure of workout intensity and resting heart rate is sometimes used as an overall measure of cardiovascular fitness. 
In this project, a pulse rate estimation algorithm was built for a wrist-wearable device.

This project has 2 main parts.

> 1. Develop a Pulse Rate Algorithm on the given training data. Then Test Your Algorithm and see that it has met the success criteria.
> 2. Apply the Pulse Rate Algorithm on a Clinical Application and compute more clinically meaningful features and discover healthcare trends.

## Project Highlight
The development of this project resulted in a model that:
* Estimates pulse rate from the PPG signal and a 3-axis accelerometer
* Assumes pulse rate will be restricted between 40BPM (beats per minute) and 240BPM
* Produces an estimation confidence. A higher confidence value means that this estimate should be more accurate than an estimate with a lower confidence value
* Produces an output at least every 2 seconds



## The Project at a glance

Success criteria
The algorithm performance success criteria was if the mean absolute error (MAE) at 90% availability was less than 15 BPM on the test set. Put another way, the best 90% of the estimates, according to the confidence output, must have a MAE of less than 15 BPM.


Remember to bandpass filter all your signals. Use the 40-240BPM range to create your pass band.
Use plt.specgram to visualize your signals in the frequency domain. You can plot your estimates on top of the spectrogram to see where things are going wrong.
When the dominant accelerometer frequency is the same as the PPG, try picking the next strongest PPG frequency if there is another good candidate.
Sometimes the cadence of the arm swing is the same as the heartbeat. So if you can't find another good candidate pulse rate outside of the accelerometer peak, it may be the same as the accelerometer.
One option for a confidence algorithm is to answer the question, "How much energy in the frequency spectrum is concentrated near the pulse rate estimate?" You can answer this by summing the frequency spectrum near the pulse rate estimate and dividing it by the sum of the entire spectrum.

Dataset
You will be using the [Troika](https://ieeexplore.ieee.org/document/6905737) dataset to build your algorithm. Find the dataset under datasets/troika/training_data. The README in that folder will tell you how to interpret the data. The starter code contains a function to help load these files.


