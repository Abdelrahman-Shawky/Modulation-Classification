# Modulation Classification
This project analyzes the DeepSig Dataset: RadioML 2016.04C, which is a synthetic dataset generated with GNU Radio and classifies them into their 
corresponging modulation techniques using different architectures.

The 10 modulation Signals are : 8PSK, AM-DSC, BPSK, CPFSK, GFSK, PAM4, QAM16, QAM64, QPSK, WBFM
## Colab
https://colab.research.google.com/drive/1Z_x4DkwAnzvGqilIhVa9UYFfIuAwJttB?usp=sharing

## Dataset
Sig Dataset: RadioML 2016.04C

http://opendata.deepsig.io/datasets/2016.10/RML2016.10b.tar.bz2

A synthetic dataset, generated with GNU Radio, consisting of 11 modulations. This is a variable-SNR dataset with moderate LO drift, light fading, 
and numerous different labeled SNR increments for use in measuring performance across different signal and noise power scenarios.
- It has 1,200,000 samples
- Each sample is presented using two vectors each of them has 128 elements.
- The data is split into 70% for training/validation and 30% for testing.
- 5% of the training and validation dataset for validation.

## Feature Space
Every sample is presented using two vectors each of them has 128 elements. The dataset has the signals with raw features so we extracted more features from it which are:
- Raw time series as given (two channels)
- Integral in time (two channels)

## Architecture
Loss Used: Sparse Categorical Crossentropy<br>
Optimizaer: Adam Optimizer
### CNN
○ Input layer:  (2,128,1)

○ Convolutional layer with 64 filters of size (1x3)

○ Convolutional Layer with 16 filters of size (2x3)

○ Flatten Layer

○ Fully connected layer of size 128

○ Softmax output Layer: 10

### Vanilla RNN
○ Input layer: (2,128)

○ RNN layer: 128

○ Dense Relu: 128

○ Dense Relu: 64

○ Softmax output Layer: 10

### LSTM
○ Input layer: (2,128)

○ LSTM layer: 128

○ Flatten Layer

○ Dense Relu: 128

○ Softmax output Layer: 10

## Conclusion
The best model was found through hyperparameter tuning on the learning rate on the validation dataset, the highest accuracy was obtained using the CNN model trained
with the raw data features giving an accuracy of 57.0%. Further investigation showed an accuracy of 78% at
SNR=0dB, as well as, 81% at the highest SNR.

These findings demonstrate the potential of deep learning models for analyzing synthetic radio signals and suggest that the CNN network is a promising approach for this type of analysis. Further research is needed to optimize the performance of these models and to extend their applicability to other types of signals and scenarios.
## References
[1] T. O’shea, N. West “Radio Machine Learning Dataset Generation with GNU Radio”, https://pubs.gnuradio.org/index.php/grcon/article/download/11/10/

[2] T. O’Shea, J. Corgan, and T. Clancy “Convolutional Radio Modulation Recognition Networks” <br> https://arxiv.org/pdf/1602.04105.pdf

[3] N. West, T. O’shea “Deep Architectures for Modulation Recognition”,<br>
https://arxiv.org/pdf/1703.09197.pdf

[4] K. Karra, S. Kuzdeba, J. Peterson “Modulation recognition using hierarchical deep neural networks” <br> http://ieeexplore.ieee.org/document/7920746/?anchor=authors
