
**This Lecture:**
> Types of signals; Sampling, Quantisation, Aliasing and Nyquist-Shannon; Time domain, frequency domain and DFT; Convolution; Filtering

Quiz may involve SQL to query EHR data
Python for the time series data analyses

• Explain the key concepts of signals and signal types, including the distinction
between continuous, discrete, analogue, and digital signals as well as how these
relate to common health data sources
• Describe and apply the principles of sampling, including the Nyquist–Shannon
sampling theorem to avoid aliasing, to real-world time series health data.
• Interpret signals in both the time and frequency domains and know how the Discrete
Fourier Transform (DFT) can be used to convert from the time to the frequency domain.
• Explain the purpose and principles of signal filtering, distinguish between key filter types
(low-pass, high-pass, and band-pass), and describe common filter designs used to
implement them



## Signals

- quantity that can be varied in order to convey information, if no information then its noise

### Signal Processing

**Accelerometer signals**
**Photoplethysmogram**
**ECG**

### Types of Signals

Continuous-time signals - **signals that are specified for every value of time x**
Discrete-time signals - **signals that are specified at discrete values of time x**
Analogue signals - **signals can have any value over a continuous range**
Digital signals - **signals whose amplitude is restricted to a finite number of values**

### Aliasing

- occurs when a signal is samples at too low a rate, causing higher-frequency components to appear as lower frequencies in the samples data

### Nyquist-Shannon

$f_s >= 2fmax$

sampling rate, double Hz to capture information

### Quantisation
Q(.)
may introduce quantise error, which the difference between the actual analogue value and the quantise digital value

usually use uniform quantisation
### time domain, frequency domain

Time, over time

Frequency 
focus is on how the signals energy is distributed across different frequencies

DFT - transform signal from time to frequency
IDFT - reverse operation

### Signal Composing

map continuous signal into sign and cosign components
always have a phase and some amplitude

DFT, the Fourier series shows that any continuous periodic signals can be expressed as a sum of sinusoids

FFT, a fast algorithm for computing DFT, complexity O(NlogN)

```python
import numpy as np
import scipy as fft

# Parameters
22 / 39
f = 10 # s i g n a l frequency (Hz)
d t = 1/200 # sampling period  
durat i on = 1 # s i g n a l durat i on ( s )

# time domain s i g n a l - s i n e wave
t = np.arange(0, d u r a t i o n , d t )
x = n p . s i n ( 2 * n p . p i * f * t )

# convert t o frequency domain s i gn a l
xf = f f t . f f t ( x )
N = l e n ( x f )
f r e q = f f t . f f t f r e q ( N , d t )
magnitude = np.abs(xf)

```
