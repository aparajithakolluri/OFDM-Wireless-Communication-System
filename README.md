# OFDM-Based Wireless Communication System

A MATLAB-based simulation of an **Orthogonal Frequency Division Multiplexing (OFDM) wireless communication system** incorporating 16-QAM, QPSK, AWGN noise, multipath fading, cyclic prefix, channel equalization, and BER performance analysis.

---

## 📌 Project Overview

This project demonstrates the step-by-step development of an OFDM-based wireless communication system.

The system starts with random binary data and progressively introduces realistic wireless-channel effects such as:

- Digital modulation
- OFDM subcarriers
- AWGN noise
- Cyclic prefix
- Multipath propagation
- Channel equalization
- BER performance analysis
- Modulation comparison

The project was implemented and simulated using **MATLAB**.

---

## 🛰️ System Architecture

```text
                 TRANSMITTER

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
────────────────────────────────
       WIRELESS CHANNEL
────────────────────────────────
        │
        ├── AWGN Noise
        │
        └── Multipath Fading
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
