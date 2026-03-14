# EXP.NO.7-Simulation-of-Spread-Spectrum-Modulation-Techniques

11.Simulation of Spread Spectrum Modulation Techniques

# AIM
 To simulate the process of Direct Sequence Spread Spectrum (DSSS) modulation using Binary Phase Shift Keying (BPSK).
# SOFTWARE REQUIRED
COLAB USING PYTHON 
# ALGORITHMS
 1. Generate random binary data.
 2. Create a PN sequence of length 8.
 3. Perform BPSK modulation on the data (0 → -1, 1 → +1).
 4. Spread the BPSK modulated signal using the PN sequence.
 5. Modulate the spread signal using a BPSK carrier.
 6. Plot the DSSS spread signal and the BPSK modulated carrier waveform.
# PROGRAM
import numpy as np
import matplotlib.pyplot as plt

data = np.array([1,0,0,0])   # Data bits = 1000
chips = 8
bit_rate = 1000
carrier = 20000
fs = 160000
samples = int(fs/(bit_rate*chips))

pn = np.random.choice([-1,1],chips)

def bpsk(b):
    return 2*b-1

spread=[]
for b in data:
    spread.extend(bpsk(b)*pn)
spread=np.array(spread)

t=np.arange(len(spread)*samples)/fs
carrier_wave=np.cos(2*np.pi*carrier*t)
chip_samples=np.repeat(spread,samples)
signal=chip_samples*carrier_wave

print("Data Bits:",data)
print("PN Sequence:",pn)

plt.figure()
plt.step(range(len(spread)),spread)
plt.title("DSSS Spread Signal")
plt.grid()

plt.figure()
plt.plot(t,signal)
plt.title("BPSK Modulated Signal")
plt.grid()

plt.show()
# OUTPUT
 ![Screenshot 2025-05-15 152231](https://github.com/user-attachments/assets/91f434ce-3cec-45e6-a205-7b36488ca458)
# RESULT / CONCLUSIONS
The DSSS spread signal is displayed as a plot showing the baseband spread signal after applying the PN sequence. The BPSK modulated signal is shown as a plot of the BPSK
 modulated carrier waveform

