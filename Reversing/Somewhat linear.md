# Somewhat linear

The flag of this challenge ironically tells a lot about the way I solved it: prompting the problem to ChatGPT, which wrote for me the solution script below to get the original .wav file containing the spelling of the flag:

```python
import soundfile as sf
import numpy as np

#Read the "shuffled_flag.wav" and "impulse_response.wav" files using the soundfile module
shuffled_flag, rate = sf.read('shuffled_flag.wav')
impulse_response, rate = sf.read('impulse_response.wav')

#Compute the frequency response of the impulse response
impulse_response_freq = np.fft.rfft(impulse_response)
#Divide the frequency spectrum of the shuffled flag file by the frequency response of the impulse response
original_signal_freq = np.fft.rfft(shuffled_flag) / impulse_response_freq
#Inverse Fourier transform the frequency spectrum to obtain the original signal in the time domain:
original_signal = np.fft.irfft(original_signal_freq)

#Write the original signal to a file using the soundfile module
sf.write('original_flag.wav', original_signal, rate)
```

## HTB{th1s_w@s_l0w_eff0rt}
