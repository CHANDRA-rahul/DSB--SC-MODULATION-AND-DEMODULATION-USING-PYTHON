# DSB--SC-MODULATION-AND-DEMODULATION-USING-PYTHON

__AIM__:

To generate a Double Sideband Suppressed Carrier (DSB-SC) signal in Python (Google Colab), transmit it (optionally add noise), and recover the message using coherent (synchronous) demodulation with a low-pass filter. Observe time and frequency domain waveforms and measure demodulation performance

__APPARATUS REQUIRED__:

Google Colab (or any Python environment)

Python libraries: numpy, matplotlib, scipy (scipy.signal)

__Theory__:

DSB-SC signal: s(t) = m(t) · cos(2πf_c t)
Coherent demodulation: multiply received s(t) by a synchronized carrier cos(2πf_c t) then low-pass filter (LPF) to remove double-frequency components:

r(t) = s(t)·cos(2πf_c t) = m(t)·cos²(2πf_c t) = 0.5 m(t) + 0.5 m(t)·cos(4πf_c t)
LPF extracts 0.5·m(t) → scale by 2 to recover m(t).

__Procedure__:

1) Import libraries and set parameters
2) Define message and carrier signals
3) Generate DSB-SC signal (modulation)
4) View spectra (FFT) of message and DSB-SC
5) (Optional) Add noise
6) Coherent demodulation (multiply by synchronized carrier)
7) Low-pass filter to recover message

__Program__:
```
import numpy as np 
import matplotlib.pyplot as plt 
Am = 14.4
Fm = 450  
Ac = 28.8 
Fc = 4500 
Fs = 4500000 
t = np.arange(0, 2/Fm, 1/Fs) 
em = Am * np.sin(2 * np.pi * Fm * t) 
plt.subplot(3, 1, 1) 
plt.plot(t, em) 
plt.grid() 
ec = Ac * np.sin(2 * np.pi * Fc * t) 
plt.subplot(3, 1, 2) 
plt.plot(t, ec) 
plt.grid() 
edsbsc=((Am/2)*np.cos((2*np.pi*Fc*t)-(2*np.pi*Fm*t)))
((Am/2)*np.cos((2*np.pi*Fc*t)+(2*np.pi*Fm*t))) 
plt.subplot(3, 1, 3) 
plt.plot(t, edsbsc) 
plt.grid() 
plt.tight_layout() 
plt.show()
```

   __Tabulation__:

   <img width="1116" height="1202" alt="image" src="https://github.com/user-attachments/assets/2b48fd6c-4213-449d-a05b-190dc30a510e" />


   __Output__:

   <img width="787" height="583" alt="image" src="https://github.com/user-attachments/assets/8c57e05f-52d0-4a89-a9c3-5f88ba537ee3" />


   __Result__:

   The message signal, carrier signal, and phase/modulated (PM) signal will be display ed in modulated signal variations of the separate plots. The will show phase corresponding to the amplitude message signal.
