# Text-Generator
Using a LSTM-based neural network to generate text based on an input seed text, providing predictions for the next word and generating new text sequences.

## Data Preparation:

Read the data from a CSV file named "fake_or_real_news.csv" containing text data.
Join all the text data into a single string.

## Tokenization:

Tokenize the joined text using the RegexpTokenizer from NLTK (Natural Language Toolkit).
Lowercase all tokens for consistency.

## Unique Token Indexing:

Identify unique tokens and assign each a unique index.

## Data Vectorization:

Prepare input and output data for the LSTM model:
Create input sequences of length n_words (defaulted to 10).
Generate corresponding output sequences.
Convert input and output sequences into binary matrices where each row represents a sequence and each column represents a token, with a value of 1 indicating the presence of the token.

## Model Construction:

Build a sequential LSTM model using Keras:
Add two LSTM layers with 128 units each for sequence processing.
Add a Dense layer with softmax activation for outputting probabilities for each token.
Compile the model using categorical cross-entropy loss and RMSprop optimizer.

## Model Training:

Train the LSTM model using the prepared input and output data:
Fit the model to the data with a batch size of 128, for 10 epochs.
Monitor training progress and store history.

## Model Saving:

Save the trained model to a file named "textgenmodel_two.keras".

## Model Loading:

Load the trained model from the saved file.

## Prediction Function:

Define a function (predict_next_word) to predict the next word given an input text;
Tokenize the input text.
Convert tokens into input format.
Use the model to predict the probabilities of next words.
Return the indices of the top n_best predicted words.

## Text Generation Function:

Define a function (generate_text) to generate text given an input seed text:
Split the input text into tokens.
Generate the next word based on the input text and model predictions.
Append the predicted word to the input text and repeat the process until the desired number of words is generated.
Return the generated text.

## Text Generation Example:

Generate a sample text sequence by calling the generate_text function with an input seed text and desired number of words.
