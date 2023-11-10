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
| 10 Hz | 4 V | 3.5 V | -1.160 |
| 50 Hz | | 3.5 V | -1.160 |
| 100 Hz | | 3.5 V | -1.160 |
| 500 Hz | | 3.4 V | -1.412 |
| 1 kHz | | 3.2 V | -1.938 |
| 1.5 kHz | | 2.8 V | -3.098 |
| 2 kHz | | 1.9 V | -6.466 |
| 2.5 kHz | | 1.0 V | -12.041 |
| 3 kHz | | 0.5 V | -18.062 |
| 3.5 kHz | | 0.2 V | -26.021 |

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/007a072b-66bc-4bd5-9ed4-903bcaaf4489)

This is a sketch of the graph obtained using the table above.

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/ef67657d-ff3b-4685-91c7-0d0cf8b9a79a)

This is the actual response of the baseband LPF found using software. The sketch of the graph matches up well until the software starts making spikes in the response due to the higher frequencies.

Question 1: Use the graph to determine the Baseband LPF module's cut-off frequency.

This was done using the software as shown with the red line the cut off frequency is around 1.5 kHz which was also confirmed with the emona biskit manual.

### Part B - Setting up the signal and noise components for transmission over the baseband channel

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/0ccac025-d3b2-4e0a-9f2a-723829f4db22)

This is the block diagram used for the majority of this lab while changing where the probes are located. The master signal is feeding a clock into a sequence generator that creates a 31 bit sequence. This signal is added to a noise adder module along with noise that is generated by a noise generater and passed through a low pass filter. Before the noise is added to the signal it is added with a DC voltage from the variable DC module to control the amount of noise put into the system. Afterwards the entire added signal is passed through the Baseband LPF that was characterized in the previous part of the lab and through a buffer amplifier.

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/1569c2b7-9eb7-457e-a959-31cfc12c1619)

This is the response of this block diagram which shows the digital signal separate from the noise. The period is also shown in red on the time domain while the frequency domain shows the blue noise is a line meaning it is AWG.

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/7f33041b-d91b-4b83-926d-dc3351f93313)

This is the frequency response when the noise if filtered setting the cut off frequency of the LPF around 3.5 kHz.

Table 2

| NRZ - L voltage RMS | Noise voltage RMS | SNR (dB)|
| :-: | :-: | :-: |
| 1.9 V | 4.6 V | -7.9 |
| 1.9 V | 1.9 V | 0 |

As shown by the table above the SNR is worse when the noise is added vs when the noise is taken away leaving the signal to noise ratio = 0.

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/2bfdca8c-4d83-4f8b-b822-e8da82e13079)

This is the new block diagram with the probes moved to right before and right after the baseband filter.

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/93528a99-7eca-4170-ba06-adc19ad51834)

This is the response shown with the yellow being before the baseband filter and the blue being after.

Question 4: Why is the data signal on the output of the Baseband LPF module distorted?

As shown by the frequency response above the blue signal's harmonics are being cut off by the baseband LPF thus the signal is distorted.

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/44a40193-9240-456e-b9e4-d9bb05d210a2)

To prove the answer to question 4 the noise was disconnected and the signals were recompared and as shown the recovered signal is now simliar to the original digital signal.

Question 5: At what frequency should the attenuation of the Baseband LPF module's output signal (relative to the input signal) exceed -3dB?

The cut off frequency of the Baseband LPF module is aroun 1.6 kHz.

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/243d35aa-ea1b-42bb-9cd7-033374faa035)

This picture is showing the two waveform's maximum gain at the baseband LPF's cut off frequency of 1.6 kHz, the values are listed in the table below.

Table 3

| Channel A gain | Channel B gain | Difference |
| :-: | :-: | :-: |
| -17.235 dB | -23.015 dB | -5.78 dB |

### Part C - Setting the noisy signal to within ETT-101 system module limits

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/1bb3e5f3-bdb3-45d4-b183-8d135523dd78)

This is the block diagram used for this part moving the channel B probe to the output of the buffer. The purpose of this was to set the buffer's gain module to obtain an RMS voltage for the signal on its output of around 800mV. This sets the peak to peak voltage to around 4 V which is the maximum capacity for this hardware.

### Part D - Implementation and adjustment of the BER measurement system

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/16f3627f-7a54-497a-aad7-a451a194a65e)

This is the block diagram that connects to our previous block diagram to finally get to counting the bit errors in the signals.

![image](https://github.com/blee0730/Digital-Comm-Lab-6/assets/130094173/8e341e2a-186e-40ca-a881-419508e5951d)

This is the result of our block diagram with the bottom showing spikes which is the clock of the BER which is the interval the XOR gate checks for errors. A lot of the process for confirming whether the BER was working properly or not was skipped due to time constraints and a table was made with the data that was gathered.

Table 4

| Measured Signal V_RMS | Measured Noise V_RMS | SNR (dB) | Average of Measured Errors | Error Rate |
| :-: | :-: | :-: | :-: | :-: |
| 0.68 V | 0.45 V | 7.99 | | |
| | 0.85 V | 5.52 | 1075.33 | 0.129 (1/8) |
| | 0.9 V | 6.02 | 1390 | 0.166 (4/25) |
| | 1 V | 6.94 | 1768.66 | 0.212 (1/5) |

These values were obtained by moving the cut off frequency down thus cutting off more of the noise producing a larger BER and larger SNR. The maximum SNR reached with just the base signal RMS voltage and base noise RMS voltage is shown at the top. The numbers after in the measured noise column are from the combination of the signal and noise.
