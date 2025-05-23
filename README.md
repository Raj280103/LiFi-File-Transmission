# 🔦 LiFi File Transmission System using Arduino

This project demonstrates a **LiFi-based file transmission system** using visible light communication between two Arduino boards. The transmitter uses a **laser module** to encode and send file data, while the receiver employs an **LDR sensor** to decode the light signals back into data.

---

## 📌 Project Summary

This is a prototype implementation of data communication using **Light Fidelity (LiFi)**. Instead of radio waves, it uses a **laser beam** (or LED) for wireless transmission. This project focuses on **file transfer**—transmitting filename, size, and data bytes—between two Arduino Mega boards via light pulses.

---

## ⚙️ System Components

### Transmitter
- **Arduino Mega 2560**
- **Laser Module (3-pin)**
- **SD Card Module (SPI interface)**
- File stored on SD card (`.txt` or `.bin`)
- Custom bit encoding to pulse the laser for transmission

### Receiver
- **Arduino Mega 2560**
- **LDR Sensor** connected with a voltage divider
- Threshold calibration for laser ON/OFF detection
- Decoding light pulses into data

---

## 📂 Features

- 🔄 **Serial data transfer** over a laser beam
- 📁 **File name and size recognition**
- 📡 **Bit-wise data modulation using laser**
- 📥 **Reconstructed output stored/displayed at receiver**
- ⚙️ **Calibrated threshold for LDR detection**

---

## 🧠 Challenges Encountered

- SD card initialization issues on the transmitter
- Garbage values in file name or size due to timing mismatch
- Calibration of LDR threshold (e.g., threshold = 528 for ON/OFF)
- Synchronization errors between TX and RX Arduino boards
- Laser module remaining always ON due to code logic

---

## 🛠️ How It Works

### Transmission Logic
1. Read the file from SD card byte-by-byte.
2. Send filename and file size first.
3. For each byte, convert to 8 bits and pulse the laser accordingly.

### Reception Logic
1. Continuously monitor LDR analog input.
2. Detect HIGH/LOW based on threshold.
3. Decode bits into bytes → reconstruct filename and file content.

---

## 🔧 Hardware Setup

### 📤 Transmitter Side
- **Arduino Mega 2560** – main controller
- **Laser Module (3-pin)** – acts as the optical transmitter
- **SD Card Module** – connected via SPI to read file data
  - **CS pin**: 53  
  - **MOSI/MISO/SCK**: standard SPI pins
- **File** stored on SD card (e.g., `.txt`)
- **Pin 8** – controls the laser ON/OFF based on bit encoding

### 📥 Receiver Side
- **Arduino Mega 2560** – main controller
- **LDR Sensor** – detects laser light intensity
- **Voltage Divider Circuit** – with a fixed resistor (e.g., 10kΩ)
- **Analog Pin A0** – reads LDR voltage
- **Threshold** – calibrated value (e.g., `528`) to differentiate light ON vs OFF

### 📡 Physical Alignment
- The **laser** must be precisely aligned to directly hit the **LDR sensor**
- Ideal in a **dark or controlled light environment** to reduce noise
- Distance between laser and LDR: typically a few centimeters to meters (based on beam strength and LDR sensitivity)


