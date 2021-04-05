# Speech-Enhancement



This repostiory builds an audio denoising system to attenuate noise.


For time-frequency decompositions, spectrograms are really useful representation. Here, audio is represented as 2D representing sequences of Short Time Fourier Transform (STFT) with time and frequency as axes, and brightness representing the strength of a frequency component at each time frame. STF outputs don't lose information about audi waveform and can recreate it with very minimal loss.

![Spectrogram](https://github.com/saty101/Speech-Enhancement/blob/main/images/spectro1.png?raw=true)


### Data
LibriSpeech dataset and UrbanNoise8K has been used. UrbanNoise dataset provides us with various background noises while the LibriSpeech dataset provides us clean speech.

### Model
U-Net style architecture has been applied which incolves downsampling layers that reduce the height and width of image and then it is umsampled. Here first upsampling is done using change of number of channels, 4 batchnorm and Relu and then the usual upsampling by transposed convolutions along with skip connections.

One spectrogram used is a simple STFT output that resulted in a complex-valued spectrogram and was represented as a two channeled image representing the real and imaginary parts. The other type involved only feeding the magnitude of the STFT as a one-channel image and receiving a magnitude spectrogram at the end. The phrase used for reconstruction was simply the initial STFT phase (phase does not change), as shown in the figure above.


### References
https://github.com/vbelz/Speech-enhancement

https://medium.com/@klintcho/

https://github.com/domerin0/rnn-speech/blob/master/util/dataprocessor.py

https://docs.google.com/presentation/d/1zzgNu_HbKL2iPkHS8-qhtDV20QfWt9lC3ZwPVZo8Rw0/pub?start=false&loop=false&delayms=3000#slide=id.g5a7a9806e_0_67

https://www.kaggle.com/parulpandey/eda-and-audio-processing-with-python/notebook
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
