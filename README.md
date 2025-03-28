# Exp:3 Pulse-Code-Modulation
# Name: Keerthana S
# Reg No: 212223060122
### Aim:
To implement Pulse Code Modulation (PCM) for encoding and decoding a sinusoidal signal using quantization and to observe the output waveforms.

### Tools/Software Required:

 1. Python Software

-> Numpy Library

-> Matplotlib Library

### Program:
```python
import numpy as np
sampling_rate = 5000  
frequency = 50  
duration = 0.1  
quantization_levels = 16
t = np.linspace(0, duration, int(sampling_rate * duration), endpoint=False)
message_signal = np.sin(2 * np.pi * frequency * t)
clock_signal = np.sign(np.sin(2 * np.pi * 200 * t))  
quantization_step = (max(message_signal) - min(message_signal)) / quantization_levels
quantized_signal = np.round(message_signal / quantization_step) * quantization_step
pcm_signal = (quantized_signal - min(quantized_signal)) / quantization_step
pcm_signal = pcm_signal.astype(int)
plt.figure(figsize=(12, 10))
plt.subplot(4, 1, 1)
plt.plot(t, message_signal, label="Message Signal (Analog)", color='blue')
plt.title("Message Signal (Analog)")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)
plt.subplot(4, 1, 2)
plt.plot(t, clock_signal, label="Clock Signal (Increased Frequency)",color='green')
plt.title("Clock Signal (Increased Frequency)")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)
plt.subplot(4, 1, 3)
plt.step(t, quantized_signal, label="PCM Modulated Signal", color='red')
plt.title("PCM Modulated Signal (Quantized)")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)
plt.subplot(4, 1, 4)
plt.plot(t, quantized_signal, label="Signal Demodulation", color='purple', linestyle='--')
plt.title("Signal Without Demodulation")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)
plt.tight_layout()
plt.show()
```
### Output Waveform:

<img width="871" alt="image" src="https://github.com/user-attachments/assets/d78349ec-4e25-45a8-8e2e-f2b90004c576" />

<img width="872" alt="image" src="https://github.com/user-attachments/assets/e6ca4ceb-8585-4c05-b467-153ce173363a" />

<img width="882" alt="image" src="https://github.com/user-attachments/assets/12550ba4-fd9a-4a8a-acb0-660c611a4e20" />

<img width="873" alt="image" src="https://github.com/user-attachments/assets/8f0bc45f-b120-404c-9950-5c1f58173502" />

### Results:

The PCM encoding process successfully quantized the original sine wave into 16 levels.

The demodulated signal closely resembled the original signal with minor quantization noise.

The output waveforms validated the functioning of PCM in digital communication systems.
