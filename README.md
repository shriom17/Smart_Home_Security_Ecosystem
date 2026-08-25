# 🏠 Smart Home Security Ecosystem using IoT & VLAN Segmentation

![Packet Tracer](https://img.shields.io/badge/Cisco%20Packet%20Tracer-v8.2+-00569B?style=for-the-badge&logo=cisco&logoColor=white)
![Network Architecture](https://img.shields.io/badge/Architecture-Router--on--a--Stick-orange?style=for-the-badge)
![VLAN](https://img.shields.io/badge/VLAN%20Segmentation-Enabled-brightgreen?style=for-the-badge)
![Status](https://img.shields.io/badge/Project%20Status-Completed-success?style=for-the-badge)

An intelligent, enterprise-grade **Smart Home Security System** designed and simulated using **Cisco Packet Tracer**. The project demonstrates the seamless integration of IoT network automation, real-time threat detection, conditional logic execution, and strict network isolation using **VLAN Segmentation** and **Inter-VLAN Routing (Router-on-a-Stick)**.

---

## 📌 Table of Contents
- [Architecture Overview](#-architecture-overview)
- [Key Features](#-key-features)
- [Network Segmentation & Topology](#-network-segmentation--topology)
- [System Operational Flow](#-system-operational-flow)
- [Configuration & Execution](#-configuration--execution)
- [Testing & Verification](#-testing--verification)
- [Author](#-author)

---

## 🏛️ Architecture Overview

Modern smart homes face significant cybersecurity risks if IoT devices share the same network space with critical end-user devices. This project solves that problem by implementing **Network Segmentation**:
1. **IoT Security Zone (VLAN 25):** Houses automated sensors, actuators, smart peripherals, and the Home Gateway.
2. **Network Access Zone (VLAN 20):** Dedicated to user end-devices (PCs, Laptops, Smartphones, Tablets) and centralized application servers.

Inter-VLAN communication is bridged securely using a **Router-on-a-Stick** configuration with `802.1Q` encapsulation, enabling remote management without compromising broadcast isolation.

---

## ✨ Key Features

* 🔐 **Network Isolation via VLANs:** Segregates IoT devices from standard network endpoints to mitigate broadcast storms and enhance network security.
* ⚡ **Autonomous Intrusion Response:** Real-time threat detection using Motion Sensors to instantly trigger physical deterrence mechanisms (Siren, Smart Lighting, Automated Door Locking, and Webcam Recording).
* 📧 **Automated SMTP Email Alerts:** Sends instantaneous email notifications to end-user devices upon intrusion detection via a central mail server.
* 🌐 **Cross-VLAN IoT Monitoring:** Enables secure user access to the Home Gateway web interface (`http://192.168.25.1`) from wireless devices on VLAN 20.
* 🔄 **Self-Healing / Auto Reset:** Automatically resets sensor states, unlocks doors, and standby peripherals when no threat/motion is detected.

---

## 🌐 Network Segmentation & Topology

| Network Zone | VLAN ID | IP Subnet / Scope | Components Connected |
| :--- | :---: | :--- | :--- |
| **IoT Security Zone** | `VLAN 25` | `192.168.25.0/24` | Home Gateway, Motion Detector, Smart Light, Siren, Automated Door, Webcam |
| **Network Access Zone** | `VLAN 20` | `192.168.20.0/24` | Main Server, Router, Switch, Wireless Access Point, Laptop, PC, Smartphone, Tablet |

---

## 🔄 System Operational Flow

```mermaid
flowchart TD
    A[Start / Idle Monitoring] --> B{Motion Detected?}
    B -- No --> A
    B -- Yes --> C[Activate Local Defense]
    C --> D[Pulsing Siren & Smart Light ON]
    C --> E[Lock Automated Door]
    C --> F[Activate Webcam Video Stream]
    C --> G[Trigger SMTP Alert Payload]
    G --> H[User Receives Email Alert on Smartphone/Tablet]
    H --> I[End / Event Handled]
