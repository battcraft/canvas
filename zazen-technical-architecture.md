# ZAZEN SYSTEMS Technical Architecture Document

## System Integration Overview

ZAZEN SYSTEMS employs automotive-grade components originally developed for electric vehicle and marine propulsion applications, integrated into a sophisticated refrigeration control platform. This architecture provides industrial-grade reliability, unified control, real-time monitoring, and hybrid power capabilities unmatched in conventional commercial refrigeration.

---

## System Block Diagram

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                        ZAZEN SMART FREEZER SYSTEM                               │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                 │
│  ┌──────────────────┐      CAN Bus (250 kbps)     ┌───────────────────────┐   │
│  │   NAYANA HMI     │◄───────────────────────────►│     ASTRA VCU         │   │
│  │   4.3" Display   │                              │  (Master Controller)  │   │
│  │ ───────────────  │                              │ ─────────────────────  │   │
│  │ • Temperature    │                              │ • Sensor acquisition  │   │
│  │ • Energy trends  │                              │ • Control algorithms  │   │
│  │ • Inventory      │                              │ • ML inference        │   │
│  │ • Alerts/Alarms  │                              │ • IoT gateway         │   │
│  │ • Settings UI    │                              │ • CAN bus master      │   │
│  └──────────────────┘                              └───────┬───────────────┘   │
│                                                            │                   │
│                              ┌─────────────────────────────┼───────────────┐   │
│                              │                             │               │   │
│                              ▼                             ▼               ▼   │
│  ┌──────────────────┐  ┌──────────────┐  ┌───────────────────┐  ┌──────────┐  │
│  │  EV TRACTION     │  │  DC-DC       │  │  SOLID STATE      │  │  EEV     │  │
│  │  INVERTER        │  │  CONVERTER   │  │  RELAY / E-FUSE   │  │  DRIVER  │  │
│  │  (5kW rated)     │  │  48V→12V/5V  │  │  Protection       │  │          │  │
│  │                  │  │  /3.3V       │  │  & Switching      │  │          │  │
│  └────────┬─────────┘  └──────┬───────┘  └─────────┬─────────┘  └────┬─────┘  │
│           │                   │                     │                 │        │
│           ▼                   ▼                     ▼                 ▼        │
│  ┌──────────────────┐  ┌──────────────────────────────────┐  ┌──────────────┐ │
│  │ BLDC COMPRESSOR  │  │ Sensors & Peripherals            │  │  ELECTRONIC  │ │
│  │ Variable Speed   │  │ ──────────────────────           │  │  EXPANSION   │ │
│  │ 2000-3500 RPM    │  │ • Temp sensors (±0.1°C)         │  │  VALVE       │ │
│  │ R290 Refrigerant │  │ • Pressure transducers          │  │  (Stepper)   │ │
│  └──────────────────┘  │ • Energy meter                   │  └──────────────┘ │
│                        │ • Door switches                  │                   │
│                        │ • Ambient temp/humidity          │                   │
│                        │ • ESP32-CAM (optional)           │                   │
│                        │ • LED lighting                   │                   │
│                        │ • DC fan                         │                   │
│                        └──────────────────────────────────┘                   │
│                                                                                │
│  ┌────────────────────────────── 48V DC BUS ──────────────────────────────┐   │
│  │                                                                         │   │
│  │  ◄── AC-DC Converter ──┤├── Solar Panels ──┤├── Battery Bank ──┤      │   │
│  │      (Grid Power)              (Off-grid)         (Backup)            │   │
│  │                                    │                                   │   │
│  │                         ┌──────────┴──────────┐                        │   │
│  │                         │  1.5kW AGNI Charger │                        │   │
│  │                         │  (Solar/Battery)    │                        │   │
│  │                         └─────────────────────┘                        │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                                                                 │
│  ┌─────────────────────────── CONNECTIVITY ──────────────────────────────┐    │
│  │                                                                        │    │
│  │  Wi-Fi / 4G Cellular ──► Cloud Platform ──► Mobile App / Web Dashboard│    │
│  │  • Real-time data sync        • Historical analytics                  │    │
│  │  • OTA firmware updates       • Fleet management                      │    │
│  │  • Alert notifications        • Predictive maintenance                │    │
│  │  • Remote diagnostics         • Compliance reports                    │    │
│  └────────────────────────────────────────────────────────────────────────┘    │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## Component Specifications & Integration

