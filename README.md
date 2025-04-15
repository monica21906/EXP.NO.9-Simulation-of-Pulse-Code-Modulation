# EXP.NO.9-Simulation-of-Pulse-Code-Modulation
9.Simulation of PCM

# AIM
```
To verify and simulate the pulse code modulation using colab software.
```
# SOFTWARE REQUIRED
```
colab software
```
# ALGORITHMS
```
Step1:Import required libraries (matplotlib.pyplot and numpy).
Step2:Set sampling rate, message frequency, duration, and quantization levels.
Step3:Create time array for the total signal duration.
Step4:Generate the message signal using a sine wave.
Step5:Generate a high-frequency clock signal using the sign of a sine wave.
Step6:Calculate the quantization step size from the message signal range.
Step7:Quantize the message signal by rounding to the nearest level.
Step8:Convert quantized signal into integer PCM values.
Step9:Plot the original analog message signal.
Step10:Plot the clock signal.
Step11:Plot the quantized signal as a step graph (PCM modulated).
Step12:Plot the quantized signal again as the demodulated output.
Step13:Show all plots together using tight layout.
```
# PROGRAM
```
import matplotlib.pyplot as plt
import numpy as np
sampling_rate = 5000 
frequency = 100
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
plt.plot(t, clock_signal, label="Clock Signal (Increased Frequency)", color='green')
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
# OUTPUT

![image](https://github.com/user-attachments/assets/58360e66-5d72-4629-beec-8609278e80fe)

# RESULT / CONCLUSIONS
```
Thus the pulse code modulation was successfully simulated and verified.
```

