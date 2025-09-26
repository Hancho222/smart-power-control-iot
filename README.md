# smart-power-control-iot
IoT-based Smart Power &amp; Control Monitoring System (EE Portfolio Project)
# ⚡ Smart Power & Control IoT Monitoring System

## 🔍 Problem Statement
In small-to-medium industrial environments and server rooms, there is often **no affordable real-time monitoring and control system** for electrical and thermal parameters.  
This leads to:
- Delayed detection of abnormal conditions (overcurrent, overheating)
- Energy waste and unnecessary costs
- Potential equipment damage due to a lack of an automated response

## 🎯 Project Goal
To build a **low-cost, end-to-end IoT monitoring and control system** that integrates:
- Current & temperature sensing
- Microcontroller-based data acquisition
- IoT communication (MQTT/HTTP)
- Cloud dashboard visualization (Grafana/InfluxDB)
- Automatic control logic (fan/motor actuation, anomaly detection)

## 🛠 System Architecture (Draft)

flowchart LR
  %% SENSORS
  subgraph S[Sensors & Actuators]
    CS[ACS712<br/>Current Sensor]
    TS[DS18B20 / LM35<br/>Temperature Sensor]
    FAN[Cooling Fan (12V/5V)]
  end

  %% EDGE/MCU
  subgraph E[Edge Device: MCU (ESP32)]
    ADC[ADC / 1-Wire Read<br/>Sampling & Timestamp]
    FILT[Signal Processing<br/>(Moving Average / Filter)]
    CTRL[Control Logic<br/>(Threshold / PID)]
    NET[Networking<br/>(Wi-Fi, MQTT/HTTP)]
    GPIO[GPIO / PWM Output]
  end

  %% CLOUD
  subgraph C[Cloud / Server]
    direction TB
    BRK[MQTT Broker<br/>(e.g., Mosquitto)]
    TGF[Telegraf / Data Parser]
    DB[(InfluxDB<br/>Time-Series DB)]
    GF[Grafana<br/>Dashboard]
  end

  %% FLOWS
  CS --> ADC
  TS --> ADC
  ADC --> FILT --> CTRL
  CTRL --> GPIO --> FAN

  %% UPLOAD PATH
  FILT --> NET --> BRK --> TGF --> DB --> GF

  %% ALERTS/LOGGING
  CTRL -. Overcurrent / Overheat Event Log .-> DB
  GF -. Alerts / Notifications (optional) .-> E
