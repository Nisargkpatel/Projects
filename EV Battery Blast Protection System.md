# 🔥 EV Battery Blast Protection System

A real-time thermal safety system for electric vehicles that monitors battery temperature and cuts off power to the BLDC motor when thermal runaway is detected — protecting the battery from catastrophic failure.

---

## 📘 Abstract

Electric vehicle (EV) batteries are prone to thermal runaway — a chain reaction triggered by overheating due to overcurrent, overcharging, or external temperature. This project presents a **cost-effective, real-time blast protection system** that monitors battery temperature and uses a **relay mechanism controlled by an ESP32 microcontroller** to immediately disconnect power if unsafe temperature levels are reached.

The solution addresses core challenges in EV battery safety using simple electronics and embedded logic to provide a robust and scalable system.

---

## 🚩 Problem Statement

With increasing EV adoption, battery safety is a critical concern. Several EV fires and explosions have been attributed to poor thermal management, especially during aggressive charging/discharging. 

This system provides:
- **Instant thermal cutoff**
- **Current isolation**
- **Preventive circuit disengagement**

---

## 🧪 Working Principle

### ⚙️ System Workflow:

1. **Continuous Temperature Monitoring**  
   The ESP32 continuously polls temperature sensor data connected to the battery casing.

2. **Threshold Comparison**  
   If the temperature exceeds a predefined limit (e.g., 60°C), a digital HIGH signal is sent from a GPIO pin.

3. **Relay Activation via Transistor**  
   Since the ESP32 GPIO cannot directly drive a mechanical relay, a **BC547 transistor** is used to amplify the signal.

4. **Motor Cutoff**  
   The relay deactivates the power path to the **BLDC motor**, preventing further thermal escalation.

---

## 🧰 Hardware Components

| Component              | Description / Use                                               |
|------------------------|-----------------------------------------------------------------|
| **ESP32**              | Wi-Fi-enabled microcontroller for logic control                 |
| **DSB1820 RTD** | For temperature sensing (user configurable)              |
| **BC547 Transistor**   | Drives the relay from ESP32 GPIO                                |
| **5V Relay Module**    | Isolates and cuts off high-current motor circuit                |
| **BLDC Motor (Simulated)** | Represents EV load                                         |
| **Power Supply Unit**  | Provides regulated 5V to relay and logic circuits               |
| **Resistors**          | Pull-down and base limiting resistors                           |
| **PCB / Breadboard**   | For circuit assembly                                            |

Youtube video Link:
(https://youtu.be/kiBSixkugpc?feature=shared)
