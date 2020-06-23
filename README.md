# Chatbot
Define a model for the chatbot system for our app, website &amp; social media handles.
Data Libraries
•	train_chatbot.py — the code for reading in the natural language data into a training set and using a Keras sequential neural network to create a model
•	chatgui.py — the code for cleaning up the responses based on the predictions from the model and creating a graphical interface for interacting with the chatbot
•	classes.pkl — a list of different types of classes of responses
•	words.pkl — a list of different words that could be used for pattern recognition
•	intents.json — abunch of JavaScript objects that lists different tags that correspond to different types of word patterns
•	chatbot_model.h5 — the actual model created by train_chatbot.py and used by chatgui.py
The training data has been initialized with a variable training. A giant nested list has been created which contains bags of words for each of our documents. We have a feature called output_row which simply acts as a key for the list. We then shuffle our training set and do a train-test-split, with the patterns being the X variable and the intents being the Y variable.
This particular network has 3 layers, with the first one having 128 neurons, the second one having 64 neurons, and the third one having the number of intents as the number of neurons. After the model is trained, the whole thing is turned into a numpy array and saved as chatbot_model.h5.
The clean_up_sentence() function cleans up any sentences from the input. This function is used in the bow() function, which takes the sentences that are cleaned up and creates a bag of words that are used for predicting classes (which are based off the results got from the training model earlier).
In the predict_class() function, an error threshold of 0.25 is used to avoid too much over fitting. This function will output a list of intents and the probabilities, their likelihood of matching the correct intent. The function getResponse() takes the list outputted and checks the json file and outputs the most response with the highest probability.
Finally the chatbot_response() takes in a message (which will be inputted through the chatbot GUI), predicts the class with the predict_class() function, puts the output list into getResponse(), then outputs the response. 
A function called send() sets up the basic functionality of the chatbot. If the message sent as input to the chatbot is not an empty string, the bot will output a response based on the chatbot_response() function.
After this, the chat window, scrollbar, and textbox can be created. All the components can be placed on the screen with simple coordinates and heights.
