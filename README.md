# acoustic-anomaly-detection-edge

# 🔊 Acoustic Anomaly Detection for Home Security  
### Powered by Edge Impulse & Deep Learning

This project implements an efficient acoustic anomaly detection (AAD) system designed for smart home security. It leverages **Edge Impulse**, **DSP feature extraction**, and a quantized **CNN model**, enabling **real-time inference on low-power embedded devices** like Raspberry Pi or Cortex-M MCUs.

---

## 📂 Repo Contents

| File | Description |
|------|-------------|
| `trained.tflite` | Quantized model for embedded inference (TensorFlow Lite) |
| `model.h5` | Original Keras model (for retraining or testing) |
| `deployment-metadata.json` | Contains model structure, DSP block config, and feature extraction info |
| `model_metadata.h` | C header file for C++ SDK deployments |
| `model_variables.h` | Quantized model weights for embedded systems |
| `README.md` | You're reading it! Project overview and deployment guide |

---

## 🧠 Project Overview

This system detects **abnormal acoustic events** like:
- 🚨 Alarms
- 🧍 Screams
- 💥 Glass breaking

By classifying them against **normal household sounds** using audio features extracted with **MFCC**, **MFE**, and **Spectrogram** pipelines.

---

## ⚙️ Technical Summary

- **Model**: 1D CNN
- **Input**: Fused MFCC + MFE + Spectrogram (10,914 features)
- **Output**: Binary classification (normal vs abnormal)
- **Accuracy**: 91.9%
- **Latency**: ~1 ms (on embedded target)
- **Model Size**: ~965 KB
- **RAM Usage**: ~74 KB

---

## 🧪 Deployment Options

### 🔹 Embedded (C++)
Use the C header files (`model_metadata.h`, `model_variables.h`) with the Edge Impulse C++ SDK to deploy on:
- STM32 / nRF MCUs
- Arduino Portenta
- Raspberry Pi Pico (with C SDK)

### 🔹 TensorFlow Lite
Use `trained.tflite` with Python or mobile inference libraries:

```bash
pip install tflite-runtime numpy soundfile
python run_inference.py --model trained.tflite --audio sample.wav
