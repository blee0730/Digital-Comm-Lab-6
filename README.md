# Digital-Comm-Lab-6
## Introduction
In this lab the SNR (Signal to Noise Ratio) and BER (Bit Error Rate) were explored. The SNR shows the ratio between the message signal and the amount of noise in that signal. The higher this ratio the better as this means the signal has a higher ratio than the noise making it easier to receive properly. The BER counts the number of errors in the digital message signal using an XOR gate with reference to a constant clock which means that the higher the number the worse the error is.
## SNR
### Part A - Adding Noise to a Signal
![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/9019c3a9-d00f-497d-9215-7545c1f15982)

This is the first block diagram used in this lab to generate a signal and add noise to it. The left hand side is what generates a digital signal using master signals and a sequence generator while the right side is what adds the noise to the system. The noise added to the system increases starting at -20dBs, to -6dBs, and 0dBs, the pictures are shown in order below.

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/7a71282e-034f-4927-a131-67e12c3d1938)

This is the signal with -20dBs of noise added to it which is the smallest amount of noise. The digital signal is still visibile even while the noise is added.

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/7bbf69ba-8f10-42a7-bffd-70c35ad9a4a8)

This is the signal with -6dBs of noise added to it. The digital signal is a lot less visible while the shape is still somewhat preserved.

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/e437dff8-f882-4e82-99c7-56ecbe4379cb)

This is the signal with 0dBs of noise added to it. The digital signal is not at all visible making it almost impossible to recover the signal.

Question 1: Based on its appearance, what type of noise is the Noise Generator module modelling?

This is AWG (Additive White Gausian) noise based on each of the fft's that show a near flat line as the signal.

Question 2: Which of the Noise Generator's outputs provides the most amount of noise?

The signal with the most amount of noise as stated many times before is the signal with 0dBs of noise added

### Part B - Band-limiting the noisy signal

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/9f4030dd-5dfd-4cf8-8526-bca3a5d9c020)

This is the block diagram used for part B which is taking the previous block diagram and putting the output through a baseband low pass filter.

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/0111f98b-4585-4f52-8222-220e97cb4b61)

This is the signal with -20dBs of noise added to it while going through the baseband filter. As shown in the frequency domain the noise that was once a flat line is not getting filtered out creating a cleaner signal.

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/38504879-e39f-4fac-a946-1378cdb6c097)

This is the signal with -6dBs of noise added to it while going through the baseband filter. This is a similar output to the -20dBs of noise since most of the noise is getting filtered out but it does have more bumps than the -20dBs.

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/e5b13097-23c5-46e2-b05b-879f09199091)

This is the signal with 0dBs of noise added to it while going through the baseband filter. This signal has many more ripples than the previous signals.

Question 3: Why doesn't the digital data signal look as "noisy" now as it did before?

As explained above the baseband filter is cutting off most of the noise making the data signal look less "noisy".

### Part C - Determining signal-to-noise ratio (SNR)
For this part of the lab a table was constructed to find the SNR by first finding the signal voltage by disconnecting the noise from the adder. Then doing the opposite and disconnecting the signal from the adder to find just the noise voltage (RMS values were used). Afterwards the SNR was found as both a ratio and in dBs. Finally the signal+noise voltage was found along with an alternate SNR as both a ratio and in dBs using the signal+noise value.

Table 1

| Signal Voltage | Noise Voltage | SNR | SNR (dB) | Signal + Noise Voltage | Alternate SNR | Alternate SNR (dB) |
| :--:| :--: | :--: | :--: | :--: | :--: | :--: |
| 1.582 V | 0.033 V | 47.93 V | 33.64 | 1.583 | 47.96 | 31.619 |

