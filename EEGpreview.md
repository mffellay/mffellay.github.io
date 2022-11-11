---
layout: default
---
[Main Site](./)

# EEG Thesis Project

An Electroencephalogram (EEG) was built using 8 gold cup electrodes connected to an OpenBCI Cyton.

The development was made on Python (JupyterNotebooks) and a Nvidia Jetson Nano as the AI and processing unit.

**Files can be found at: [EEG Graduation Thesis repository](https://github.com/mffellay/EEG).**

The first step is to record the signals through the 8 electrodes (channels) as comma separated values (.csv) ([record.py](https://github.com/mffellay/EEG/blob/main/record.py)).

Then this .csv file is initialized and a 50Hz (Mains plug frequency) Notch filter is applied. The plots show both the raw and the filtered signals ([initializedata.py](https://github.com/mffellay/EEG/blob/main/initializedata.py)).

<img src="https://raw.githubusercontent.com/mffellay/EEG/main/pics/samplesnotch.png" alt="notch">

For Channels 1 to 8 a Butterworth Bandpass Filter was applied, using 2Hz as lowcut frequency and 35Hz and highcut frequency. ([filtering.py](https://github.com/mffellay/EEG/blob/main/filtering.py)).

Channels 1 and 2.

<img src="https://raw.githubusercontent.com/mffellay/EEG/main/pics/ch%201-2.png" alt="channel1-2">

Channels 3 and 4.

<img src="https://raw.githubusercontent.com/mffellay/EEG/main/pics/ch3-4.png" alt="channel3-4">

Channels 5 and 6.

<img src="https://raw.githubusercontent.com/mffellay/EEG/main/pics/ch5-6.png" alt="channel5-6">

Channels 7 and 8.

<img src="https://raw.githubusercontent.com/mffellay/EEG/main/pics/ch7-8.png" alt="channel7-8">

Since the peak of the signal can be visualized clearly on channels 1 and 2, these are selected for the Autoencoder Model training. ([autoencoder.py](https://github.com/mffellay/EEG/blob/main/autoencoder.py)).

The signal (channel 1) is shortened to the specific range of the peak as shown.

<img src="https://raw.githubusercontent.com/mffellay/EEG/main/pics/sampletotrain.png" alt="sample">

Then, the training process is plotted, comparing the input to the trained Autoencoder model (reconstruction of the signal) 5, 15, 25 and 50 Epochs.

<img src="https://raw.githubusercontent.com/mffellay/EEG/main/pics/autoencodertraining.png" alt="training">

After 50 epochs, the model is tested on channel 2.

<img src="https://raw.githubusercontent.com/mffellay/EEG/main/pics/autoencoderTesting.png" alt="autoencodertest">

Then, using the same signal, the K-Means algorithm is applied, the goal being able to group the clusters on the signal peaks ([kmeans.py](https://github.com/mffellay/EEG/blob/main/kmeans.py)).

<img src="https://raw.githubusercontent.com/mffellay/EEG/main/pics/Kmeans.png" alt="Kmeans">

