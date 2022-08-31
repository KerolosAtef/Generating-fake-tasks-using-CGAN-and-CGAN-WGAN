# Generate fake tasks using CGAN and WGAN with Wassertein loss function
![Fake or real](https://drive.google.com/uc?export=view&id=1-PMAvx35fcqMgSatbjTQjxx7nGWJJTv-)

### This project uses and explain how to use GANs with tabular data not only with images
### Notes 
This repo contains 2 notebooks which are the same but the only difference that one uses binary cross entropy as the loss function of the discriminator and the other uses wistern loss function 
## Overview
Fake task attack is critical for Mobile Crowdsensing system (MCS) that aim to clog the sensing servers in
the MCS platform and drain more energy from participants’ smart devices. Typically, fake tasks are
created by empirical model such as CrowdSenSim tool. Recently, cyber criminals deploy more intelligent
mechanisms to create attacks. Generative Adversarial Network (GAN) is one of the most powerful
techniques to generate synthetic samples. GAN considers the entire data in the training dataset to
create similar samples. This project aims to use GAN to create fake tasks and verify fake task detection
performance.<br>

## Important dependencies 
```python
pip install numpy 
pip install tensorflow-gpu==2.9.1
pip install pandas 
pip install seaborn 
pip install matplotlib 
pip install sklearn
pip install imbalanced-learn
```

## Project Main steps
1. Download MCS dataset which and Split the dataset into training dataset (80%) and test dataset (20%)
2. Implement classic classifiers (Adaboost and RF) and train them
3. Verify detection performance using test dataset and present results comparison in bar chart
4. Implement a CGAN model and train it.
5. Generate synthetic fake tasks via Generator network in CGAN after the training procedure
6. Mix the generated fake tasks with the original test dataset to obtain a new test dataset
7. Obtain Adaboost and RF detection performance using the new test dataset and present results in
bar chart
8. Consider the Discriminator to as the first level classifier
and RF/Adaboost as the second level classifier
![Project steps](https://drive.google.com/uc?export=view&id=1YuHxXGr96Zgg2h5zbb_uO4ejviF8cEo2)

## Results 
**The generated tasks from the generator are robust and succussed to fault the
classic ML algorithms because it is tried to generate tasks very close to the real
one, so the models can’t determine it and the accuracies has been decreased
from 0.92 to 0.575 in the Adaboost model and has been decreased from 0.993 to
0.590 in the Random Forest model.<br>
In the cascade approach the discriminator helped the models because it can filter
the fake tasks, so after the filtering it out the accuracies increased again to 0.926
in Adaboost and to 0.993 in the Random Forest model and this result is
approximately one before mixing which means that the discriminator filtered**


![Original test set](https://drive.google.com/uc?export=view&id=1ZQSdpkSDZ-QCko7_9cE8iQDpWx7fYNnv)
![Mixed without disc](https://drive.google.com/uc?export=view&id=10F31icaCioeeXcFox_4R9GkNMSm3KVmA)
![Cascade framework](https://drive.google.com/uc?export=view&id=1ov0sRD1zQxonKinQjQOqzZsE4cvA-F06)

