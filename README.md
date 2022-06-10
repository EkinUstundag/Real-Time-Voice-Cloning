In this repository, I tried to train a TTS or Voice-Cloning model for Turkish. The original project was for English language.
I mostly changed parts that differentiate between Turkish and English language. Such as the cleaners and the characters defined for language.

Original repo: https://github.com/CorentinJ/Real-Time-Voice-Cloning

Turkish dataset: https://www.openslr.org/resources/108/TR.tgz

I only trained the synthesizer. The encoder and vocoder are using the parameters from original repository.

After ~50K steps I got the attention layer. I trained around 105K steps for curiosity. Below image is at 103K steps
![attention_step_103000_sample_1](https://user-images.githubusercontent.com/47627265/173051017-1a2134ad-ccc5-466e-9852-4d0f05877c4e.png)

Below is the mel spectogram at 103K steps
![step-103000-mel-spectrogram_sample_1](https://user-images.githubusercontent.com/47627265/173051415-c4459088-8997-4ac4-8a04-bcc0f72234b2.png)

At this point model is good at converting Turkish text into sound. However the output sound does not like the sound that you give as input rather it is an overall average of all sounds that model has trained on.

I saw a comment that the model can be trained on a specific person's sound and kinda learn to imitate his/her sound too.
I used the model above at 103K steps as a pretrained model, since it can understand Turkish text, and trained on a specific person's voice.
I did not use any voice from the above dataset. This is because I need a lot more occurences, above dataset has too few voice samples per person. One of my friends created an amateur dataset where she read sentences from different books. It was around 10 - 15 minutes of voice.

This is the attention layer at 126K steps on top of 103K already so around ~240K in total
![attention_step_126000_sample_1](https://user-images.githubusercontent.com/47627265/173053689-5a442efb-532f-45f1-9f86-163791708d4f.png)

Below is the mel spectogram at 126K steps
![step-126000-mel-spectrogram_sample_1](https://user-images.githubusercontent.com/47627265/173053872-a7445c7e-6211-4c44-a0f6-45eb17453bb5.png)

 The output voice was actually similar to my friends voice. However it gets mechanical too quickly after 1 or 2 words.
 This is probably because the recordings were not perfect. In both my friend's recordings and recordings in above dataset there were lots of other voices besides the recording hardware (such as TV or some musical enstruments).
 
 I need better datasets to train. In addition, training the vocoder on a specific person can perfect the output if you would like to use it as a TTS. However, I would like a Voice-Cloning with a little input like some seconds, not 10 - 15 minutes of voice but I think models used in this repo becoming old. So, I will try with newer architectures.
