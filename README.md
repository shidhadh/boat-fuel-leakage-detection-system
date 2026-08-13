# Boat Fuel Leakage Detection and Automatic Motor Shutdown System

## 📌 Project Overview

The **Boat Fuel Leakage Detection and Automatic Motor Shutdown System (BFLDS)** is an **IoT-based safety system** designed to detect fuel leakage in boat engine compartments and automatically take protective action.

The system uses an **ESP32 microcontroller**, **MQ-2 gas sensor**, **Blynk IoT**, **relay module**, **fuel pump**, and **buzzer**.

The MQ-2 sensor continuously monitors combustible gas/fuel vapour levels. The ESP32 processes the sensor data and sends the gas level information to the **Blynk IoT platform**, allowing the user to monitor the fuel leakage status remotely.

When the detected gas level exceeds the predefined threshold, the system activates the buzzer and operates the relay to automatically shut down the fuel pump.

## 🎯 Objectives

* Detect fuel vapour leakage continuously.
* Monitor gas levels using an MQ-2 gas sensor.
* Display gas sensor readings remotely using **Blynk IoT**.
* Provide an immediate audible warning using a buzzer.
* Automatically stop the fuel pumping motor when a hazardous gas level is detected.
* Use ESP32 for real-time sensing, processing, and IoT communication.
* Provide a low-cost IoT-based safety solution for boats.

## 🌐 IoT Integration – Blynk IoT

**Blynk IoT** is used to provide remote monitoring of the fuel leakage detection system.

The ESP32 connects to Wi-Fi and communicates with the Blynk IoT platform. The gas sensor reading obtained from the MQ-2 sensor is sent to Blynk, where it can be viewed through a smartphone or web dashboard.

### IoT Working

```text
MQ-2 Gas Sensor
       │
       ▼
     ESP32
       │
       │ Wi-Fi
       ▼
   Blynk IoT
       │
       ▼
 Smartphone / Web Dashboard
```

The Blynk IoT platform can be used to monitor the gas sensor value and observe the system status remotely.

## ⚙️ Components Used

| Component       | Purpose                                                |
| --------------- | ------------------------------------------------------ |
| ESP32           | Main controller and Wi-Fi communication                |
| MQ-2 Gas Sensor | Detects combustible gas/fuel vapour                    |
| Blynk IoT       | Remote monitoring of sensor data                       |
| Relay Module    | Controls the fuel pump                                 |
| Active Buzzer   | Provides an audible alarm                              |
| Fuel Pump Motor | Pumps fuel and is automatically stopped during leakage |
| Power Supply    | Provides power to the system                           |

## 🔌 ESP32 Pin Configuration

| ESP32 Pin | Function       | Connected Component |
| --------- | -------------- | ------------------- |
| GPIO 34   | Analog Input   | MQ-2 Sensor A0      |
| GPIO 26   | Digital Output | Relay Control       |
| GPIO 27   | Digital Output | Active Buzzer       |
| VIN       | 5V Input       | Power Supply        |
| GND       | Ground         | Common Ground       |

The project uses GPIO 34 for MQ-2 analog sensing and GPIO 26 for relay control.

## 🔄 Working Principle

1. The ESP32 initializes the system.
2. The MQ-2 sensor is allowed to warm up.
3. The ESP32 continuously reads the analog output of the MQ-2 sensor.
4. The gas sensor value is processed by the ESP32.
5. The sensor value is sent to **Blynk IoT through Wi-Fi**.
6. The user can monitor the gas level through the Blynk dashboard.
7. The sensor reading is compared with the predefined threshold.
8. Under normal conditions:

   * Fuel pump operates normally.
   * Buzzer remains OFF.
   * Gas level is displayed on Blynk.
9. When the gas level exceeds the threshold:

   * Buzzer turns ON.
   * Relay is activated.
   * Fuel pump is switched OFF.
   * Updated gas level/status can be monitored through Blynk IoT.
10. The system continues monitoring the gas level.

The documented alarm threshold is **1500 ADC counts**, with a hysteresis value of **100 ADC counts**.

## 🚨 Detection and IoT Flow

```text
              START
                │
                ▼
        Initialize ESP32
                │
                ▼
        Connect to Wi-Fi
                │
                ▼
        Connect to Blynk IoT
                │
                ▼
        MQ-2 Sensor Warm-up
                │
                ▼
         Read Gas Level
                │
          ┌─────┴─────┐
          ▼           ▼
     Send Data     Check Threshold
     to Blynk           │
          │       ┌─────┴─────┐
          │       ▼           ▼
          │      SAFE       LEAKAGE
          │       │           │
          │       ▼           ▼
          │    Pump ON     Buzzer ON
          │    Buzzer OFF   Relay ON
          │                  Pump OFF
          │       │           │
          └───────┴───────────┘
                  │
                  ▼
           Continue Monitoring
```

## 📊 Blynk IoT Monitoring

The Blynk IoT dashboard can be configured to display:

* **Real-time MQ-2 gas sensor value**
* **Fuel leakage status**
* **Alarm status**
* **Fuel pump status**

This allows the user to observe the condition of the boat's fuel system remotely through the Blynk IoT platform.

## 📊 Testing Results

| Test Parameter         | Result                           | Status |
| ---------------------- | -------------------------------- | ------ |
| Gas Detection Accuracy | Zero false positives observed    | PASS   |
| Alarm Response Time    | Under 500 ms                     | PASS   |
| Relay Switching        | 100% successful over 200 cycles  | PASS   |
| Motor Shutdown         | Immediate on threshold breach    | PASS   |
| Continuous Operation   | Stable for 8 hours               | PASS   |
| Power Stability        | Stable under 5V / 12V conditions | PASS   |

The reported testing results include a sub-500 ms alarm response, successful relay switching over 200 cycles, and stable 8-hour operation.

## 💻 Software and Technologies

* **Arduino IDE**
* **ESP32 Arduino Core**
* **C/C++**
* **Blynk IoT**
* Wi-Fi communication
* `analogRead()` for MQ-2 sensor measurement
* GPIO control for relay and buzzer

## 📁 Repository Structure

```text
Boat-Fuel-Leakage-Detection-System/
│
├── README.md
│
├── firmware/
│   └── boat_fuel_leakage_detection.ino
│
├── hardware/
│   ├── circuit_diagram.png
│   ├── block_diagram.png
│   └── hardware_setup.jpg
│
├── documentation/
│   └── Boat_Fuel_Leakage_Detection_System.pdf
│
├── images/
│   ├── project_model.jpg
│   ├── blynk_dashboard.jpg
│   └── testing.jpg
│
└── presentation/
    └── project_presentation.pptx
```

## 🔮 Future Improvements

* Push notifications for fuel leakage alerts.
* Cloud-based historical data logging.
* Multiple gas sensor nodes for larger boats.
* OLED/LCD display for onboard monitoring.
* Battery-backed low-power operation.
* GPS integration for leakage event location.
* Improved gas sensor calibration for more accurate fuel vapour measurement.

## 📄 Documentation

The complete project report is included in the `documentation` folder.

## ⚠️ Disclaimer

This project is an academic prototype intended for demonstration and development purposes. Actual marine deployment should use appropriate certified marine safety equipment and professional validation.

---

⭐ **If you find this project useful, consider giving the repository a star!**