### 1. Astra VCU (Master Controller)

**Function**: System brain orchestrating all refrigeration operations

**Hardware**:
- Automotive-qualified Renesas R7FA6M3 microcontroller (Arm Cortex-M4, 120 MHz)
- CAN bus transceiver for communication with HMI and peripherals
- Multiple ADC channels for sensor inputs (16-bit resolution)
- PWM outputs for EEV and fan control
- Digital I/O for relay control and door switches
- SD card storage for local data logging
- Wi-Fi/4G cellular module for cloud connectivity

**Software Functions**:
- **Compressor Control**: Variable speed modulation algorithm (PID control with adaptive tuning)
- **EEV Control**: Superheat management (target 5-8°C superheat)
- **Defrost Management**: Intelligent defrost cycles based on usage patterns
- **Temperature Monitoring**: Multi-zone temperature tracking with alarm thresholds
- **Energy Analytics**: Real-time power consumption tracking and optimization
- **Predictive Maintenance**: ML algorithms detect anomalies (Isolation Forest model)
- **IoT Gateway**: MQTT protocol for cloud platform communication
- **CAN Bus Master**: Coordinates communication with Nayana HMI

**Key Algorithms**:
- Adaptive PID for compressor speed control
- Superheat calculation: `Superheat = Suction_Temp - Saturation_Temp(Suction_Pressure)`
- Predictive defrost scheduling based on door openings and ambient humidity
- Anomaly detection using Isolation Forest for predictive maintenance

---

### 2. Nayana 4.3" HMI Display

**Function**: Professional touchscreen interface for system monitoring and control

**Hardware**:
- 4.3" capacitive touchscreen LCD (480×272 resolution)
- Resistive touch option available for gloved operation
- Renesas RA6M3 MCU for UI rendering
- CAN bus interface for VCU communication
- Ambient light sensor for auto-brightness
- IP65 rated front panel (water/dust resistant)

**User Interface Screens**:

**1. Dashboard (Home Screen)**
- Real-time temperature for all three zones
- Current compressor RPM and power consumption
- Energy usage today/this week/this month
- Active alerts/warnings
- Wi-Fi/cloud connection status

**2. Temperature Trends**
- Historical temperature graphs (1 hour, 1 day, 1 week views)
- Min/max temperature markers
- Excursion events highlighted
- Setpoint adjustment interface

**3. Energy Analytics**
- kWh consumption over time
- Cost calculations (user-configurable electricity rate)
- Comparison to baseline (before retrofit)
- Efficiency score (0-100)

**4. Inventory Management** (Optional Feature)
- ESP32-CAM integration for visual inventory
- Manual inventory tracking
- Low-stock alerts
- FIFO tracking for perishables

**5. System Diagnostics**
- Sensor readings (all temperatures, pressures)
- Compressor runtime hours
- Defrost cycle history
- Error codes and troubleshooting

**6. Settings**
- Temperature setpoint adjustment (-18°C to -24°C)
- Alert thresholds configuration
- Wi-Fi network setup
- Defrost schedule override
- User access control

---

### 3. EV Traction Inverter (5kW Rated)

**Function**: Precision BLDC motor drive for variable-speed compressor control

**Hardware**:
- Three-phase IGBT bridge (rated 5kW continuous)
- Gate driver ICs with shoot-through protection
- Current sensing on all three phases
- DC link capacitor bank for ripple current handling
- Thermal management: Heat sink + temperature sensor
- Overcurrent/overvoltage/overtemperature protection

