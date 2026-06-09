# Embedded Electronics Health Monitoring & Protection Platform

## Overview

This project is an embedded hardware monitoring and validation platform designed to simulate health monitoring functions commonly used in electronic, aerospace, defense, and industrial systems.

The system continuously monitors electrical current and temperature conditions, automatically activates cooling responses when predefined thresholds are exceeded, and logs telemetry data for validation and analysis.

The project demonstrates practical engineering skills in:

- Embedded Systems
- Sensor Integration
- Hardware Validation
- Fault Detection
- Telemetry Logging
- Data Analysis
- System Troubleshooting

---

## Problem Statement

Electronic systems can experience abnormal current draw, overheating, and sensor failures that may lead to degraded performance, reduced reliability, or hardware damage.

Many low-cost embedded systems lack continuous monitoring and automated protection mechanisms.

This project aims to develop a simplified electronics health monitoring platform capable of:

- Monitoring electrical and thermal conditions
- Detecting abnormal operating states
- Triggering automated cooling responses
- Logging system telemetry for validation and troubleshooting

---

## System Architecture

```text
┌─────────────────┐
│ Temperature     │
│ Sensor          │
│ (DS18B20)       │
└────────┬────────┘
         │
┌────────▼────────┐
│                 │
│     ESP32       │
│                 │
└────────┬────────┘
         │
┌────────▼────────┐
│ Current Sensor  │
│ (ACS712)        │
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Fault Detection │
│ Threshold Logic │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ MOSFET Control  │
│ (IRLZ44N)       │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ 12V Cooling Fan │
└─────────────────┘
         │
         ▼
┌─────────────────┐
│ Telemetry       │
│ Logging         │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Python Logger   │
│ CSV Storage     │
│ Data Analysis   │
└─────────────────┘
```

---

## Hardware Components

| Component | Function |
|------------|------------|
| ESP32 DevKit V1 | Main controller |
| DS18B20 | Temperature monitoring |
| ACS712 (20A) | Current monitoring |
| IRLZ44N MOSFET | Fan control |
| 12V DC Fan | Cooling response |
| 12V Power Supply | System power |
| Breadboard & Jumpers | Prototyping |

---

## Firmware Features

### Sensor Acquisition

- Temperature measurement
- Current measurement
- Continuous monitoring

### Protection Logic

- Temperature threshold detection
- Overcurrent threshold detection
- Fault state identification

### Automated Response

- Cooling fan activation
- Fault reporting
- Event logging

### Telemetry Output

Serial transmission of:

```text
timestamp,temp,current,fan_state,fault_code
```

Example:

```text
15230,28.4,0.72,0,0
16340,31.2,0.78,1,0
18100,36.5,0.81,1,1
```

---

## Python Telemetry Logger

A Python-based validation tool records real-time telemetry from the ESP32.

Features:

- Serial communication
- CSV data logging
- Timestamp generation
- Temperature plotting
- Current plotting
- Event analysis

Example output:

```text
Timestamp,Temp_C,Current_A,Fan_State,Fault_Code
14:00:01,28.4,0.72,0,0
14:00:02,28.5,0.73,0,0
14:00:03,30.1,0.75,1,0
```

---

## Validation Plan

| Test ID | Description |
|----------|-------------|
| TC-01 | Temperature sensor verification |
| TC-02 | Current sensor verification |
| TC-03 | Fan threshold activation |
| TC-04 | Thermal response validation |
| TC-05 | Overcurrent detection |
| TC-06 | Sensor fault detection |
| TC-07 | Telemetry logging verification |
| TC-08 | Data visualization verification |

---

## Expected Results

- Stable temperature monitoring
- Stable current monitoring
- Automatic cooling activation
- Fault event detection
- Telemetry data collection
- Validation graphs for system behavior analysis

---

## Engineering Skills Demonstrated

### Hardware

- Sensor Integration
- Power Electronics
- MOSFET Switching
- Embedded Hardware Prototyping

### Firmware

- Embedded C/C++
- Sensor Drivers
- State Logic
- Fault Detection

### Validation

- Test Planning
- Data Logging
- Verification & Validation
- Troubleshooting

### Software

- Python
- Serial Communication
- CSV Data Processing
- Data Visualization

---

## Future Improvements

- OLED Status Display
- MQTT Communication
- Grafana Dashboard
- Wireless Monitoring
- Predictive Maintenance Algorithms
- PCB Design & Manufacturing

---

## Author

Joseph Ryoo

Electrical Engineer

Focused on Embedded Systems, Hardware Validation, Electrical Testing, and System Integration.
