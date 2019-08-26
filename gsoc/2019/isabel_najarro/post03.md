# Be careful,the voice is taking shape!

For this second delivery the changes that were commented in the previous delivery have been carried out. The neural network used is Tacotron 2, an AI-powered speech synthesis system that can convert text to speech.

### Tacotron.
This neural network learns to pronounce according to the semantics of phrases, it takes into account punctuation signals and pauses, is able to overlook small spelling mistakes and can learn intonation and accentuation from dataset.
It uses two neural networks to achieve an humanized voice in text-to-speech (TTS) conversion:

 - The first one converts the text into an spectrogram or a visual representation of audio frequencies over time.
 - The second one, nicknamed WaveNet, reads this spectrogram and generates the corresponding audio.

## Train.
A computer with an *NVIDIA GeForce GTX 1080* graphics card was used for network training. When attempting to run the training, numerous problems were encountered with the versions that the network satisfied. Searching for the problems encountered it is eventually opted to use **Mimic2 from MycroftAI** which is based on Tacotron. The training of this one has been carried out in a container gpu of docker in which we have trained it and testing it during several steps to see its progress.

### Examples of training:
[Audio examples of the differents epochs](https://github.com/inajarrob/AudioSamples/tree/master)

## Conclussions:
With regard to the final delivery, it will be focused on connecting all components so that EBO has the ability to speak using the results obtained with the neural network in English.