**Specifications**:
- Input voltage: 12V DC or 24V DC (auto-detect)
- Output: Three-phase variable frequency (50-300 Hz)
- Current rating: 200A peak @ 24V
- Efficiency: >95% at rated load
- Control method: Field-Oriented Control (FOC) for smooth operation

**Integration with Astra VCU**:
- VCU sends speed command via analog voltage (0-5V) or PWM signal
- 0V = 2000 RPM (minimum speed)
- 5V = 3500 RPM (maximum speed)
- Linear interpolation for intermediate speeds
- Inverter provides fault signals back to VCU (over-temp, over-current)

**Key Features**:
- Smooth acceleration/deceleration ramps (configurable 1-10 sec)
- Sensorless motor control (no hall sensors required)
- Thermal derating at high ambient temperatures
- Silent operation (ultrasonic PWM frequency)

---

### 4. Variable-Speed BLDC Compressor

**Function**: Core refrigeration component with variable capacity

**Specifications**:
- Motor type: 3-phase brushless DC (BLDC)
- Speed range: 2000-3500 RPM (continuously variable)
- Refrigerant: R290 (propane), charge 100-150g
- Cooling capacity: 800-2000W @ 24V (varies with speed)
- Voltage: 12V or 24V DC operation
- Current draw:
  - 2000 RPM: 0.67-1.02 mA (minimum load)
  - 2500 RPM: 1.63-1.78 mA
  - 3000 RPM: 2.39-2.54 mA
  - 3500 RPM: 3.15-3.61 mA
- Compressor type: Rotary (for small units) or Scroll (for larger units)

**Speed Control Strategy**:
- **Idle/Steady State** (2000 RPM): Minimal power draw, maintains set temperature
- **Normal Operation** (2200-2800 RPM): Responds to door openings, ambient heat gain
- **High Demand** (2800-3500 RPM): Product loading, defrost recovery, high ambient
- **Adaptive Modulation**: VCU continuously adjusts speed based on temperature error

**Benefits vs. Fixed-Speed**:
- 25-40% energy savings (no on-off cycling waste)
- ±0.5°C temperature stability (vs. ±2°C for fixed-speed)
- Reduced mechanical wear (no hard starts)
- Quieter operation (low speed most of the time)

---

### 5. Electronic Expansion Valve (EEV)

**Function**: Precision refrigerant flow control for optimal system efficiency

**Hardware**:
- Stepper motor valve (200-500 steps full range)
- Stainless steel body, rated for R290
- Orifice size: 1.0-1.5mm (varies by application)
- Operating range: 0-100% open

**Control Strategy**:
- **Target**: Maintain 5-8°C superheat at compressor suction
- **Measurement**: Suction temp sensor + suction pressure transducer
- **Calculation**: `Superheat = T_suction - T_saturation(P_suction)`
- **Adjustment**: PID control adjusts EEV opening every 2-5 seconds

**Benefits vs. TXV (Thermostatic Expansion Valve)**:
- Precise control across all operating conditions
- Faster response to load changes
- Optimizes efficiency at part-load (variable speed compressor)
- No hunting/oscillation issues

---

### 6. 48V DC Bus Power Architecture

**Function**: Unified power distribution for hybrid solar/battery/grid operation

**System Configuration**:

```
           ┌─── AC-DC Converter ◄── Grid Power (230V AC)
           │
48V DC Bus ┼─── Solar Charge Controller ◄── Solar Panels (PV array)
           │
           ┼─── Battery Bank (48V LiFePO4, 50-200Ah)
           │
           └─── 1.5kW AGNI Charger (manages battery charging)
```

**Power Distribution**:
- **High Power Loads** (48V direct):
  - EV traction inverter → BLDC compressor
  - DC fan (48V model)

- **Low Power Loads** (via DC-DC converter):
  - 12V: Astra VCU, relays, DC fan (12V model), sensors
  - 5V: IoT modules, Wi-Fi/4G modem, ESP32-CAM
  - 3.3V: Precision sensors, microcontroller peripherals
  - LED lighting: 12V or 24V LED strips

