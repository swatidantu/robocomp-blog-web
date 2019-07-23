# Create Your Own Text to Speech synthesizer with Ossian

## Introduction

There is growing demand for text-to-speech (TTS) in various industries as the world moves towards technologies that can interact with users more naturally. Many industries including gaming, film, appliances, and accessibility. As a result, there is a lot of needs to produce a variety of good quality voices in different languages. The TTS problem is challenging especially for low-resourced languages, because of the lack of data. Smaller text and audio corpora imply that more experiments might need to be done in order to get the most out of the available resources.

Tackling this problem for low-resourced languages usually requires close collaboration between computer scientists, who understand the algorithms and know how to utilize the tools, and linguists, who understand linguistic phenomena and can help provide linguistic resources required to improve the voices.

From our experience building voices for low-resourced languages, we have observed many pain points that prevent these researchers from conducting quick experiments and iterating on their existing baseline voices. These pain points include (i) the complexity of setting up initial voice building infrastructure, which often requires fairly strong technical background to setup and maintain (ii) the heterogeneous nature of different tools, which requires a non-trivial amount of effort to stitch the required pieces together to form a working pipeline for TTS research.

Text to speech synthesis is the process of converting a text string into a waveform. A conventional TTS system is usually made up of several components connected through a pipeline that includes a front-end-text-analyzer and a backend speech synthesizer. Each of the front end and backend is composed of several parts each performing one or more tasks. The front end is responsible for text analysis while the backend is responsible for converting features into audio.

The front end consists of text normalizers and a text-to-phoneme converter. Text normalizers tokenize phrases and convert numbers and texts in the raw text into written words. Text to phoneme converters takes the normalized text as an input and outputs phonemes which are symbolic representations of how the text is pronounced.

The output from the front end acts as an input for the backend which then converts the input into audio features then into sound. For example, for the statistical parametric speech synthesis, the backend uses statistical acoustic models to map linguistic features from the analyzer into compact acoustic features. These acoustic features are then inputted into a vocoder that converts these features to a waveform.

## Ossian
Ossian is a python based tool for automatically building speech synthesis front ends.The framework consists of a sequence of utterance processors, each of which accepts and enriches an XML representation of an utterance. The framework is designed to be flexible so that the nature and  number of processors and their roles can be configured by a user. A range of processors are supplied by the system, but it is also relatively easy to code new ones, Ossian supports the use of NN trained with the Merlin toolkit as duration and acoustic models. You can also use the HTS toolkit to build HMM.

### Ossian default processors

* proc no. 1  (word_splitter)
* proc no. 2  (segment_adder)
* proc no. 3  (word_vector_tagger)
* proc no. 4  (feature_dumper)
* proc no. 5  (acoustic_feature_extractor)
* proc no. 6  (aligner)
* proc no. 7  (pause_predictor)
* proc no. 8  (phrase_maker)
* proc no. 9  (duration_data_maker)
* proc no. 10 (labelmaker)
* proc no. 11 (duration_predictor)
* proc no. 12 (dnn_labelmaker)
* proc no. 13 (acoustic_predictor)


**In the next steps we will discuss how to install Ossian and train a model in a few minutes**


### Dependencies
```
**Perl 5** is required.

**Python 2.7** is required.
```

First of all you should do all following steps with **Python 2.7** not **Python 3.7**



### Getting the tools

Clone the Ossian github repository as follows:

```
git clone https://github.com/AhmedMadbouly/Ossian.git
```

This will create a directory called ```Ossian```, Let's move to ```Ossian``` directory ```cd Ossian```


Taking a look inside to see what you just cloned:
```
ahmed@ml:~/ossian$ ls
0_README.txt      LICENSE          remove-voice.sh  test-voice.sh
config_templates  make_release.sh  rules            tools
corpus            play-voice.sh    scripts          train-cpu.sh
doc               README.md        test             train-gpu.sh
install.sh        recipes          test_release.sh
```


** Instead of following the official documentation I wrote some scripts which will make all the next steps much easier also you may notice that there are Some Data ```corpus``` which we will use during the demo**



