# code

import matplotlib.pyplot as plt
import numpy as np
from scipy.fft import fft, fftfreq

data = np.loadtxt("S1L1E")

t = data[:,0]

amp_left = data[:,1]

amp_right = data[:,2]

plt.plot(time, amp_left, label="left pendula")
plt.plot(time, amp_right, label="right pendula")
plt.title("S1L1E time vs amplitude data plot")
plt.xlabel("time (s)")
plt.ylabel("amplitude")
plt.legend()
plt.show()

# fft attempt

npts=len(t)
FFT = abs(fft(amp_left))
freqs = fftfreq(npts, 0.0002)
plt.plot(freqs,(FFT), label= "peak is at 0.67 Hz")
plt.xlim(0,10)
plt.grid()
plt.title("S1L1E frequency vs amplitude plot for left pendula")
plt.xlabel("frequency (Hz)")
plt.ylabel(" amplitude")
plt.legend()
plt.show()

npts=len(t)
FFT = abs(fft(amp_right))
freqs = fftfreq(npts, 0.0002)
plt.plot(freqs,abs((FFT)), color = 'darkorange', label= "peak is at 0.67 Hz")
plt.grid()
plt.xlim(0,10)
plt.title("S1L1E frequency vs amplitude plot for right pendula")
plt.xlabel("frequency (Hz)")
plt.ylabel(" amplitude")
plt.legend()
plt.show()
