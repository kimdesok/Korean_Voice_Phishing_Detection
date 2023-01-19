[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/selfcontrol7/Korean_Voice_Phishing_Detection/HEAD)

# AI-based Voice Phishing Detection in Korean Texts
Several machine learning and deep learning methods were developed to classify texts in Korean involved with voice phishing [1][2].
This repository is organized as below:
- **Attention** : contains source codes for investigating mostly an attention-based detection model and comparing its performance to other models such as CNN-BiSLTM, BiLSTM, LSTM, and CNN models 
- **Data_Collection_Preprocessing** : contains source codes for preprocessing raw data and create the datasets 
- **KoBERT** : contains source codes for implementing a KoBERT detection model
- **ML_DL_models** : contains  source codes for implementing a shadow ML and DL models

## Classification of Voice Phishing Texts vs. Normal Phone Conversation Texts
### A. Attention-based CNN-BiLSTM model
This model has been implemented in a script named 'Att-Based CNN-BiLSTM for Detecting Korean Vishing.ipynb' available at https://github.com/selfcontrol7/Korean_Voice_Phishing_Detection/tree/main/Attention (the original repository created by the first author[1][2])

Several minor things to mind before a fully blown execution of the script: <br>

1) Two text input files are required (that are NOT provided at the repo: One contains non vishing tokens and the orther contains vishing tokens.  <br>
For this step, outfile_space_20230117.npz needs to be loaded and is available at https://github.com/kimdesok/Korean_Voice_Phishing_Detection/tree/main/Attention. <br>

2) To evaluate the performance of a trained model, the model needs to be (re)compiled just before 'model.evaluate()' command.

> model = load_model(model_path, custom_objects=create_custom_objects()) <br>
> **model.compile(loss = "categorical_crossentropy", optimizer = Adam(learning_rate=learning_rate, decay=learning_decay), metrics = ['accuracy'])** <br>
> model.evaluate(X_test, y_test) <br>

3) Tensorflow version 2.4 and python 3.7 were installed (See the updated 'requirement.txt' for more installation). <br>

The figures below show the loss, accuracy, and the classification report of the attention based CNN-BiLSTM model. Training, validation, test sets were divided into 6.4:1.6:2. The training was performed by having epochs and patience set by 50 and 20, respectively.

<img src=https://user-images.githubusercontent.com/64822593/213472097-02add1a8-4da1-4dd8-b546-ec9268794b8b.png width="600" height="420">
<img src=https://user-images.githubusercontent.com/64822593/213472326-605c235b-b70e-4c20-9912-a4f0a09f25ad.png width="600" height="420">
<img src=https://user-images.githubusercontent.com/64822593/213472821-d3ec26e9-4cdf-4ef9-a9c0-42af44c4d48c.png width="600" height="300">

To compare the performance of the attention based model to other models such as CNN-BiLSTM, CNN, BiLSTM, and LSTM.
By training and testing the rest of the methods, a performance comparison table could be prepared:

<img src=https://user-images.githubusercontent.com/64822593/213474862-e1e0d612-0951-4e68-ba14-5df760748a4a.png width="600" height="400">
<img src=https://user-images.githubusercontent.com/64822593/213474593-fe9f122a-45d6-4872-a7ce-c10b2d041bfe.png width="600" height="400">

![image](https://user-images.githubusercontent.com/64822593/213474128-ab6c8ef6-aa8d-44e3-8500-25fc450b9efd.png)

The proposed attention based CNN-BiLSTM model and CNN-BiLSTM resulted in the same accuracy but the former converged slightly faster.
CNN-BiLSTM seems to fluctuate a quite bit at the beginning of training in terms of accuracy and loss but eventually converged at about 25 epochs.

Later on CNN, BiLSTM, and LSTM....

## References
[1] M. K. M. Boussougou, S. Jin, D. Chang, and D.-J. Park, “Korean Voice Phishing Text Classification Performance Analysis Using Machine Learning Techniques,” Proceedings of the Korea Information Processing Society Conference, pp. 297–299, Nov. 2021.<br>
[2] M. K. M. Boussougou and D.-J. Park, “Exploiting Korean Language Model to Improve Korean Voice Phishing Detection,” KIPS Transactions on Software and Data Engineering, vol. 11, no. 10, pp. 437–446, Oct. 2022. <br>