```
corpus/
└── en
    └── speakers
        └── lisa
            ├── txt
            │   ├── livingalone_01_benson_00014.txt
            │   ├── livingalone_01_benson_00016.txt
            │   ├── livingalone_01_benson_00018.txt
            │   ├── livingalone_01_benson_00024.txt
            │   ├── ****
            │   ├── ****
            │   ├── ****
            │   ├── livingalone_01_benson_00066.txt
            │   └── livingalone_01_benson_00169.txt
            └── wav
                ├── livingalone_01_benson_00014.wav
                ├── livingalone_01_benson_00016.wav
                ├── livingalone_01_benson_00018.wav
                ├── livingalone_01_benson_00024.wav
                ├── ****
                ├── ****
                ├── ****
                ├── livingalone_01_benson_00166.wav
                └── livingalone_01_benson_00169.wav
```


**```install.sh```**: Install and Compile Ossian

**```train-cpu.sh```** : Train Ossian Model on a CPU

**```train-gpu.sh```**: Train Ossian Model on a GPU

**```test-voice.sh```**: Synthesis new wave

**```play-voice.sh```**: Play new wave

**```remove-voice.sh```**: Remove Ossian Model



### Compile Ossian


Our configuration and compiling will be done by the ```install.sh``` script. 


```
ahmed@ml:~/ossian$ ./install.sh
...
...
...
Compile Ossian.......
Cloning into 'merlin'...
remote: Enumerating objects: 19, done.
remote: Counting objects: 100% (19/19), done.
remote: Compressing objects: 100% (19/19), done.
remote: Total 3502 (delta 6), reused 2 (delta 0), pack-reused 3483
Receiving objects: 100% (3502/3502), 6.68 MiB | 164.00 KiB/s, done.
Resolving deltas: 100% (2012/2012), done.
mkdir -p ./build/objs
g++ -O1 -g -Wall -fPIC -Isrc -o "build/objs/cheaptrick.o" -c "src/cheaptrick.cpp"
mkdir -p ./build/objs
g++ -O1 -g -Wall -fPIC -Isrc -o "build/objs/common.o" -c "src/common.cpp"
mkdir -p ./build/objs
g++ -O1 -g -Wall -fPIC -Isrc -o "build/objs/d4c.o" -c "src/d4c.cpp"
mkdir -p ./build/objs
g++ -O1 -g -Wall -fPIC -Isrc -o "build/objs/dio.o" -c "src/dio.cpp"
mkdir -p ./build/objs
g++ -O1 -g -Wall -fPIC -Isrc -o "build/objs/fft.o" -c "src/fft.cpp"
mkdir -p ./build/objs
g++ -O1 -g -Wall -fPIC -Isrc -o "build/objs/matlabfunctions.o" -c "src/matlabfunctions.cpp"
mkdir -p ./build/objs
g++ -O1 -g -Wall -fPIC -Isrc -o "build/objs/stonemask.o" -c "src/stonemask.cpp"
...
...
...
...
...
/usr/bin/install -c 'wav2raw.sh' '/home/ahmed/ossian/scripts/..//tools/bin/wav2raw.sh'
make[2]: Nothing to be done for 'install-data-am'.
make[2]: Leaving directory '/home/ahmed/ossian/tools/downloads/SPTK-3.6/script'
make[1]: Leaving directory '/home/ahmed/ossian/tools/downloads/SPTK-3.6/script'
make[1]: Entering directory '/home/ahmed/ossian/tools/downloads/SPTK-3.6'
make[2]: Entering directory '/home/ahmed/ossian/tools/downloads/SPTK-3.6'
make[2]: Nothing to be done for 'install-exec-am'.
test -z "/home/ahmed/ossian/scripts/..//tools/include" || /bin/mkdir -p "/home/ahmed/ossian/scripts/..//tools/include"
 /usr/bin/install -c -m 644 'include/SPTK.h' '/home/ahmed/ossian/scripts/..//tools/include/SPTK.h'
make[2]: Leaving directory '/home/ahmed/ossian/tools/downloads/SPTK-3.6'
make[1]: Leaving directory '/home/ahmed/ossian/tools/downloads/SPTK-3.6'
165
Installation completed.
```

This script has installed all dependencies and compiled ```Ossian```, cloned and compiled ```Merlin```, downloaded and compiled ```HTK```, and put everything in the tools directory. At this point, if you didn’t run into any problems, you should have a working installation of Ossian which can call both Merlin and HTK.




### Train Ossian Model

