# Wireless Communications - The Physical Layer

## A Digital Radio Communications System

- Data
- Source Encoder
  - removes some data (for compression)
  - _ADC_
- Channel Encoder
  - adds some data (for correction)
- Modulator
  - maps bits to symbols
  - e.g. _GPSK, QAM, MSK_
- Frequency Translation
  - _900MHz, 2GHz, ..._
- Amplifier
  - adds power (_10W, 100W, ..._)
- **Wireless Channel**
- Low-noice Amplifier
- Frequency Translation
- Demodulator
- Channel Decoder
  - correct
- Source Decoder
  - decompress
  - _DAC_
- Data

## Signals

- Digital computations are done in discrete time
  - **sampling** allows modern digital electronics to process, transmit, store and retrieve continuous-time signals

## Sampling

Refer to the slides:

- Fourier Transform
- Frequency Domain
- Nyquist Rate and Aliasing
  - https://en.wikipedia.org/wiki/Nyquist_frequency
  - https://en.wikipedia.org/wiki/Nyquist%E2%80%93Shannon_sampling_theorem
- Analogue-to-Digital Conversion
- Digital-to-Analogue Conversion
- **Euler's Formula**
- Amplitude Modulation
- Quadrature Amplitude Modulation
- ...

## Modulation

Modulation transforms the 0 frequency (baseband signal) to a higher frequency (passband signal).

- We use a higer frequency because **we want to use a smaller antenna.**

Fading Channel: when environment changes, the signal strength varies (fades) from time to time.

## Channel Noise

**Additive White Gaussian Noise (AWGN):** Noise added with the probability of Gaussian (Normal) Distribution.

Getting rid of the background noise: add a low-pass filter on the needed band.
