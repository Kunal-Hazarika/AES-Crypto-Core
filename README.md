# AES Encryption & Decryption Modules with Data Splitter

## Overview
This project implements a **64-bit AES encryption and decryption core** in Verilog, along with a **Data Splitter** and **Unslicer** to handle 128-bit data.  
The design supports **multiple keys**, enabling independent encryption of two 64-bit halves, and includes a **testbench with scoreboard mechanism** to verify correctness.

## Features
- **AES Core Modules**
  - SubBytes
  - ShiftRows
  - MixColumns / InvMixColumns
  - AddRoundKey
- **Data Splitter**: Splits 128-bit input into two 64-bit blocks for parallel encryption.
- **Unslicer**: Combines two 64-bit decrypted blocks into 128-bit original data.
- **Multiple Key Support**: Different keys for each 64-bit block.
- **Scoreboard Verification**: Automated checking of encryption–decryption consistency.

## How It Works
1. **Encryption**
   - Input: 128-bit plaintext
   - Data Splitter divides it into two 64-bit halves.
   - Each half passes through the AES encryption core.
   - Encrypted halves are combined into a 128-bit ciphertext.

2. **Decryption**
   - Input: 128-bit ciphertext
   - Unslicer splits into two encrypted halves.
   - Each half passes through AES decryption core.
   - Decrypted halves are combined to recover the original plaintext.

3. **Scoreboard**
   - Automatically compares decrypted output with original input.
   - Displays pass/fail results in simulation.
