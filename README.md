
# OFDM-Based Wireless Communication System

A MATLAB-based simulation of an **Orthogonal Frequency Division Multiplexing (OFDM) wireless communication system** incorporating **16-QAM, QPSK, AWGN noise, multipath fading, cyclic prefix, channel equalization, and BER performance analysis**.

---

## 📌 Project Overview

This project demonstrates the progressive development of an OFDM-based wireless communication system using MATLAB.

The system starts with basic digital modulation and is gradually extended to include important wireless communication concepts such as:

- 16-QAM modulation and demodulation
- QPSK modulation
- OFDM transmission and reception
- IFFT and FFT processing
- AWGN channel
- Cyclic Prefix (CP)
- Multipath channel
- Frequency-domain channel equalization
- BER versus SNR analysis
- QPSK versus 16-QAM comparison

The project was developed and simulated using **MATLAB Online**.

---

## 🛰️ System Architecture

```text
                         TRANSMITTER
                              │
                              ▼
                     Random Binary Data
                              │
                              ▼
                       QAM Modulation
                              │
                              ▼
                        OFDM Mapping
                              │
                              ▼
                             IFFT
                              │
                              ▼
                       Cyclic Prefix
                              │
                              ▼
                ┌─────────────────────────┐
                │     WIRELESS CHANNEL    │
                │                         │
                │      AWGN Noise         │
                │           +             │
                │    Multipath Fading     │
                └─────────────────────────┘
                              │
                              ▼
                   Cyclic Prefix Removal
                              │
                              ▼
                             FFT
                              │
                              ▼
                  Channel Equalization
                              │
                              ▼
                    QAM Demodulation
                              │
                              ▼
                       Received Bits
                              │
                              ▼
                       BER Calculation
````

---

# 📚 Project Development Stages

The complete project was developed in **8 stages**, with each stage introducing an additional concept in the OFDM wireless communication system.

---

## Stage 1 — 16-QAM Modulation and Demodulation

The first stage implements a basic **16-QAM communication system**.

### Implemented Concepts

* Random binary data generation
* 16-QAM modulation
* 16-QAM demodulation
* Constellation diagram
* BER calculation

### Result

The transmitted symbols were successfully recovered without errors in the simulated ideal channel.

```text
Number of bit errors = 0
BER = 0
```

### Documentation

📄 [View Stage 1 — 16-QAM PDF](stage1.pdf)

---

## Stage 2 — Basic OFDM System

The second stage introduces the basic OFDM transmitter and receiver.

### System Configuration

* 64 OFDM subcarriers
* 100 OFDM symbols
* 16-QAM modulation
* IFFT at the transmitter
* FFT at the receiver

### Processing

```text
Random Bits
     ↓
16-QAM
     ↓
64 Subcarriers
     ↓
IFFT
     ↓
Wireless Channel
     ↓
FFT
     ↓
16-QAM Demodulation
     ↓
BER
```

### Result

The OFDM system successfully recovered the transmitted data in the absence of channel impairments.

```text
BER = 0
```

### Documentation

📄 [View Stage 2 — Basic OFDM PDF](stage2ofdm.pdf)

---

## Stage 3 — OFDM over AWGN Channel

In this stage, **Additive White Gaussian Noise (AWGN)** is introduced to simulate a noisy wireless communication channel.

The system is evaluated over different SNR values.

### SNR Range

```text
0 dB → 5 dB → 10 dB → 15 dB → 20 dB → 25 dB
```

### BER Results

| SNR (dB) | Bit Errors |          BER |
| -------: | ---------: | -----------: |
|        0 |       7326 | 2.861719e-01 |
|        5 |       4118 | 1.608594e-01 |
|       10 |       1530 | 5.976563e-02 |
|       15 |        135 | 5.273438e-03 |
|       20 |          0 |            0 |
|       25 |          0 |            0 |

The simulation shows the relationship between **SNR and BER** for the OFDM system under AWGN.

### Documentation

📄 [View Stage 3 — AWGN PDF](stage3.pdf)

---

## Stage 4 — Cyclic Prefix

The fourth stage introduces a **Cyclic Prefix (CP)** into the OFDM system.

A cyclic prefix is added to each OFDM symbol before transmission.

### System Configuration

```text
Number of Subcarriers = 64
Cyclic Prefix Length  = 16
```

### Processing

```text
OFDM Symbol
     │
     ▼
