🚑 Smart Fall Detection System (IoT)

A wearable biomedical device firmware that detects falls using a 3-axis accelerometer (MPU6050) and an ESP32 microcontroller. The system uses a vector-magnitude algorithm to distinguish between daily activities (walking, sitting) and sudden fall events.

🌟 Features

Real-time kinematics monitoring: Continually reads X, Y, Z acceleration forces.

False-Positive Rejection: Uses a two-stage threshold (Impact + Orientation Change) to prevent false alarms from jumping or clapping.

Edge Computing: All processing happens on the device (no cloud latency).

Visual/Audio Alert: Triggers an LED and Buzzer upon confirmed fall.

🛠️ Hardware Requirements

Microcontroller: ESP32 Dev Kit V1 (or Arduino Uno)

Sensor: MPU6050 (6-Axis Accelerometer & Gyroscope)

Output: Active Buzzer & LED

Connection: I2C Protocol (SDA, SCL)

🔌 Wiring (ESP32)

| MPU6050 Pin | ESP32 Pin |
| VCC | 3.3V |
| GND | GND |
| SDA | GPIO 21 |
| SCL | GPIO 22 |

📐 The Algorithm

The system calculates the Total Acceleration Vector (AM):

$$AM = \sqrt{Ax^2 + Ay^2 + Az^2}$$

Stage 1 (Free Fall): Detects if $AM < 0.5G$ (Device dropping).

Stage 2 (Impact): Detects if $AM > 3.0G$ (Hitting the ground).

Stage 3 (Inactivity): Waits 5 seconds to check if the user recovers or remains still.

🚀 How to Run

Install Arduino IDE.

Install the Adafruit MPU6050 and Adafruit Unified Sensor libraries via Library Manager.

Upload FallDetection.ino to your board.

Open Serial Monitor (115200 baud) to view real-time data.

📜 License

MIT License
