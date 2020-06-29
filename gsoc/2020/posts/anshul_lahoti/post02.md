## Work Updates

June 28,2020

In this article I will discussing about the speech capturing block ,speech enhancement block , transcriber , feature extraction and acoustic modelling. 

### Speech Capturing Block 

There are many ASR which are working on specified dataset. But we have to build ASR component for robots . So it is necessary that our component will work on live speeches. From this we can create our on datsets. We can creates Datasets in different ways like using microphone or without using microphone . 

### Speech Enhancement Block 

The speech signal that is recorded might not be clean in every case. Noisy speech will not give correct transcription when given as input to the recognition block. Hence ,noise removal (i.e. speech enhancement) needs to be performed. I am using Butterworth low pass filter to enhanced the speech files to increase the signal noise ratio (SNR). I have learn many type of denoising techniques while implementing speech enhancement block like - Kalmann filter , RLS filter and by using differnet features like MFCC , median etc. So this gives me opportunity to explore differnt types of filters. 

### Transcriber

Here transcriber consists of two parts: a producer that captures voice from microphone, and a consumer that converts this speech stream to text. These two execute in parallel. The audio recorder keeps producing chunks of the speech stream. The speech recognizer listens to this stream, consumes these chunks upon arrival and updates the transcribed text.
This transcriber is built by using deepspeech library or deepspeech API .This transcriber is useful to compare our live speech rcongition with already proposed. I have learn many things from this like - how to use an API for building models .

### Features Extraction

I have explore many types of speech related features  for speech recognition like - MFCC , PLP , LPCC , FBANK and Spectrogram . I have used MFCC and Spectrogram for building my models . 

### Acoustic Model 

DeepSpeech is composed of two main subsystems: an acoustic model and a decoder. The acoustic model is a deep neural network that receives audio features as inputs, and outputs character probabilities. The decoder uses a beam search algorithm to transform the character probabilities into textual transcripts that are then returned by the system.

### Expected Work done before First eval
 1. Speech Capturing Block
 2. Speech Enhancement Block
 3. Features Extraction
 
### Actual Work done before First eval
 1. Speech Capturing Block
 2. Speech Enhancement Block
 3. Transcriber
 4. Features Extraction
 5. Acoustic Model 
 
