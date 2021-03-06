# Stellar label estimation using deep learning.
This repository contains code to estimate stellar labels.


## Eksperiments
In order to run the code, change name of datafile in dataloader.py
### Unsupervised learning models

```
cd src
python denoising.py --name DAE --latentdim 10 --learningrate 3e-4 --num_epochs 750 --model_type DAE1d --batch_size 256 --noise_level 0.01
```

### Supervised learning models
#### Simple resnet
```
cd src
python main.py --name MODELNAME --learningrate 1e-4 --convolutions [128,128,128,128,128] --kernel_size [7,7,7,7,7] --epochs 500 --hiddenlayer [1024,1024,512] --model_type bayes --dropout 0.3 --SGD TRUE --noise_level 0.01
```
#### Model with denoising
```
cd src
python3 main.py --name noisefreeresenet --learningrate 1e-4 --convolutions [128,128,128,128,128] --kernel_size [7,7,7,7,7] --epochs 500 --hiddenlayer [1024,1024,512] --model_type bayes --dropout 0.3 --SGD TRUE --noise_level 0.01 --denoise_latent 10 --denoise DAE1d
```
#### Attention model
```
cd src
python3 main.py --name attentionnetwork --learningrate 1e-4--epochs 500 --hiddenlayer [1024,1024,512] --model_type bAttnVGG --batch_size 128 --noise_level 0.01 --SGD TRUE 
```