**DC-DC Converter Specifications**:
- Input: 48V DC (36-60V range)
- Outputs:
  - 12V @ 10A (120W)
  - 5V @ 5A (25W)
  - 3.3V @ 3A (10W)
- Efficiency: >90%
- Isolation: 1500V DC (safety requirement)

**Hybrid Power Benefits**:
- **Solar Integration**: Direct DC coupling, no inverter losses
- **Battery Backup**: Seamless transition during grid outages
- **Off-Grid Capable**: Ideal for rural/remote locations
- **Load Shifting**: Charge batteries during off-peak, run on battery during peak rates
- **Lower Power Draw**: DC systems 10-15% more efficient than AC equivalents

---

### 7. Solid State Relay / E-Fuse

**Function**: Intelligent power switching and protection

**Hardware**:
- Back-to-back MOSFETs for bidirectional switching
- Current sensing shunt resistor
- Microcontroller for intelligent control
- Thermal management (heat sink)

**Features**:
- **Soft Start**: Gradual current ramp-up prevents inrush
- **Overcurrent Protection**: Trip at 1.5× rated current within 100ms
- **Fault Isolation**: Disconnect faulty loads to protect system
- **Status Reporting**: Real-time current/voltage monitoring to VCU
- **Silent Operation**: No mechanical relay clicking

**Benefits vs. Mechanical Contactors**:
- Higher reliability (no wear from arcing)
- Faster switching (microseconds vs. milliseconds)
- Intelligent protection features
- Longer lifespan (millions of cycles)

---

### 8. Sensor Suite

**Temperature Sensors**:
- Type: NTC thermistors (10kΩ @ 25°C) or PT1000 RTDs
- Accuracy: ±0.1°C after calibration
- Range: -40°C to +85°C
- Locations:
  - **Zone 1 Temperature** (left compartment)
  - **Zone 2 Temperature** (center compartment)
  - **Zone 3 Temperature** (right compartment)
  - **Suction Line Temperature** (superheat calculation)
  - **Discharge Line Temperature** (compressor health monitoring)
  - **Ambient Temperature** (outside freezer cabinet)

**Pressure Transducers**:
- Type: Piezo-resistive with signal conditioning
- Accuracy: ±0.5% full scale
- Range: 0-2 MPa (0-290 psi)
- Locations:
  - **Suction Pressure** (low side, superheat calculation)
  - **Discharge Pressure** (high side, system health)

**Other Sensors**:
- **Energy Meter**: Hall-effect current sensor + voltage divider, calculates real-time power
- **Door Switches**: Magnetic reed switches, one per lid
- **Ambient Humidity** (optional): Capacitive RH sensor for defrost optimization
- **Vibration Sensor** (optional): Accelerometer for compressor health monitoring

---

### 9. Communication & IoT Platform

**Local Communication**:
- **CAN Bus**: 250 kbps, connects Astra VCU ↔ Nayana HMI
- **I²C**: Sensor interface for temperature/humidity sensors
- **SPI**: High-speed interface for energy meter IC
- **UART**: Debug console, GPS module (for mobile applications)

**Cloud Connectivity**:
- **Wi-Fi**: 2.4 GHz 802.11 b/g/n for in-premise connectivity
- **4G Cellular**: Backup connectivity for critical alerts
- **Protocol**: MQTT over TLS (secure, lightweight)
- **Cloud Platform**: AWS IoT Core or Azure IoT Hub

**Data Transmission**:
- **Real-time**: Temperature, energy, alerts (every 30 seconds)
- **Historical**: 5-minute aggregated data for trends
- **Events**: Door openings, defrost cycles, alarm conditions (immediate)
- **Firmware OTA**: Background downloads, scheduled installation

**Mobile App & Web Dashboard**:
- **Platforms**: iOS, Android, Web browser
- **Features**:
  - Live temperature monitoring
  - Energy analytics and cost tracking
  - Alert notifications (push + SMS)
  - Remote setpoint adjustment
  - Fleet management (multi-location)
  - Compliance reports (FSSAI, WHO PQS)
  - Predictive maintenance alerts