We’re going to train both an acoustic and duration model to train fancy-dancy DNNs for our speech synthesizer then it will take the Merlin DNNs we just made and format them for Ossian.


It will be done by ```train-gpu.sh``` or ```train-cpu.sh``` script. which takes two main arguments:

* The speaker dir name 
* The language dir name

e.g.
```
ahmed@ml:~/ossian$ ./install.sh  $LANG  $SPEAKER
```



```
ahmed@ml:~/ossian$ ./install.sh en lisa
 -- Gather corpus
 -- Train voice
/home/ahmed/ossian/train//en/speakers/lisa/naive_01_nn
/home/ahmed/ossian/voices//en/lisa/naive_01_nn
try loading config from python...
/home/ahmed/ossian/recipes/naive_01_nn.cfg
***
***
***
***
2.374075   2.0863028  1.664159   1.4150871  1.0233809  1.0554826
0.9608512  0.77851677 3.5460434  2.92667    3.0400178  2.826391
2.3268406 ]
Lock freed
Training Done.
```


### Synthesize New Audio

Now we’ve got everything in place to synthesize some speech with Ossian! We can use a sample sentence (text) to make synthesis new wave:



We will use ```test-voice.sh``` script. which takes three main arguments:

* The speaker dir name 
* The language dir name
* Test file

```
ahmed@ml:~/ossian$ ./test-voice.sh en lisa english.txt


/home/ahmed/ossian/train//en/speakers/lisa/naive_01_nn
/home/ahmed/ossian/voices//en/lisa/naive_01_nn
try loading config from python...

***
***
***
***

=  proc no. 1 (word_splitter)  ==
p 
==  proc no. 2 (segment_adder)  ==
p 
==  proc no. 3 (word_vector_tagger)  ==
p 
==  proc no. 4 (pause_predictor)  ==
p 
==  proc no. 5 (phrase_maker)  ==
p 
==  proc no. 6 (labelmaker)  ==
p 
==  proc no. 7 (duration_predictor)  ==
p 1

***
***
***

/home/ahmed/ossian//tools/bin//synth 2048.0 48000 /tmp/tmp_d.lf0 /tmp/tmp.spec /tmp/tmp_d.bap /tmp/tmp.resyn.wav
complete /tmp/tmp.resyn.wav.
Produced /home/ahmed/ossian/voices//en/lisa/naive_01_nn/output/wav/temp.wav
Warning: no lab produced for this utt
                     --> took 4.18 seconds
Done.
```

Now, You can listen to your beautiul new English speech inside the file ```./test/wav/```


Also you able to listen to your speech without saving it by runing  ```play-voice.sh```

which takes three main arguments:

* The speaker dir name 
* The language dir name
* text file


```
ahmed@ml:~/ossian$ ./play-voice.sh en lisa "Hi, How are you today"

/home/ahmed/ossian/train//en/speakers/lisa/naive_01_nn
/home/ahmed/ossian/voices//en/lisa/naive_01_nn
try loading config from python...

***
***
***
***

=  proc no. 1 (word_splitter)  ==
p 
==  proc no. 2 (segment_adder)  ==
p 
==  proc no. 3 (word_vector_tagger)  ==
p 
==  proc no. 4 (pause_predictor)  ==
p 
==  proc no. 5 (phrase_maker)  ==
p 
==  proc no. 6 (labelmaker)  ==
p 
==  proc no. 7 (duration_predictor)  ==
p 1

***
***
***

/home/ahmed/ossian/voices/en/lisa/naive_01_nn/output/wav/temp.wav:

 File Size: 117k      Bit Rate: 768k
  Encoding: Signed PCM    
  Channels: 1 @ 16-bit   
Samplerate: 48000Hz      
Replaygain: off         
  Duration: 00:00:01.22  

In:100%  00:00:01.22 [00:00:00.00] Out:58.3k [      |      ] Hd:0.0 Clip:0    
Done.
                     --> took 2.15 seconds
Done.
```

### Remove Ossian Model

Sometimes you may need to make some updates on your model and retrain it therefore you are required to remove the previour model from ```train``` and ```voices``` directory


You can use ```remove-voice.sh``` script. which takes two main arguments:

* The speaker dir name 
* The language dir name


```
ahmed@ml:~/ossian$ ./remove-voice.sh en lisa

```

