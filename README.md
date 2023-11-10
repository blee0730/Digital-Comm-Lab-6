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
| 1.582 V | 0.033 V | 47.93 | 33.64 | 1.583 V | 47.96 | 31.619 |

Question 4: What is the signal-to-noise ratio (the ratio not the decibel) actually telling you?

This is the ratio between the signal and the noise which tells us whether there is more noise than signal or vice versa.

Question 5: Why are the two signal-to-noise ratios almost identical even though they've been calculated in different ways?

They are almost identical because the signal + noise voltage was very similar to the voltage as the noise was set to be small at -20dBs.

Question 6: What would you expect to happen to the signal-to-noise ratio figures if the Noise Generator module's -6dB or 0dB outputs are used?

The SNR would decrease providing a worse result as the noise would now be overtaking the signal.

Question 7: What other change to the signal-to-noise figures would you expect to see if you used the Noise Generator module's other outputs?

Not only would the SNR change but the noise voltage as well as the signal + noise voltage would also increase.

For this next part and table the noise input was increased from -20dBs to 0dBs to confirm whether the answer for question 6 and 7 were accurate or not.

Table 2

| Signal Voltage | Noise Voltage | SNR | SNR (dB) | Signal + Noise Voltage | Alternate SNR | Alternate SNR (dB) |
| :--:| :--: | :--: | :--: | :--: | :--: | :--: |
| See Table 1 | 0.313 V | 5.054 | 14.073 | 1.609 V | 5.141 | 14.22 |

As shown by the table the answers to question 6 and 7 are confirmed as the SNR drastically decreased as the noise and signal+noise voltages increased.

### Part D - Eye Diagrams

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/8c05b5af-c51a-4631-b97f-26849c142605)

This is the block diagram used for this part of the lab to obtain different eye diagrams. This is very simiar to the first few block diagrams as the master signal changes to the VCO module and everything else stays the same.

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/127500eb-5240-4663-9abb-ee4cca9325a4)

This is the signal with -20dBs of noise in the system and the eyes are clear and visible.

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/e18b6c55-39ce-44c7-ad18-4183f61cbf17)

This is the signal with -6dBs of noise and the eye's are already bigger and more distorted.

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/d0049328-aaa3-4c66-9b47-91441ce6a390)

This is the signal with 0dBs of noise and the eyes are incredibly large compared to before.

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/b3ad25aa-9cc9-4b84-a1b7-b4830802d55a)

As a reference this is the digital signal's eye diagram that shows the ideal case.

Question 8: What is the relationship between the level of noise that the channel introduces to the digital data signal and the size of the Eye Diagram's eyes?

The more noise that is put into the system the bigger the eyes get as shown by the pictures above.

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/7f005dbd-2b26-40f7-a778-26e8ccf1420f)

This is the eye diagram when the VCO module's frequency was moved to have five eyes within one eye.

Question 9: What is the relationship between the digital data signal's bit-clock and the size of the Eye Diagram's eyes?

The more you crank up the frequency of the VCO module the worse the eye diagrams look similar to adding more noise and moves the eye diagram forwards or backwards.

## BER
### Part A - Characterising the frequency response of the Baseband LPF module

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/ea3adbdd-ca0e-4b99-80cb-e0d67d3d140a)

This is the block diagram used for this part which was mainly to understand and characterise the frequency response of the Baseband LPF module such as where the cutoff frequency is.

| Table 1 | Input Voltage | Output Voltage | Gain (in dB) |
| :--:| :--: | :--: | :--: |
| 10 Hz | 4 V | 3.5 V | 1.160 |
| 50 Hz | | 3.5 V | 1.160 |
| 100 Hz | | 3.5 V | 1.160 |
| 500 Hz | | 3.4 V | 1.412 |
| 1 kHz | | 3.2 V | 1.938 |
| 1.5 kHz | | 2.8 V | 3.098 |
| 2 kHz | | 1.9 V | 6.466 |
| 2.5 kHz | | 1.0 V | 12.041 |
| 3 kHz | | 0.5 V | 18.062 |
| 3.5 kHz | | 0.2 V | 26.021 |