Take last 16 samples
     │
     ▼
Add them to the beginning
     │
     ▼
OFDM Symbol + Cyclic Prefix
```

At the receiver, the cyclic prefix is removed before FFT processing.

### Result

The transmitted data was successfully recovered.

```text
BER = 0
```

### Documentation

📄 [View Stage 4 — Cyclic Prefix PDF](stage4.pdf)

---

## Stage 5 — Multipath Channel and Equalization

In this stage, a **multipath wireless channel** is introduced.

The channel impulse response used in the simulation is:

```text
h = [1 0.5 0.3]
```

This represents multiple propagation paths between the transmitter and receiver.

### Receiver Processing

After removing the cyclic prefix and performing FFT, the received signal is equalized using the frequency response of the channel.

```text
Received OFDM Signal
          │
          ▼
     Remove CP
          │
          ▼
         FFT
          │
          ▼
 Channel Equalization
          │
          ▼
   QAM Demodulation
          │
          ▼
         BER
```

### Result

The transmitted data was successfully recovered after channel equalization.

```text
BER = 0
```

The stage also includes the frequency response of the multipath channel and the received 16-QAM constellation.

### Documentation

📄 [View Stage 5 — Multipath Channel PDF](stage5.pdf)

---

## Stage 6 — Multipath + AWGN + Equalization

The sixth stage combines the two major channel impairments:

* Multipath propagation
* AWGN noise

Channel equalization is then applied at the receiver.

### Channel

```text
h = [1 0.5 0.3]
```

### SNR Range

```text
0 dB → 25 dB
```

### BER Results

| SNR (dB) | Bit Errors |          BER |
| -------: | ---------: | -----------: |
|        0 |       8014 | 3.130469e-01 |
|        5 |       4943 | 1.930859e-01 |
|       10 |       2352 | 9.187500e-02 |
|       15 |        642 | 2.507812e-02 |
|       20 |         34 | 1.328125e-03 |
|       25 |          0 |            0 |

The results demonstrate the effect of combined **multipath propagation and AWGN** on OFDM communication.

### Documentation

📄 [View Stage 6 — Multipath + AWGN PDF](stage6.pdf)

---

## Stage 7 — Wireless Channel Performance Comparison

The seventh stage compares the BER performance under three different channel conditions.

### Cases Compared

1. **AWGN only**
2. **Multipath + AWGN without equalization**
3. **Multipath + AWGN with equalization**

### BER Results

| SNR (dB) |  AWGN Only | Multipath + AWGN (No EQ) | Multipath + AWGN (With EQ) |
| -------: | ---------: | -----------------------: | -------------------------: |
|        0 | 2.8805e-01 |               3.3633e-01 |                 3.1020e-01 |
|        5 | 1.6543e-01 |               2.5250e-01 |                 1.9801e-01 |
|       10 | 5.8359e-02 |               1.9535e-01 |                 9.3398e-02 |
|       15 | 4.6875e-03 |               1.6469e-01 |                 2.6016e-02 |
|       20 |          0 |               1.4789e-01 |                 9.3750e-04 |
|       25 |          0 |               1.3836e-01 |                          0 |

This comparison demonstrates the effect of multipath distortion and the role of channel equalization in recovering the transmitted signal.

### Documentation

📄 [View Stage 7 — Channel Comparison PDF](stage7.pdf)

---

## Stage 8 — QPSK vs 16-QAM

The final stage compares two modulation schemes:

* QPSK
* 16-QAM

Both modulation schemes are implemented in an OFDM system and evaluated using BER versus SNR.

### BER Results

| SNR (dB) |     QPSK BER |   16-QAM BER |
| -------: | -----------: | -----------: |
|        0 | 1.604687e-01 | 2.872266e-01 |
|        5 | 3.789062e-02 | 1.631641e-01 |
|       10 | 1.093750e-03 | 6.156250e-02 |
|       15 |            0 | 4.687500e-03 |
|       20 |            0 |            0 |
|       25 |            0 |            0 |

The results provide a comparison of BER performance between QPSK and 16-QAM at different SNR values.

### Documentation

📄 [View Stage 8 — QPSK vs 16-QAM PDF](stage8.pdf)

---

# 📊 Overall Project Results

The simulations demonstrate the progressive behavior of an OFDM wireless communication system.

### Key observations

* Increasing SNR reduces BER in the simulated AWGN channel.
* Multipath propagation introduces additional distortion.
* Cyclic Prefix enables the OFDM system to handle the modeled multipath channel.
* Frequency-domain equalization is used to compensate for the channel response.
* QPSK and 16-QAM exhibit different BER behavior under the tested SNR conditions.
* The complete system progresses from an ideal modulation system to a more realistic wireless-channel model.

---

# ⚙️ System Parameters

| Parameter              | Value            |
| ---------------------- | ---------------- |
| Simulation Tool        | MATLAB           |
| Modulation Schemes     | 16-QAM, QPSK     |
| OFDM Subcarriers       | 64               |
| Number of OFDM Symbols | 100              |
| Cyclic Prefix Length   | 16 samples       |
| SNR Range              | 0–25 dB          |
| SNR Step               | 5 dB             |
| Multipath Channel      | `[1 0.5 0.3]`    |
| Equalization           | Frequency-domain |
| BER Analysis           | Yes              |

---

# 🛠️ Technologies and Concepts

### Software

* MATLAB
* MATLAB Online

### Communication Concepts

* Digital Communication
* OFDM
* 16-QAM
* QPSK
* AWGN
* Multipath Fading
* Cyclic Prefix
* Channel Equalization
* BER Analysis
* SNR Analysis
* FFT
* IFFT

---

# 📁 Repository Structure

```text
OFDM-Wireless-Communication-System/
│
├── README.md
│
├── stage1.pdf
├── stage2ofdm.pdf
├── stage3.pdf
├── stage4.pdf
├── stage5.pdf
├── stage6.pdf
├── stage7.pdf
└── stage8.pdf
```

Each PDF contains the corresponding stage's **MATLAB code, simulation results, graphs, and screenshots**.

> **Note:** The project was developed using MATLAB Online. The downloadable `.m` source files were not available in the current trial environment, so the MATLAB implementations and results are documented in the stage-wise PDF files included in this repository.

---

# 🎯 Learning Outcomes

This project provided practical experience in:

* Understanding the OFDM transmission chain
* Implementing digital modulation and demodulation
* Understanding FFT and IFFT operations
* Implementing cyclic-prefix based OFDM
* Modeling AWGN channels
* Modeling multipath propagation
* Understanding channel frequency response
* Implementing frequency-domain equalization
* Evaluating BER versus SNR
* Comparing different digital modulation schemes
* Analyzing wireless communication system performance

---

# 🚀 Future Improvements

The system can be further extended with:

* MIMO-OFDM
* Rayleigh fading channel
* Rician fading channel
* Pilot-based channel estimation
* Adaptive modulation
* Forward Error Correction (FEC)
* Channel coding
* PAPR analysis and reduction
* 5G NR OFDM numerology
* Subcarrier allocation
* Real-time Software Defined Radio (SDR) implementation

---

# 👩‍💻 Author

## K. V. S. L. Aparajitha

**Electronics and Communication Engineering**
**B.Tech — 2027**

### Areas of Interest

* Wireless Communication
* RF Engineering
* Digital Communication
* Signal Processing
* Embedded Systems
* MATLAB

---

# 📌 Project Summary

This project presents a progressive MATLAB implementation of an **OFDM-based wireless communication system**.

Starting from **16-QAM modulation**, the system is progressively extended to **OFDM, AWGN, cyclic prefix, multipath propagation, channel equalization, BER analysis, and QPSK versus 16-QAM comparison**.

The eight stage-wise PDF documents provide the **MATLAB implementation, simulation outputs, plots, and screenshots** for the complete project.

---

⭐ **Explore the stage-wise PDFs above to see the complete development and simulation results.**
QAM project**. Keep it as a separate project; this OFDM project is the more advanced continuation of the communication-system work.
