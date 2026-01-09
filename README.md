# IoT Smart Payment & Fee Management System 💳🎓

A comprehensive cashless campus solution integrating an **ESP32-based Payment Terminal** with a **Web-based Fee Management Portal**. This system allows students to pay fees, recharge their accounts, and transfer funds using NFC cards, with real-time syncing via GPRS.

## 🌟 Features

### 🖥️ Web Portal (Student Dashboard)
* **Secure Login:** Student authentication system.
* **Fee Management:** View total fees, paid amount, and due balance.
* **NFC Card Management:** View card balance and transaction history.
* **Online Recharge:** Simulate adding funds to the NFC card via UPI.
* **Fund Transfer:** Transfer NFC wallet balance directly to college fees.
* **Auto-Recharge:** Automatically top-up the card when the balance is low.

### 📟 Hardware Terminal (ESP32)
* **Tap-to-Pay:** RFID/NFC authentication for transactions.
* **GPRS Connectivity:** Real-time server communication using SIM800L.
* **Offline/Online Logic:** Robust handling of network connection states.
* **User Feedback:** 20x4 LCD display and Keypad input for PIN/Amount.

---

## 🛠️ Hardware Requirements 
* **Microcontroller:** ESP32 Dev Module
* **RFID Reader:** MFRC522 * **GSM Module:** SIM800L (GPRS) * **Display:** 20x4 LCD with I2C Backpack
* **Input:** 4x4 Matrix Keypad
* **Power Supply:** 5V (Ensure sufficient amps for SIM800L)

### 🔌 Pin Arrangement

| Component | Pin Label | ESP32 GPIO |
| :--- | :--- | :--- |
| **RFID (RC522)** | SDA (SS) | 4 |
| | RST | 33 |
| | MOSI | 23 |
| | MISO | 19 |
| | SCK | 18 |
| **GSM (SIM800L)** | TX | 16 (RX2) |
| | RX | 17 (TX2) |
| **LCD (I2C)** | SDA | 21 |
| | SCL | 22 |
| **Keypad** | Rows 1-4 | 12, 14, 27, 26 |
| | Cols 1-4 | 25, 15, 32, 13 |

#### **RFID Reader (RC522)**
| RC522 Pin | ESP8266 Pin | Description |
| :--- | :--- | :--- |
| **SDA (SS)** | **D1** | Chip Select |
| **SCK** | **D5** | SPI Clock |
| **MOSI** | **D7** | SPI MOSI |
| **MISO** | **D6** | SPI MISO |
| **RST** | **D2** | Reset |
| **GND** | GND | Ground |
| **VCC** | 3.3V | Power |

---

## 💻 Software Setup

### 1. Database Configuration
Import the following schema structure into your MySQL database:
* `Users`: Authentication details (`username`, `password`, `enrollment_no`).
* `nfc`: Card details (`uid`, `amount`, `secret_code`, `auto_recharge_*`).
* `Student`: Academic details (`name`, `course`, `semester`, etc.).
* `Fees`: Fee tracking (`total_fee`, `fee_paid`, `amount_transferred`).
* `Transactions`: Log of all recharges and deductions.

### 2. Web Portal
1.  Upload the `php` folder contents to your hosting server (e.g., Hostinger, cPanel).
2.  Edit `config.php` with your database credentials.

### 3. ESP32 Firmware
1.  Install the required libraries in Arduino IDE: `MFRC522`, `LiquidCrystal_PCF8574`, `Keypad`, `ArduinoJson`.
2.  Update `apn` and `serverAddress` in the `.ino` file.
3.  Flash the code to your ESP32.

---

## 📸 Screenshots
<img width="2560" height="1371" alt="Screenshot (178)" src="https://github.com/user-attachments/assets/80de302d-b97c-4af5-9b0a-68b8a034cb70" />
<img width="359" height="300" alt="Screenshot 2026-01-09 110708" src="https://github.com/user-attachments/assets/9b7e3644-510f-42ee-b95a-1ecb3171fa6d" />


## 📄 License
This project is open-source and available under the [MIT License](LICENSE).
