# 🤖 Mikrokontroler & TinyML Projects

![ESP32](https://img.shields.io/badge/Hardware-ESP32-red?style=for-the-badge&logo=espressif)
![Arduino](https://img.shields.io/badge/Firmware-Arduino-teal?style=for-the-badge&logo=arduino)
![TensorFlow](https://img.shields.io/badge/AI-TensorFlow%20Lite-orange?style=for-the-badge&logo=tensorflow)
![Python](https://img.shields.io/badge/Tools-Python-blue?style=for-the-badge&logo=python)

> **Repositori Tugas & Proyek Akhir Mata Kuliah Mikrokontroler**
> Berisi koleksi implementasi sistem *embedded* mulai dari komunikasi IoT dasar (MQTT), sistem kontrol motor (PWM/RPM), hingga penerapan kecerdasan buatan pada perangkat keras (*Edge AI/TinyML*) menggunakan ESP32.

---

## 🌟 Fitur & Modul Utama

Repositori ini terbagi menjadi dua bagian utama (ETS dan EAS) dengan fitur-fitur berikut:

### 🚀 EAS (Evaluasi Akhir Semester) - Fokus Utama
1.  **TinyML / AI on Edge (`Mikrokontroler with Ai`)**
    * Implementasi jaringan syaraf tiruan **LSTM (Long Short-Term Memory)** langsung pada ESP32.
    * Penggunaan **TensorFlow Lite for Microcontrollers**.
    * Skrip pelatihan model (`train_lstm_pwm_ff.py`) dan konversi model ke C header (`tflite_to_header.py`).
2.  **Motor Control System (`PWM - RPM`)**
    * Pengaturan kecepatan motor DC menggunakan sinyal PWM.
    * Monitoring RPM motor secara *real-time*.
    * **Dashboard Monitoring** berbasis Python (`motor_dashboard.py`) untuk visualisasi data.
3.  **IoT Application (`MQTT`)**
    * Komunikasi data nirkabel menggunakan protokol MQTT (`iot_apps.ino`).

### 📚 ETS (Evaluasi Tengah Semester)
* Dasar-dasar pemrograman mikrokontroler.
* Integrasi awal dengan Jupyter Notebook.
* Aplikasi MQTT sederhana (`modul2-Apk_MQTT.ino`).

---

## 🛠️ Teknologi yang Digunakan

* **Hardware:** ESP32 Development Board, DC Motor, Sensor Kecepatan (Encoder/Optocoupler).
* **Firmware:** C++ (Arduino Framework).
* **Software & AI:**
    * Python 3.x
    * TensorFlow & Keras (Training Model)
    * Paho MQTT (Komunikasi Python)
    * Matplotlib/Tkinter (Dashboard)

---

## 📂 Susunan Proyek

```bash
mikrokontroler/
├── EAS-Mikrokontroler/             # 🎓 Proyek Akhir
│   ├── 1. MQTT/
│   │   └── iot_apps.ino            # Firmware aplikasi IoT
│   ├── 2. PWM - RPM/
│   │   ├── monnitol.ino            # Firmware kontrol motor & baca sensor
│   │   └── motor_dashboard.py      # Script Python untuk dashboard PC
│   └── 3. Mikrokontroler with Ai/
│       ├── esp32_lstm_ff_pid.ino   # Firmware utama AI di ESP32
│       ├── train_lstm_pwm_ff.py    # Training model AI (di PC)
│       ├── tflite_to_header.py     # Konverter model (.tflite ke .h)
│       └── telemetry.csv           # Dataset untuk training
├── ETS-Mikrokontroler/             # 📝 Tugas Tengah Semester
│   ├── modul1-JupyterNotebook.ino
│   ├── modul1-Notebook.ipynb
│   └── modul2-Apk_MQTT.ino
├── LAPORAN EAS-Mikro.pdf           # 📄 Dokumentasi lengkap proyek EAS
└── README.md
```
## ⚙️ Prasyarat & Instalasi

1. Hardware Setup
Siapkan board ESP32.
Rangkai motor DC dan sensor sesuai skema (lihat folder masing-masing modul).
2. Software Setup (PC)
Pastikan Python terinstal untuk menjalankan skrip training dan dashboard.
```bash
pip install tensorflow numpy pandas paho-mqtt matplotlib
```
3. Arduino IDE Setup
Install Arduino IDE.
Tambahkan Board Manager untuk ESP32.
Install library yang dibutuhkan melalui Library Manager:
PubSubClient (untuk MQTT)
TensorFlowLite_ESP32 (untuk modul AI)

## 🚀 Contoh Penggunaan (Modul AI)
Untuk menjalankan proyek Mikrokontroler with AI:
1. Training Model: Jalankan script Python untuk melatih model berdasarkan data telemetry.csv.
```bash
cd "EAS-Mikrokontroler/3. Mikrokontroler with Ai"
python train_lstm_pwm_ff.py
```
Output: File model .tflite.

2. Konversi Model: Ubah model menjadi file header C agar bisa dibaca ESP32.
```bash
python tflite_to_header.py
```
Output: File .h berisi array hex model.

3. Flash ke ESP32:
Buka esp32_lstm_ff_pid.ino di Arduino IDE.
Pastikan file .h hasil konversi berada satu folder dengan file .ino.
Upload ke board ESP32.

Monitoring: Buka Serial Monitor (Baudrate 115200) untuk melihat hasil prediksi inferensi AI secara real-time.
