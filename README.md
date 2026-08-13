# 🚤 Boat Fuel Leakage Detection and Automatic Motor Shutdown System

## 📌 Project Overview

The **Boat Fuel Leakage Detection and Automatic Motor Shutdown System (BFLDS)** is an embedded safety system designed to detect fuel vapour leakage in boat engine compartments and automatically take protective action.

The system uses an **ESP32 microcontroller** and an **MQ-2 gas sensor** to continuously monitor combustible gas/fuel vapour levels. When the detected gas level exceeds the predefined threshold, the system activates a **buzzer alarm** and operates a **relay to shut down the fuel pump**, helping to reduce the risk of fire and explosion.

## 🎯 Objectives

* Detect fuel vapour leakage continuously.
* Provide an immediate audible warning using a buzzer.
* Automatically stop the fuel pumping motor when a hazardous level is detected.
* Use an ESP32 for real-time monitoring and control.
* Provide a low-cost embedded safety solution for small and medium-sized boats.

## ⚙️ Components Used

| Component       | Purpose                                    |
| --------------- | ------------------------------------------ |
| ESP32           | Main controller                            |
| MQ-2 Gas Sensor | Detects combustible gas/fuel vapour        |
| Relay Module    | Controls the fuel pump                     |
| Active Buzzer   | Provides an audible alarm                  |
| Fuel Pump Motor | Controlled according to detected gas level |
| Power Supply    | Provides power to the system               |

## 🔌 ESP32 Pin Configuration

| ESP32 Pin | Function       | Connected Component |
| --------- | -------------- | ------------------- |
| GPIO 34   | Analog Input   | MQ-2 Sensor A0      |
| GPIO 26   | Digital Output | Relay Control       |
| GPIO 27   | Digital Output | Active Buzzer       |
| VIN       | 5V Input       | Power Supply        |
| GND       | Ground         | Common Ground       |

The project report specifies GPIO 34 for the MQ-2 analog output, GPIO 26 for relay control, and GPIO 27 for the buzzer.

## 🔄 Working Principle

1. The ESP32 initializes the system.
2. The MQ-2 sensor is allowed to warm up.
3. The ESP32 continuously reads the sensor's analog output.
4. The sensor reading is compared with a predefined threshold.
5. Under normal conditions, the fuel pump operates and the buzzer remains OFF.
6. When the gas level exceeds the threshold:

   * The buzzer turns ON.
   * The relay is activated.
   * The fuel pump is switched OFF.
7. The system continues monitoring until the gas level returns to a safe range.

The documented alarm threshold is **1500 ADC counts**, with a hysteresis value of **100 ADC counts**.

## 🚨 Detection Flow

```text
              START
                │
                ▼
        Initialize ESP32
                │
                ▼
        MQ-2 Sensor Warm-up
                │
                ▼
         Read Gas Level
                │
                ▼
       Gas Level > 1500?
          /           \
        NO             YES
        │               │
        ▼               ▼
  Normal Operation   Buzzer ON
  Buzzer OFF         Relay ON
  Pump ON            Pump OFF
        │               │
        └───────┬───────┘
                ▼
        Continue Monitoring
```

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

## 💻 Software

* **Arduino IDE**
* **ESP32 Arduino Core**
* Embedded C/C++ firmware
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
│   └── testing.jpg
│
└── presentation/
    └── project_presentation.pptx
```

## 🔮 Future Improvements

* Wi-Fi-based remote monitoring.
* Smartphone notifications.
* Cloud-based data logging.
* Multiple gas sensor nodes.
* OLED/LCD display for gas level and system status.
* Battery-backed low-power operation.
* GPS integration for leakage event location logging.

# 🚤 Boat Fuel Leakage Detection and Automatic Motor Shutdown System

## 📌 Project Overview

The **Boat Fuel Leakage Detection and Automatic Motor Shutdown System (BFLDS)** is an embedded safety system designed to detect fuel vapour leakage in boat engine compartments and automatically take protective action.

The system uses an **ESP32 microcontroller** and an **MQ-2 gas sensor** to continuously monitor combustible gas/fuel vapour levels. When the detected gas level exceeds the predefined threshold, the system activates a **buzzer alarm** and operates a **relay to shut down the fuel pump**, helping to reduce the risk of fire and explosion.

## 🎯 Objectives

* Detect fuel vapour leakage continuously.
* Provide an immediate audible warning using a buzzer.
* Automatically stop the fuel pumping motor when a hazardous level is detected.
* Use an ESP32 for real-time monitoring and control.
* Provide a low-cost embedded safety solution for small and medium-sized boats.

## ⚙️ Components Used

| Component       | Purpose                                    |
| --------------- | ------------------------------------------ |
| ESP32           | Main controller                            |
| MQ-2 Gas Sensor | Detects combustible gas/fuel vapour        |
| Relay Module    | Controls the fuel pump                     |
| Active Buzzer   | Provides an audible alarm                  |
| Fuel Pump Motor | Controlled according to detected gas level |
| Power Supply    | Provides power to the system               |

## 🔌 ESP32 Pin Configuration

| ESP32 Pin | Function       | Connected Component |
| --------- | -------------- | ------------------- |
| GPIO 34   | Analog Input   | MQ-2 Sensor A0      |
| GPIO 26   | Digital Output | Relay Control       |
| GPIO 27   | Digital Output | Active Buzzer       |
| VIN       | 5V Input       | Power Supply        |
| GND       | Ground         | Common Ground       |

The project report specifies GPIO 34 for the MQ-2 analog output, GPIO 26 for relay control, and GPIO 27 for the buzzer.

## 🔄 Working Principle

1. The ESP32 initializes the system.
2. The MQ-2 sensor is allowed to warm up.
3. The ESP32 continuously reads the sensor's analog output.
4. The sensor reading is compared with a predefined threshold.
5. Under normal conditions, the fuel pump operates and the buzzer remains OFF.
6. When the gas level exceeds the threshold:

   * The buzzer turns ON.
   * The relay is activated.
   * The fuel pump is switched OFF.
7. The system continues monitoring until the gas level returns to a safe range.

The documented alarm threshold is **1500 ADC counts**, with a hysteresis value of **100 ADC counts**.

## 🚨 Detection Flow

```text
              START
                │
                ▼
        Initialize ESP32
                │
                ▼
        MQ-2 Sensor Warm-up
                │
                ▼
         Read Gas Level
                │
                ▼
       Gas Level > 1500?
          /           \
        NO             YES
        │               │
        ▼               ▼
  Normal Operation   Buzzer ON
  Buzzer OFF         Relay ON
  Pump ON            Pump OFF
        │               │
        └───────┬───────┘
                ▼
        Continue Monitoring
```

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

## 💻 Software

* **Arduino IDE**
* **ESP32 Arduino Core**
* Embedded C/C++ firmware
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
│   └── testing.jpg
│
└── presentation/
    └── project_presentation.pptx
```

## 🔮 Future Improvements

* Wi-Fi-based remote monitoring.
* Smartphone notifications.
* Cloud-based data logging.
* Multiple gas sensor nodes.
* OLED/LCD display for gas level and system status.
* Battery-backed low-power operation.
* GPS integration for leakage event location logging.


## ⚠️ Disclaimer

This project is an academic prototype intended for demonstration and development purposes. Actual marine deployment should use appropriate certified marine safety equipment and professional validation.

---

⭐ **If you find this project useful, consider giving the repository a star!**


## ⚠️ Disclaimer

This project is an academic prototype intended for demonstration and development purposes. Actual marine deployment should use appropriate certified marine safety equipment and professional validation.

---

⭐ **If you find this project useful, consider giving the repository a star!**
