# Chemical Reactor Simulator: Level Control Loop and Safety Instrumented System (SIS)

An Arduino-based functional prototype designed to simulate a **closed-loop proportional level control system** and an independent protection layer, commonly known in the chemical industry as a **Safety Instrumented System (SIS)** or **Emergency Shutdown System (ESD)**.

The main objective is to demonstrate the coexistence of continuous process control and discrete, immediate safety actions for industrial risk mitigation.

---

## 🚀 System Architecture

The project is structured into two distinct automation layers:

### 1. Operational Control Layer (Proportional Closed-Loop Control)

- **Sensor (LT-01):** An ultrasonic sensor acts as a Level Transmitter, measuring the liquid level inside the reactor.
- **Actuator (LCV-01):** A servo motor simulates a discharge Flow Control Valve.
- **Control Logic:** Using a linear mapping function (`map`), the system calculates the appropriate valve opening angle. As the reactor level rises (sensor distance decreases), the valve opens proportionally to drain the fluid. As the level decreases, the valve closes to retain the liquid inventory.

### 2. Protection and Interlock Layer (SIS / ESD)

- **Critical Condition:** High-level alarm threshold set at **8 cm** from the ultrasonic sensor.
- **Emergency Action (Interlock):** If the operational control loop fails or a severe process disturbance occurs, the protection logic takes priority and forces the discharge valve (LCV-01) to open completely (**100% / 180°**).
- **Alarms (LAH – High-Level Alarm):** Synchronized intermittent activation of a visual alarm (LED) and an audible alarm (passive buzzer using software-based frequency modulation).

---

## 🛠️ Hardware Components (Bill of Materials)

| Component | Specification | Quantity |
|---|---|---:|
| Arduino Board | Uno / Mega / Nano | 1 |
| Ultrasonic Sensor | HC-SR04 (Level Transmitter) | 1 |
| Micro Servo Motor | SG90 (Control Valve) | 1 |
| LED | Diffused LED (Visual Alarm) | 1 |
| Resistor | 220 Ω | 1 |
| Passive Buzzer | Audible Alarm | 1 |
| Breadboard and Jumper Wires | Prototyping Components | 1 set |

---

## 📌 Pin Mapping and Connections

| Component | Component Pin | Arduino Pin | Industrial Function |
|---|---|---|---|
| Ultrasonic Sensor | VCC | 5V | Power Supply (+5V) |
| Ultrasonic Sensor | Trig | Pin 12 | Trigger Signal (Output) |
| Ultrasonic Sensor | Echo | Pin 11 | Echo Signal (Input) |
| Ultrasonic Sensor | GND | GND | Ground Reference (0V) |
| Servo Motor | Yellow (Signal) | Pin 3 | Valve Position Control |
| Servo Motor | Red (VCC) | 5V | Power Supply (+5V) |
| Servo Motor | Black (GND) | GND | Ground Reference (0V) |
| LED | Long Leg (+) | Pin 9 | Visual Alarm Activation |
| LED / Resistor | Short Leg (-) | GND | Circuit Return |
| Passive Buzzer | Positive (+) | Pin 10 | Audible Alarm Frequency Modulation |
| Passive Buzzer | Negative (-) | GND | Circuit Return |

---

## 📈 Dynamic Behavior Demonstration

Process variables were monitored in real time using the **Arduino Serial Plotter**, simulating the visualization interface of a traditional industrial **SCADA (Supervisory Control and Data Acquisition)** system.

The monitoring interface allows observation of process behavior, including level variations and the corresponding control actions during normal and critical operating conditions.

---

## 💻 How to Run This Project

1. Clone this repository or download the source code from the `/src` directory.
2. Open the project in the **Arduino IDE**.
3. Ensure that the standard `Servo.h` library is available in your development environment.
4. Connect the hardware components according to the pin mapping table.
5. Upload the code to your Arduino board.
6. Open the **Serial Plotter** and configure it to `9600 baud` to visualize the simulated chemical process variables.

---

## 🧠 Engineering Concepts

- **Process Control:** Closed-loop proportional control.
- **Instrumentation:** Level measurement and valve actuation.
- **Industrial Automation:** Control hierarchy and actuator positioning.
- **Functional Safety:** Safety interlocks and emergency actions.
- **SIS / ESD:** Independent protection layer concepts.
- **SCADA:** Real-time process monitoring and visualization.

---

## 🙋‍♂️ Author

Developed by **Lucas Santos Nogueira**

- 💼 **LinkedIn:** [Visit my professional profile](https://www.linkedin.com/in/lucas-santos-nogueira-8404a0379/)
- ✉️ **Email:** [Get in touch](mailto:lucassantosnogueira8@gmail.com)
