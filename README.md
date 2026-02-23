# Automated-Dual-Leaf-Swing-Gate-Controll-System
IronDome is a dual-ESP32 based intelligent automated gate control system designed for precise, safe, and reliable operation of a two-leaf swing gate. The system integrates real-time position tracking, obstacle detection, wireless control, and fail-safe logic to ensure industrial-grade performance.

This prototype is implemented using a wired perfboard-based hardware architecture before transitioning to a custom PCB design.
## 📷 Prototype Hardware

<p align="center">
  <img src="images/AUTOMATED_GATE_SYSTEM.jpeg" width="600"/>
</p>

# System Architecture
The system consists of:

2 × ESP32 Controllers

CCW Controller (Left Leaf)

CW Controller (Right Leaf)

Encoder-based position feedback

IR-based obstacle detection module

Relay-based motor driving stage

12V 40A SMPS power system

RF remote interface

Blynk IoT cloud integration

ESP-NOW inter-controller communication

Each leaf operates independently while synchronizing via ESP-NOW for coordinated movement.

## 2️⃣ Encoder-Based Position Memory

- Uses incremental rotary encoder for real-time position tracking  
- Stores **Fully Closed** and **Fully Open** positions in non-volatile memory  
- Prevents over-travel and mechanical damage  
- On power restoration:
  - Verifies encoder state consistency  
  - Triggers buzzer alert on mismatch  
  - Locks motor operation until reinitialization  

---

## 3️⃣ Intelligent Obstacle Detection

- IR beam interruption detection via relay output  
- Firmware-level debounce filtering  
- Immediate motor stop on obstacle detection  
- Prevents collision with vehicles or objects  

---

## 4️⃣ Blynk IoT Integration

### Virtual Pin Mapping

| Virtual Pin | Function |
|------------|----------|
| V1 | Open CCW Leaf |
| V2 | Close CCW Leaf |
| V4 | Open CW Leaf |
| V5 | Close CW Leaf |

### Features

- Remote control via smartphone  
- Real-time gate status monitoring  
- Cloud-based connectivity  

---

## 5️⃣ ESP-NOW Master–Slave Communication

- Low-latency peer-to-peer communication  
- Eliminates dependency on multiple cloud devices  
- Ensures synchronized dual-leaf operation  

---

## 6️⃣ Fail-Safe Buzzer Logic

- GPIO-controlled transistor-driven buzzer (Active LOW)  
- Active during:
  - Power ON  
  - Initialization phase  
  - Encoder inconsistency detection  
- Automatically disabled after safe calibration  

---

## 7️⃣ External RF Trigger Support

- Remote key-based triggering  
- Parallel hardware-level command injection  
- Fully functional without internet connectivity  

---

## 🔋 Power System

- 12V 40A SMPS power supply  
- Separate regulation for:
  - Motor drive section  
  - Logic circuits  
  - ESP32 controllers  
- Ground isolation strategy for noise immunity  

---

## 🛠 Hardware Implementation

- Perfboard-based modular prototype  
- Screw terminals for field wiring  
- Relay modules for motor polarity control  
- Dedicated obstacle input (GPIO 14)  
- Buzzer control (GPIO 12 – Active LOW logic)  
- Designed for functional validation before custom PCB migration  

---

## 🧠 Firmware Design Highlights

- State-machine based movement logic  
- Command validation before execution  
- Motor direction interlock protection  
- Encoder discrepancy detection after power restore  
- Debounced obstacle interrupt handling  
- Optimized memory usage on ESP32  

---

## 🔒 Safety Mechanisms

- Immediate stop on IR interruption  
- Motion restricted within stored position limits  
- Motor disabled on encoder mismatch  
- Hardware-level relay isolation  
- No uncontrolled startup movement  

---

## 🚀 Future Improvements

- Custom PCB with EMI shielding  
- Soft-start motor control  
- Improved enclosure thermal management  
- Enhanced mobile app UI  
- Battery backup integration  
