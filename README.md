# nlp_customer_rev
This project focuses on developing an AI system capable of analyzing the sentiment or emotion behind text data. The goal is to build a model that can accurately classify text as positive, negative, or neutral. The system could be used for sentiment analysis of customer reviews, social media posts, or any other textual data.
 

1. Data Generation:
   - The script begins by generating a fake dataset using the `generate_fake_data` function. The `num_samples` variable determines the number of samples to generate.

2. Data Preprocessing:
   - The generated data is separated into phrases and corresponding sentiments.
   - The phrases are tokenized using the `Tokenizer` class from Keras, which assigns unique integer values to each word in the vocabulary.
   - The sequences of tokenized phrases are padded to a fixed length using the `pad_sequences` function from Keras. This ensures that all input sequences have the same length for training the RNN model.
   - The sentiments are converted into categorical labels using the `sentiment_labels` array.

3. Data Split:
   - The preprocessed data is split into training and testing sets using the specified `split_ratio`.

4. RNN Model Definition:
   - The RNN model is defined using the `Sequential` class from Keras.
   - The model consists of an embedding layer, which maps the tokenized phrases to dense vectors.
   - Two LSTM layers are stacked to capture sequential dependencies within the data. The first LSTM layer returns sequences, and the second one returns a single output.
   - Dropout layers are added after each LSTM layer to prevent overfitting.
   - A dense layer with ReLU activation is added to introduce non-linearity and increase model complexity.
   - The final dense layer with a softmax activation function outputs the predicted sentiment probabilities.

5. Model Compilation and Training:
   - The model is compiled with the specified loss function (`sparse_categorical_crossentropy`), optimizer (`Adam` with a specified learning rate), and evaluation metric (`accuracy`).
   - The model is trained using the training data, with the specified number of `epochs` and `batch_size`.
   - The model's performance is evaluated on the testing data.

6. Prediction:
   - The script includes a section for making predictions on new data (`new_phrases`).
   - The new phrases are tokenized and padded using the same tokenizer and maximum sequence length used for the training data.
   - The model predicts the sentiment probabilities for the new phrases.
   - The predicted sentiment labels are extracted using the `np.argmax` function and converted to their corresponding sentiment values.

7. Results Display:
   - The script prints the predicted sentiments for each new phrase, providing an output indicating the sentiment predicted by the RNN model.

By following these steps, the script generates fake data, preprocesses it, trains an RNN model with fine-tuned architecture and hyperparameters, and makes predictions on new data.
