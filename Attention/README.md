## Text Classification of Voice Phishing Texts vs. Normal Phone Conversation Texts
A. Attention-based CNN-BiLSTM model

This model has been implemented in Att-Based CNN-BiLSTM for Detecting Korean Vishing.ipynb available at https://github.com/selfcontrol7/Korean_Voice_Phishing_Detection/tree/main/Attention (the original repository created by the first author)

Several minor things to be minded:
1) data_npz_creation.ipynb needs to be executed to get a text file that contains non vishing tokens and another file that contains vishing tokens.  
For this step, outfile_space_20230117.npz was prepared and available at https://github.com/kimdesok/Korean_Voice_Phishing_Detection/tree/main/Attention.
2) To evaluate the performance of a trained model, the model needs to be (re)compiled just before 'model.evaluate()' command.

> model = load_model(model_path, custom_objects=create_custom_objects()) <br>
> **model.compile(loss = "categorical_crossentropy", optimizer = Adam(learning_rate=learning_rate, decay=learning_decay), metrics = ['accuracy'])** <br>
> model.evaluate(X_test, y_test)

The figures below show the loss, accuracy, and the classification report.

<img src=https://user-images.githubusercontent.com/64822593/213070074-4acfba7b-6ad6-4428-aefa-708c3422f0c5.png width="600" height="480">
<img src=https://user-images.githubusercontent.com/64822593/213069089-a971596c-01fb-4749-910c-1daec9c14c99.png width="600" height="480">
<img src=https://user-images.githubusercontent.com/64822593/213071179-4e845c8d-541c-4913-80d9-8130317c4592.png width="600" height="300">

To compare the performance of the attention based model to other models such a CNN-BiLSTM, CNN, and 
