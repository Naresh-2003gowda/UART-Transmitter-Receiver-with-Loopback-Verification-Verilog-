# UART Transmitter & Receiver with Loopback Verification (Verilog)

## 📖 Project Overview
This project implements a full-duplex UART (Universal Asynchronous Receiver Transmitter) using Verilog HDL. The design includes FSM-based transmitter and receiver modules with configurable baud rate and mid-bit sampling for reliable data reception.

The design was simulated and verified using Icarus Verilog and EPWave on EDA Playground.

## 🚀 Features

- Configurable baud rate using `CLKS_PER_BIT`
- FSM-based UART Transmitter (IDLE → START → DATA → STOP)
- FSM-based UART Receiver with mid-bit sampling
- LSB-first serial transmission
- Self-checking testbench
- Waveform verification using VCD dump
- Loopback connection (TX → RX)

## 🏗️ Design Architecture

### 1️⃣ UART Transmitter (uart_tx)
- Generates start bit (0)
- Transmits 8-bit data (LSB first)
- Generates stop bit (1)
- Uses clock counter for baud timing

### 2️⃣ UART Receiver (uart_rx)
- Detects start bit
- Performs mid-bit sampling
- Reconstructs 8-bit parallel data
- Asserts `rx_done` after successful reception

### 3️⃣ Top Module (uart_top)
- Connects TX serial output to RX serial input (loopback)
- Used for internal verification

## 🧪 Verification Strategy

- Generated 50 MHz clock
- Applied reset
- Sent test byte `8'hA5`
- Waited for `rx_done`
- Compared received data with transmitted data
- Displayed PASS/FAIL message

## 📊 Waveform Verification

Verified the following in EPWave:

- Start bit generation
- Correct bit timing using `clk_count`
- LSB-first data transmission
- Stop bit generation
- Receiver mid-bit sampling
- Proper assertion of `rx_done`

## 🛠 Tools Used
- Verilog HDL
- Icarus Verilog
- EDA Playground
- EPWave Viewer
  
## 🎯 Learning Outcomes

- FSM-based serial protocol implementation
- Baud rate timing design
- Mid-bit sampling technique
- Self-checking verification methodology
- Waveform-level debugging

## 🔮 Future Improvements

- Add synchronous FIFO buffer
- Add parity bit support
- Add configurable data length
- Add error detection (framing/parity errors)
- Implement hardware-ready baud generator module

## 👨‍💻 Author
Naresh N 
Electronics & Communication Engineer  
Focused on RTL Design and Digital Systems
