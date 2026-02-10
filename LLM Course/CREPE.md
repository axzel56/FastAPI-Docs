
Uses Librosa
`LibROSA` is a Python package for audio and music analysis. It provides various functions to quickly extract key audio features and metrics from the audio files.

```python
import librosa  
  
audio_data, sampling_rate = librosa.load('audio_file.wav', sr=22050)
```

### Properties after the audio file is loaded

 ### Duration:
 We can get the duration of the audio in seconds using `librosa.get_duration()`.
 `duration = librosa.get_duration(audio_data, sr=sampling_rate)`

 #### Sampling Rate:
 The sampling rate is the number of the samples per second captured from the analog signal. It is returned when loading the audio, but can also be accessed with `audio_data.sr`
 
  #### Shape:
  The shape of the` audio_data `array represents (length of audio, number of channels). We can access it with `audio_data.shape`.

 #### Plotting the Waveform
 We can visualize the audio waveform using 
 
 `librosa.display.waveplot()`. For example:
```python

import matplotlib.pyplot as plt

plt.figure(figsize = (12,4))
librosa.display.waveplot(audio_data, sr=sampling_rate)
plt.show()
```


