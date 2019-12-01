---
name: Environmental sound recognition
title: Environmental sound recognition
tools: [NeuralNet, Swift, Python]
tags: [NeuralNet, Swift, Python]
image: /assets/project-images/logos/environmental-sound-recognition-logo.png
description: A neural network, which recognizes environmental sounds (e.g. boiling water, whisteling, ...).
---

## Overview
The aim of this project was to generate a neural network which recognizes environmental sounds and is applicaple in real time iOS-Applications. 
As a proof of conecpt, we want to detect the sound of boiling water in the kitchen.

## Table of Contents
1. [Spectrogram](#spectrogram)
2. [Neural Network](#neural-network)
3. [Result](#third-example)

<img src="/assets/project-images/environmental-sound-recognition/boiling-water-1600x800.jpg" alt="Image" width="1000"/>

### Spectrogram 

[TempiFFT](https://github.com/jscalo/tempi-fft) allows to generate real time spectrograms from the mircophone input in iOS. This is not essentially needed for the detection, but adds an intuitive layout to the App. 

It uses Fast Fourier Transform (short FFT), which is a method for deconstructing an audio signal (or any time-based signal for that matter) into its constituent frequencies and intensities.

For discrete values (like sound data), the Discrete Fourier Transformation (DFT) is given by
<a href="https://www.codecogs.com/eqnedit.php?latex=\Large&space;f_m&space;=\sum_{k=0}^{2n-1}x_k&space;e^{-\frac{2\pi&space;i}{2n}mk}\quad&space;m=0,...,2n-1" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\Large&space;f_m&space;=\sum_{k=0}^{2n-1}x_k&space;e^{-\frac{2\pi&space;i}{2n}mk}\quad&space;m=0,...,2n-1" title="\Large f_m =\sum_{k=0}^{2n-1}x_k e^{-\frac{2\pi i}{2n}mk}\quad m=0,...,2n-1" /></a>

### Neural Network

The Neural Network is bases on [Turicreate](https://apple.github.io/turicreate/docs/userguide/sound_classifier/), which is a library provided by Apple.

```python
import turicreate as tc
from os.path import basename

# Load the audio data and meta data.
data = tc.load_audio('./ESC-50/audio/')
meta_data = tc.SFrame.read_csv('./ESC-50/meta/esc50.csv')

# Join the audio data and the meta data.
data['filename'] = data['path'].apply(lambda p: basename(p))
data = data.join(meta_data)

# Drop all records which are not part of the ESC-10.
data = data.filter_by('True', 'esc10')

# Make a train-test split, just use the first fold as our test set.
test_set = data.filter_by(1, 'fold')
train_set = data.filter_by(1, 'fold', exclude=True)

# Create the model.
model = tc.sound_classifier.create(train_set, target='category', feature='audio')

# Generate an SArray of predictions from the test set.
predictions = model.predict(test_set)

# Evaluate the model and print the results
metrics = model.evaluate(test_set)
print(metrics)

# Save the model for later use in Turi Create
model.save('mymodel.model')

# Export for use in Core ML
model.export_coreml('mymodel.mlmodel')
```

In order to distribute the app see [Turicreate Issue](https://github.com/apple/turicreate/issues/2050)


<img src="/assets/project-images/logos/auto-cooking-logo.png" alt="Image" width="200"/>

<img src="/assets/project-images/logos/environmental-sound-recognition-logo.png" alt="Image" width="200"/>
