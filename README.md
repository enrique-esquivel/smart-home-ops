# Smart Home Ops - Jetson Nano NVR & Home Automation

Infrastructure as Code (IaC) for a home automation and AI-powered video surveillance system, running locally on an **NVIDIA Jetson Nano**. 

This project orchestrates Home Assistant, an MQTT broker (Mosquitto), and Frigate NVR, optimized to leverage the CUDA cores (TensorRT) of the Jetson Nano for real-time object detection using Dahua IP cameras.

## 🏗 Architecture & Hardware

* **Main Hardware:** NVIDIA Jetson Nano (4GB)
* **Storage:** External SSD via USB 3.0 (Native SSD Boot).
* **Cameras:** Dahua IP Cameras (Dual-stream configuration: Substream for AI detection, Main stream for high-res recording).
* **Orchestrator:** Docker Compose.
* **Components:**
  * [Home Assistant](https://www.home-assistant.io/) (Host Mode)
  * [Frigate NVR](https://frigate.video/) (TensorRT hardware acceleration)
  * [Eclipse Mosquitto](https://mosquitto.org/) (MQTT Broker)

## ⚡ Notes on Native SSD Boot

This environment assumes the Jetson Nano boots directly from an external SSD connected via USB 3.0, without using a microSD card. To achieve USB bus stability and avoid write errors in the Ramdisk (`RAMDISK: incomplete write`), the following is recommended:
1. Flash the JetPack image directly to the SSD.
2. Avoid SATA/NVMe enclosures with chips that conflict with the UAS protocol.
3. Ensure a barrel jack power supply (5V 4A) is used with the J48 jumper enabled.

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone git@github.com:enrique-esquivel/smart-home-ops.git
cd smart-home-ops
