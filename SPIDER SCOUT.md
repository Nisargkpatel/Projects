## 🕷️ Spider Scout - A Six-Legged Surveillance Hexapod Robot

**Spider Scout** is a six-legged robotic system designed to mimic insect locomotion for enhanced mobility, adaptability, and surveillance in rugged environments. The robot integrates 3D-printed mechanics, an ESP32-CAM with pan-tilt, and precise gait control via an Arduino Mega. It is capable of operating on various terrains with multiple walking gaits and can be remotely controlled using a Bluetooth interface.

---

## 📚 Abstract
This project showcases a functional biomimetic hexapod robot with onboard vision capabilities and multiple locomotion modes. The design was iteratively refined, starting with Arduino Nano and eventually implementing an Arduino Mega for controlling 18 high-torque MG996R servos. It also integrates an ESP32-CAM module for live video feed and remote pan-tilt control.

### Key features:
- Remote wireless control via HC-05 Bluetooth module
- ESP32-CAM-based vision with pan-tilt mount
- Custom battery management system (BMS)
- Multiple gaits: Tripod, Ripple, Wave, Tetrapod, and Obstacle Gait

---

## 💡 Motivation
- ✈️ **Terrain Adaptability**: Overcome terrain limitations faced by wheeled robots
- 🦕 **Biomimicry**: Emulate insect locomotion for stability and adaptability
- 🚩 **Surveillance**: Integrate vision for monitoring inaccessible areas
- 🎓 **Learning Platform**: Build skills in embedded systems, power electronics, CAD, and control systems

---

## 📈 Design Architecture

### 🛠️ Mechanical
- **Material**: PLA via 3D printing
- **Leg Configuration**: 3 DOF per leg using MG996R servos (Coxa, Femur, Tibia)
- **Hexagonal Body**: Optimal for symmetrical load distribution

### 💻 Electronics
- **Controller**: Arduino Mega
- **Camera**: ESP32-CAM with 2 DOF pan-tilt using SG90 servos
- **Bluetooth**: HC-05 module for remote control
- **Servos**: 18x MG996R (up to 2.5A each under load)
- **BMS**: Custom 3S Li-ion pack with over-voltage, under-voltage, and short-circuit protection
- **Voltage Regulation**: 3 Buck Converters for:
  - Servos @ 6V
  - Arduino @ 5V
  - ESP32-CAM @ 5V

---

## 🎓 Software Design

### Gait Control
Implemented gaits using inverse kinematics and smooth stride control:
- **Tripod Gait**: Fast, 3 legs lifted per cycle
- **Ripple Gait**: One leg lifted per sub-cycle for smooth motion
- **Wave Gait**: Highest stability, slowest
- **Tetrapod Gait**: Balanced between speed and stability
- **Obstacle Gait**: High-lift gait for stepping over objects

### Command Processing
- Supports commands like F (forward), B (back), L (left), R (right), S (stop), numbers (0-9) to select gait

### Camera Interface
- Live streaming via ESP32-CAM
- Web server hosted on the ESP32
- HTML+JavaScript UI for pan/tilt camera

---

## 🔧 Power System

### Battery
- Custom 3S Li-ion: 3 sets of 4 cells in parallel
- ~45 minutes of continuous operation

### Current Management
- Peak current: ~8A
- Idle draw: ~0.8A
- Startup surge: >20A (handled via BMS)

---

## 📊 Performance & Testing

### Locomotion
- Speed: ~0.15 m/s (Tripod)
- Incline: ~20° on Wave gait
- Turn rate: 30°/sec

### Camera
- Range: 15m (LoS)
- Frame Rate: 15-20 fps @ 640x480
- Pan: 180° | Tilt: 90°

### System Stability
- Maintains ±2mm foot accuracy
- Servo PWM frequency: 50Hz stable
- Latency: ~120ms (Bluetooth)

---

## 🔮 Troubleshooting Highlights
- Arduino Nano and Teensy 4.1 lacked stable servo support
- Voltage drops caused erratic movement
- Final fix: Arduino Mega with isolated servo power and proper grounding
- Used thicker wires and a power distribution board

---

## 🎯 Results
- Modular gait switching and smooth walking
- Remote visual feed + directional control
- Robust design with ~1.2 kg payload

---

## 📊 Future Scope
- ✨ Add sensors (ultrasonic/IR) for obstacle avoidance
- 📱 Integrate Android App or WebApp control
- ⚙️ Autonomous navigation using SLAM
- 🧠 ML-based adaptive gait

---

## 📊 Major Components

| Component          | Specs / Notes                                  |
|-------------------|-----------------------------------------------|
| MG996R Servo      | 2.5A max, 11kg-cm torque, 180° rotation         |
| Arduino Mega      | 54 I/O pins, 16 analog inputs                  |
| ESP32-CAM         | OV2640 sensor, 640x480 streaming               |
| SG90 Servos       | Used for pan/tilt (2 servos)                   |
| Buck Converters   | 3x; adjustable 1.25-30V, 5A output             |
| Custom BMS        | 3S config, 20A peak, 4.25V/cell over-voltage   |

---

