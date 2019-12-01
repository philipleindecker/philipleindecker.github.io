---
name: AutoCooking
title: AutoCooking
tools: [App, NeuralNet, Swift]
tags: [App, NeuralNet, Swift]
image: /assets/project-images/logos/auto-cooking-logo.png
description: AutoCooking allows you to automatically detect, when water in a pod is boiling and notifies you with an accustic alarm. 
---

## Screenshots

<div style="clear: both;display: table;">
    <img src="/assets/project-images/auto-cooking/img1.png" alt="AutoCooking" style="float: left;height: 350px;"/>
    <img src="/assets/project-images/auto-cooking/img2.png" alt="AutoCooking" style="float: left;height: 350px;margin-left: 30px;"/>
    <img src="/assets/project-images/auto-cooking/img3.png" alt="AutoCooking" style="float: left;height: 350px;margin-left: 30px;"/>
</div>


## Description
AutoCooking allows you to automate your cooking!

No longer waiting for the water to cook! Now - with AutoCooking - you can relay on your iPhone to do the waiting for you. 
When the water is boiling and ready to be used for cooking, it will notify you by an acoustic alarm.

### How to use:
1.) Place the iPhone near the pod with the water you want to cook (approx. 30cm radius) and click on Start. 
2.) When the water is boiling, the phone will detect this and notifiy you with an acoustic alarm.
3.) Done

### Restrictions: 
Additional sound or noise typical for a kitchen environment is usually ignored by the trained neural network. Boiling the water with or without a pod lid should also not affect the detection. Sometimes, if the noise is too loud, it might lead to false or no detections. 
The App is trained to detect the sound of only one pod with boiling water. Thus, do not use the App, if you are cooking with multiple pods, pans, ... etc.

### Technical background and Security:
The app uses a pre-trained AI, specifically to detect the sound of boiling water, even in a noisy environment. The app does not send or store any data of the recordings and is also fully functional offline.

<img src="/assets/project-images/logos/auto-cooking-logo.png" alt="AutoCooking" width="200"/>
