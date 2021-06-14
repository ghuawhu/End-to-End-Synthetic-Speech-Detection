# Ed-to-End Synthetic Speech Detection

## About
We present two light-weight neural network models, termed time-domain synthetic speech detection net (TSSDNet), having the classic ResNet and Inception Net style structures (Res-TSSDNet and Inc-TSSDNet), for end-to-end synthetic speech detection. They achieve the state-of-the-art performance in terms of equal error rate (EER) on ASVspoof 2019 challenge and are also shown to have promising generalization capability when tested on ASVspoof 2015. 

##Dataset
- ASVspoof 2019 LA partition. [link](https://datashare.ed.ac.uk/handle/10283/3336)
- ASVspoof 2015. [link](https://datashare.ed.ac.uk/handle/10283/853)
  
1. ASVspoof 2019 train set is used for training;
2. ASVspoof 2019 del set is used for model selection;
3. ASVspoof 2019 eval set is used for testing;
4. ASVspoof 2015 eval set is used for cross-dataset testing.

## Model Architecture
![](imgs/1.png)

## Main Results
![](imgs/2.png)

![](imgs/3.png)

## Usage
### Data Preparation 
```
ASVspoof15&19_LA_Data_Preparation.py
```
It generates 
1) equal-duration time domain raw waveform
2) 2D log power of constant Q transform

from ASVspoof2019 and ASVspoof2015 official datasets, respectively. The calculation of CQT is adopted from [Li et al. ICASSP 2021](https://github.com/ghuawhu/ASV-anti-spoofing-with-Res2Net).

### Training 
```
train.py
```
It supports training using 
1) standard cross-entropy vs weighted cross-entropy
2) standard train loader vs mixup regularization
3) 1D raw waveforms vs 2D CQT feature
4) ASVspoof 2019 training set vs ASVspoof 2015 training set

A train log will be generated, and trained models per epoch will be saved.

### Testing
```
test.py
```
It generates softmax accuracy, ROC curve, and EER.

## Citation Information
 > G. Hua, A. Teoh, and H. Zhang, “Towards end-to-end synthetic speech detection,” IEEE Signal Processing Letters, 2021.