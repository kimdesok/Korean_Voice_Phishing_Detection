## Classification of Voice Phishing Texts vs. Normal Phone Conversation Texts
A. Attention-based CNN-BiLSTM model

This model has been implemented in a script named 'Att-Based CNN-BiLSTM for Detecting Korean Vishing.ipynb' available at https://github.com/selfcontrol7/Korean_Voice_Phishing_Detection/tree/main/Attention (the original repository created by the first author)

Several minor things to mind before a fully blown execution of the script:
1)Two text input files are required (that are NOT provided at the repo: One contains non vishing tokens and the orther contains vishing tokens.  
For this step, outfile_space_20230117.npz needs to be loaded and is available at https://github.com/kimdesok/Korean_Voice_Phishing_Detection/tree/main/Attention.
2) To evaluate the performance of a trained model, the model needs to be (re)compiled just before 'model.evaluate()' command.

> model = load_model(model_path, custom_objects=create_custom_objects()) <br>
> **model.compile(loss = "categorical_crossentropy", optimizer = Adam(learning_rate=learning_rate, decay=learning_decay), metrics = ['accuracy'])** <br>
> model.evaluate(X_test, y_test) <br>

3) pip install textblob, pydot, and graphviz (See the updated 'requirement.txt')

The figures below show the loss, accuracy, and the classification report.

<img src=https://user-images.githubusercontent.com/64822593/213070074-4acfba7b-6ad6-4428-aefa-708c3422f0c5.png width="600" height="480">
<img src=https://user-images.githubusercontent.com/64822593/213069089-a971596c-01fb-4749-910c-1daec9c14c99.png width="600" height="480">
<img src=https://user-images.githubusercontent.com/64822593/213071179-4e845c8d-541c-4913-80d9-8130317c4592.png width="600" height="300">

To compare the performance of the attention based model to other models such as CNN-BiLSTM, CNN, BiLSTM, and LSTM.
By training and testing the rest of the methods, a performance comparison table could be prepared:

![image](https://user-images.githubusercontent.com/64822593/213104579-68a9daa7-7ce6-43ee-aef9-b8074f13f9a6.png)


The proposed attention based CNN-BiLSTM model and CNN-BiLSTM resulted in the same accuracy but the former converged a lot faster, about three times.
At the moment, it is not quite sure that this is a known fact.  CNN-BiLSTM seem to fluctuate a quite bit at the beginning in terms of accuracy and loss but eventually converged after about 25 epochs.

Later on CNN, BiLSTM, and LSTM....