---

## Installation Specifications

### Electrical Installation

**12V DC System**:
- Wire gauge: AWG 13 (2.5mm²) for runs ≤8 ft, AWG 8 (10mm²) for runs ≤23 ft
- Fuse: 30A (QDZH25G/30G/35G models), close to battery
- Main switch: 20A minimum rating
- Battery: 100-200Ah recommended for off-grid

**24V DC System**:
- Wire gauge: AWG 13 (2.5mm²) for runs ≤26 ft
- Fuse: 15A (24V models), close to battery
- Main switch: 20A minimum rating
- Battery: 50-100Ah recommended for off-grid

**48V DC System** (New Premium Freezers):
- Wire gauge: AWG 10 (5.5mm²) for main bus
- Fuse: 50A (48V to 12V/24V DC-DC converter)
- Battery: 50-100Ah LiFePO4 recommended

**Grounding**:
- All metal chassis must be bonded to negative terminal
- Ground fault protection recommended for safety

---

### Refrigeration Installation

**Compressor Mounting**:
- Vibration isolators required (rubber grommets)
- Orientation: Upright only (oil return considerations)
- Clearance: 50mm minimum for airflow

**EEV Installation**:
- Mount on liquid line before evaporator inlet
- Bulb sensor on suction line, 150mm from compressor
- Insulate suction line to prevent condensation

**R290 Refrigerant Handling**:
- Charge quantity: 100-150g (below flammability limit)
- Leak detection: Electronic sensor recommended
- Ventilation: Install in well-ventilated area (propane heavier than air)
- Electrical: Spark-proof components per IEC 60335-2-89

---

## System Operation Modes

### 1. Normal Cooling Mode
- Compressor modulates 2000-3500 RPM based on temperature error
- EEV maintains 5-8°C superheat
- Fan runs continuously at low speed (noise reduction)
- VCU logs data every 30 seconds

### 2. High Demand Mode
- Triggered by: Large temperature rise, door left open, product loading
- Compressor runs at 3000-3500 RPM until setpoint reached
- EEV opens further to increase capacity
- Alert sent if demand persists >15 minutes

### 3. Defrost Mode
- **Intelligent Scheduling**: Based on door openings, ambient humidity
- **Process**:
  1. Compressor stops
  2. Defrost heater activates (optional, or off-cycle defrost)
  3. Temperature monitored, terminates at +5°C or 15 min timeout
  4. Drip time: 2 minutes for condensate drainage
  5. Compressor restarts, high-speed recovery
- **Frequency**: Typically 1-2× per day, adaptive

### 4. Standby Mode
- Triggered by: User override, maintenance mode
- Compressor stopped but monitoring continues
- Alerts sent if temperature rises above threshold
- Can be initiated remotely via mobile app

### 5. Battery Backup Mode (Off-Grid Systems)
- Automatic switchover when grid fails
- Reduced compressor speed (1800-2500 RPM) to conserve battery
- Non-essential loads disabled (display brightness reduced, Wi-Fi off)
- SMS alert sent to user

---

## Error Detection & Protection

### Battery Protection (Table 1, 3)
| System Voltage | Cut-In  | Cut-Out (Std) | Cut-Out (Max) |
|----------------|---------|---------------|---------------|
| 12V            | 10.9V   | 10.4V / 11.7V | 12.5V         |
| 24V            | 22.7V   | 21.3V / 24.2V | 26.0V         |

- **Under-voltage**: Compressor stops to protect battery, resumes when voltage recovers
- **Over-voltage**: Immediate shutdown to prevent damage

### Thermal Protection
- **60°C Ambient Cut-Out**: Compressor stops if ambient > 60°C
- **75°C Electronic Unit Cut-Out**: Controller overheating protection
- **Discharge Temp Alarm**: Alert if discharge > 120°C (refrigerant breakdown risk)

### Motor Protection
- **Locked Rotor**: Detected by current spike, compressor stopped
- **Minimum Speed Error**: Alert if RPM < 1850 (system overload)
- **Differential Pressure**: Alarm if ΔP > 6 kg/cm³ (blockage or restriction)

