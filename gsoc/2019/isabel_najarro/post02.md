# We have a new component!
For this first delivery, it has been used the library mentioned on the proposal, creating a new component in RoboComp. In this case, it has been used the library **Pyttsx3** available at Python 2 and Python 3 and it offers the possibility that have a Text to Speech (TTS) without internet connection and it has many languages available. Also, it can change the audio rate or volume. The tool has not given problems when it comes to work and we have been able to test it.

Besides, it has made a preview of what will be the functionality of not including a phrase to **the robot and that can greet and say bye to you,** in this case, have carried out methods of greetings and farewells through the random library and a list of phrases both welcome and farewell.

## Test
To test this tool it has been put in the default language, English, and check that his voice is very artificial. After this, it has been tested with another voices availables and not many differences have been found with respect to the default one. As the voices available for each language are variable, we have gone on to test the tool by changing the language to Spanish. After testing it we have reached the conclusion that all available voices are too artificial for a robot that is in contact with children and the library used must be changed.

## Conclusions
As we mentioned in the Test section, we have decided to change the project focus and change the library used through a neural network called Tacotron. This neural network is passed some text files and audios reading these texts and after training, we will have a trained neural network with voice to which we will pass the phrases that the robot will have to read. This output voice will be modulated to get a tone adapted to children.