### Fan Protection
- **Over-Current**: Fan stopped if current > 1A (bearing failure indication)

### Error Codes (Table 5)

| Flash Code | Error Description                                    |
|------------|------------------------------------------------------|
| 1 Flash    | Battery voltage outside cut-out setting              |
| 2 Flashes  | Fan over-current (>1A)                              |
| 3 Flashes  | Motor locked rotor or differential pressure too high |
| 4 Flashes  | Minimum motor speed error (system overloaded)        |
| 5 Flashes  | Thermal cut-out (ambient >75°C or unit >75°C)       |
| 6 Flashes  | Controller hardware failure                          |

---

## Performance Metrics

### Energy Savings
- **Baseline** (fixed-speed): 8-12 kWh/day for 500L chest freezer
- **ZAZEN System**: 5-7 kWh/day (30-40% reduction)
- **Annual Savings**: ₹8,000 - ₹12,000 per unit (@ ₹7/kWh)
- **Fleet Savings**: 10-unit installation saves ₹80,000 - ₹1,20,000 per year

### Temperature Stability
- **Fixed-Speed**: ±2°C fluctuation (on-off cycling)
- **ZAZEN System**: ±0.5°C fluctuation (continuous modulation)
- **Compliance**: Meets FSSAI, WHO PQS, FDA guidelines for food/vaccine storage

### Reliability Improvements
- **Compressor Lifespan**: 30-50% longer (reduced start/stop cycles)
- **Maintenance Intervals**: 50% reduction in service calls
- **Uptime**: 99.5%+ (predictive maintenance prevents failures)

### ROI Analysis
- **Retrofit Cost**: ₹40,000 - ₹75,000 per unit
- **Energy Savings**: ₹8,000 - ₹12,000 per year
- **Maintenance Savings**: ₹3,000 - ₹5,000 per year
- **Payback Period**: 18-24 months
- **10-Year NPV**: ₹80,000 - ₹1,20,000 per unit

---

## Competitive Advantages

### vs. Conventional Freezers
| Feature | Conventional | ZAZEN System |
|---------|-------------|--------------|
| Compressor | Fixed-speed | Variable-speed (2000-3500 RPM) |
| Energy Consumption | 8-12 kWh/day | 5-7 kWh/day |
| Temperature Stability | ±2°C | ±0.5°C |
| Monitoring | None or basic | Real-time IoT + predictive maintenance |
| Power Source | AC only | DC (12V/24V/48V), solar/battery compatible |
| Control Interface | Mechanical dial | 4.3" touchscreen HMI |
| Maintenance | Reactive | Predictive (ML algorithms) |
| Refrigerant | R134a (GWP 1430) | R290 (GWP 3) |

### vs. Other "Smart" Freezers
- **Automotive-Grade Components**: Proven EV/marine hardware, not consumer IoT gadgets
- **Open Architecture**: CAN bus allows third-party sensor integration
- **Hybrid Power**: True off-grid capability, not just "solar-ready"
- **Predictive Maintenance**: ML algorithms, not just threshold alerts
- **Retrofit Option**: Transform existing assets, not just new equipment

---

## Future Roadmap

### Phase 1 (Current)
- BLDC compressor retrofit kits
- IoT monitoring platform
- Mobile app (iOS/Android)
- R290 refrigerant option

### Phase 2 (6-12 months)
- Computer vision inventory management (ESP32-CAM integration)
- Voice control (Alexa/Google Assistant)
- Energy-as-a-Service model (pay per kWh of cooling)
- Fleet optimization AI (multi-unit load balancing)

### Phase 3 (12-24 months)
- Walk-in cooler/freezer systems (scaled-up architecture)
- Refrigerated transport integration (truck/van refrigeration)
- Blockchain-based cold chain tracking (pharma compliance)
- White-label platform for OEMs

---

*ZAZEN SYSTEMS—Precision Engineered Cooling*
