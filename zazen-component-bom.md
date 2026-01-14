# ZAZEN SYSTEMS Component Bill of Materials (BOM)

## BOM Overview

This document provides a complete component breakdown for both ZAZEN product offerings:
1. **Premium Triple-Door Freezer** (new complete unit)
2. **Smart Retrofit Kit** (upgrade package for existing freezers)

---

## 1. Core Control System Components

| Component | Part/Model | Specifications | Qty | Unit Cost Est. | Notes |
|-----------|------------|----------------|-----|----------------|-------|
| **Astra VCU** | Custom PCB | Renesas R7FA6M3 MCU, CAN bus, ADC, I²C, SPI, Wi-Fi/4G | 1 | ₹8,000-₹12,000 | Master controller |
| **Nayana HMI** | 4.3" Display | 480×272 capacitive touch, Renesas RA6M3, CAN interface | 1 | ₹6,000-₹9,000 | User interface |
| **EV Traction Inverter** | 5kW BLDC Driver | 12/24V input, 3-phase output, FOC control, 200A peak | 1 | ₹12,000-₹18,000 | Motor drive |
| **DC-DC Converter** | 48V→12V/5V/3.3V | 150W total, isolated, >90% efficiency | 1 | ₹3,000-₹5,000 | Power distribution |
| **Solid State Relay** | E-fuse Module | MOSFET-based, 40A @ 12V, 20A @ 24V, current sensing | 1 | ₹2,500-₹4,000 | Intelligent switching |

**Core Control System Subtotal**: ₹31,500 - ₹48,000

---

## 2. Refrigeration Components

| Component | Part/Model | Specifications | Qty | Unit Cost Est. | Notes |
|-----------|------------|----------------|-----|----------------|-------|
| **BLDC Compressor** | Variable-speed | 2000-3500 RPM, R290, 12/24V DC, rotary or scroll | 1 | ₹18,000-₹28,000 | Core cooling |
| **Electronic Expansion Valve** | Stepper EEV | 200-500 steps, R290-rated, 1.0-1.5mm orifice | 1 | ₹4,000-₹6,000 | Refrigerant control |
| **Evaporator Coil** | Finned tube | Copper tubing, aluminum fins, optimized for R290 | 1 | ₹3,500-₹5,500 | Heat absorption |
| **Condenser Coil** | Finned tube | Copper tubing, aluminum fins, forced-air cooling | 1 | ₹3,000-₹4,500 | Heat rejection |
| **DC Fan (Condenser)** | 12V/24V DC | 120mm, 1.5A max, variable-speed via PWM | 1 | ₹1,200-₹1,800 | Airflow |
| **Filter Drier** | R290-compatible | Removes moisture and contaminants from refrigerant | 1 | ₹400-₹600 | Refrigerant quality |
| **Accumulator** | Suction line | Prevents liquid slugging, protects compressor | 1 | ₹1,500-₹2,500 | Compressor protection |
| **Sight Glass** | Liquid line | Visual refrigerant flow/moisture indicator | 1 | ₹300-₹500 | Diagnostics |
| **Service Valves** | Schrader type | For charging/recovery, R290-rated | 2 | ₹400-₹600 | Serviceability |
| **R290 Refrigerant** | Propane | 100-150g charge, GWP=3, high-purity | 1 charge | ₹200-₹400 | Refrigerant |
| **Refrigerant Tubing** | Copper | 1/4" and 3/8" OD, annealed, various lengths | - | ₹800-₹1,200 | Connections |

**Refrigeration Components Subtotal**: ₹33,300 - ₹51,600

---

## 3. Sensor Suite

| Component | Part/Model | Specifications | Qty | Unit Cost Est. | Notes |
|-----------|------------|----------------|-----|----------------|-------|
| **Temperature Sensors** | NTC 10kΩ or PT1000 | ±0.1°C accuracy, -40°C to +85°C range | 6 | ₹300-₹500 ea | Zones, suction, discharge, ambient |
| **Pressure Transducers** | Piezo-resistive | 0-2 MPa, ±0.5% FS, analog output | 2 | ₹2,000-₹3,000 ea | Suction + discharge |
| **Current Sensor** | Hall-effect | 0-50A, analog output, for energy metering | 1 | ₹800-₹1,200 | Power monitoring |
| **Voltage Divider** | Resistor network | For DC bus voltage measurement | 1 | ₹50-₹100 | Simple voltage sense |
| **Door Switches** | Magnetic reed | NO/NC, one per lid | 3 | ₹100-₹200 ea | Door status |
| **Humidity Sensor** (optional) | Capacitive RH | 0-100% RH, for defrost optimization | 1 | ₹600-₹1,000 | Ambient conditions |
| **Vibration Sensor** (optional) | MEMS accelerometer | 3-axis, for compressor health monitoring | 1 | ₹400-₹800 | Predictive maintenance |

**Sensor Suite Subtotal**: ₹7,850 - ₹13,400

---

## 4. Power System Components

### For Retrofit Kit (Customer's existing power)
| Component | Part/Model | Specifications | Qty | Unit Cost Est. | Notes |
|-----------|------------|----------------|-----|----------------|-------|
| **AC-DC Converter** | SMPS | 230V AC → 12V/24V DC, 300-500W | 1 | ₹3,000-₹5,000 | Grid power interface |
| **Fuses** | Blade/ANL fuse | 30A (12V) or 15A (24V) | 2 | ₹50-₹150 ea | Protection |
| **Main Switch** | DC-rated | 20-40A, manual disconnect | 1 | ₹300-₹600 | Safety disconnect |
| **Wire/Cable** | AWG 8-13 | Copper, per Table 2 specs, various lengths | - | ₹500-₹1,500 | Electrical connections |

**Power System (Retrofit) Subtotal**: ₹4,000 - ₹7,500

### For Premium New Freezer (48V DC Bus)
| Component | Part/Model | Specifications | Qty | Unit Cost Est. | Notes |
|-----------|------------|----------------|-----|----------------|-------|
| **AC-DC Converter** | SMPS | 230V AC → 48V DC, 500-800W, PFC | 1 | ₹6,000-₹10,000 | Grid power interface |
| **Solar Charge Controller** (optional) | MPPT | 48V, 20-30A, for PV array | 1 | ₹8,000-₹15,000 | Solar integration |
| **Battery Bank** (optional) | LiFePO4 | 48V, 50-100Ah, BMS included | 1 | ₹30,000-₹60,000 | Backup power |
| **1.5kW AGNI Charger** (optional) | DC-DC Charger | Battery charging from solar/grid | 1 | ₹10,000-₹15,000 | Battery management |
| **Bus Bars** | Copper | Heavy-duty 48V distribution | - | ₹1,000-₹2,000 | Power distribution |
| **Fuses/Breakers** | DC-rated | 50A main, various branch circuits | - | ₹1,000-₹2,000 | Protection |

**Power System (Premium) Subtotal**: ₹56,000 - ₹104,000 (with full solar/battery)

---

## 5. Mechanical Components (Premium New Freezer)

| Component | Part/Model | Specifications | Qty | Unit Cost Est. | Notes |
|-----------|------------|----------------|-----|----------------|-------|
| **Cabinet Shell** | Galvanized steel | 1.0-1.5mm thick, powder-coated navy blue | 1 | ₹15,000-₹25,000 | Outer structure |
| **Insulation** | PUF (Polyurethane foam) | 75-100mm thickness, CFC-free, R-value ~6 | - | ₹8,000-₹12,000 | Thermal insulation |
| **Inner Liner** | Aluminum | Embossed, food-grade, easy-clean surface | 1 | ₹5,000-₹8,000 | Interior walls |
| **Lids (3x)** | Galvanized steel + PUF | Top-opening, insulated, gold trim | 3 | ₹4,000-₹6,000 ea | Compartment access |
| **Hinges (3x sets)** | Heavy-duty | Counterbalanced, stainless steel | 3 | ₹1,500-₹2,500 ea | Lid support |
| **Handles (3x)** | Ergonomic | Gold-finished, commercial-grade | 3 | ₹800-₹1,200 ea | User interface |
| **Gaskets (3x)** | Magnetic rubber | Airtight seal, food-safe material | 3 | ₹600-₹1,000 ea | Sealing |
| **Wire Baskets (3x)** | Coated steel | Removable, white powder coat | 3 | ₹800-₹1,200 ea | Storage organization |
| **LED Light Strips** | 12V/24V DC | High-efficiency, cold-rated, lid-mounted | 3 | ₹400-₹600 ea | Interior lighting |
| **Wheels/Casters** | Heavy-duty | Locking, 100-150kg capacity | 4 | ₹300-₹500 ea | Mobility |
| **Drain Plug** | Stainless steel | For defrost water removal | 1 | ₹200-₹400 | Maintenance |
| **Gold Geometric Decals** | Vinyl/screen print | Tech-style linework, ZAZEN branding | 1 set | ₹1,000-₹2,000 | Aesthetics |

**Mechanical Components Subtotal**: ₹52,800 - ₹87,200

---

## 6. Connectivity & Software

| Component | Part/Model | Specifications | Qty | Unit Cost Est. | Notes |
|-----------|------------|----------------|-----|----------------|-------|
| **Wi-Fi Module** | ESP32 or similar | 2.4GHz, integrated in Astra VCU | Included | - | Local connectivity |
| **4G Cellular Modem** (optional) | SIM7600 or similar | LTE Cat-1, backup connectivity | 1 | ₹2,000-₹3,500 | Remote/critical apps |
| **SIM Card** | Data-only | Monthly data plan (500MB-1GB) | 1 | ₹200-₹500/mo | Recurring cost |
| **ESP32-CAM** (optional) | Camera module | 2MP, for visual inventory tracking | 1 | ₹600-₹1,000 | Inventory management |
| **Cloud Platform** | AWS IoT / Azure | Data storage, analytics, mobile app backend | - | ₹500-₹2,000/unit/yr | Subscription cost |
| **Mobile App** | iOS + Android | Native apps for monitoring/control | - | Development cost | One-time + updates |

**Connectivity & Software Subtotal**: ₹3,300 - ₹7,000 (hardware) + subscription costs

---

## 7. Packaging & Documentation

| Item | Description | Qty | Unit Cost Est. | Notes |
|------|-------------|-----|----------------|-------|
| **Installation Manual** | Printed guide | 1 | ₹50-₹100 | User documentation |
| **Quick Start Guide** | Laminated card | 1 | ₹20-₹50 | Setup instructions |
| **Warranty Card** | 2-year warranty | 1 | ₹10-₹30 | Service info |
| **Packaging** | Cardboard box + foam | 1 | ₹500-₹1,000 | Shipping protection |
| **Cable Ties/Hardware** | Mounting screws, zip ties | 1 kit | ₹100-₹200 | Installation materials |

**Packaging & Documentation Subtotal**: ₹680 - ₹1,380

---

## BOM Summary

### Smart Retrofit Kit (Upgrade Existing Freezer)

| Category | Cost Range |
|----------|------------|
| Core Control System | ₹31,500 - ₹48,000 |
| Refrigeration Components | ₹33,300 - ₹51,600 |
| Sensor Suite | ₹7,850 - ₹13,400 |
| Power System (Basic) | ₹4,000 - ₹7,500 |
| Connectivity & Software | ₹3,300 - ₹7,000 |
| Packaging & Documentation | ₹680 - ₹1,380 |
| **TOTAL COMPONENT COST** | **₹80,630 - ₹128,880** |
| **+ Labor/Installation** | **₹5,000 - ₹10,000** |
| **+ Margin (30-40%)** | **₹25,689 - ₹55,552** |
| **= RETAIL PRICE (Retrofit Kit)** | **₹111,319 - ₹194,432** |

**Target Retail Price**: **₹40,000 - ₹75,000** (requires cost optimization or subsidy for volume)

---

### Premium Triple-Door Freezer (New Complete Unit)

| Category | Cost Range |
|----------|------------|
| Core Control System | ₹31,500 - ₹48,000 |
| Refrigeration Components | ₹33,300 - ₹51,600 |
| Sensor Suite | ₹7,850 - ₹13,400 |
| Power System (48V with Solar/Battery option) | ₹56,000 - ₹104,000 |
| Mechanical Components | ₹52,800 - ₹87,200 |
| Connectivity & Software | ₹3,300 - ₹7,000 |
| Packaging & Documentation | ₹680 - ₹1,380 |
| **TOTAL COMPONENT COST** | **₹185,430 - ₹312,580** |
| **+ Assembly Labor** | **₹15,000 - ₹25,000** |
| **+ Margin (30-40%)** | **₹60,129 - ₹135,032** |
| **= RETAIL PRICE (Premium Unit)** | **₹260,559 - ₹472,612** |

**Target Retail Price**: **₹250,000 - ₹450,000** (competitive with premium commercial freezers)

---

## Cost Optimization Strategies

### Volume Discounts
- **PCB Assembly**: Astra VCU and Nayana HMI costs drop 30-40% at 100+ unit volumes
- **Compressors**: Bulk purchase from Chinese manufacturers (Huayi, Highly, Panasonic subsidiary)
- **Sensors**: Generic NTC thermistors vs. branded PT1000 (50% savings, slight accuracy trade-off)
- **Enclosures**: Sheet metal fabrication costs drop with volume orders

### Value Engineering Options
- **Basic Model**: Remove ESP32-CAM, vibration sensor, humidity sensor (save ₹2,000-₹3,000)
- **Wi-Fi Only**: Skip 4G modem for cost-sensitive markets (save ₹2,000-₹3,500)
- **AC Power Only**: Remove solar charge controller and battery system (save ₹48,000-₹75,000)
- **Single Display Option**: Offer models with LED indicators instead of Nayana HMI for budget segment (save ₹6,000-₹9,000)

### Supplier Partnerships
- **Compressor OEM**: Joint development with Highly or Secop for custom BLDC models
- **PCB Manufacturing**: Partner with Indian EMS providers (Dixon, Syrma SGS) for local assembly
- **Sheet Metal**: Local fabricators in Bangalore/Pune for cabinet production

---

## Lead Time Analysis

| Component Category | Typical Lead Time | Critical Path? |
|-------------------|-------------------|----------------|
| Custom PCBs (Astra, Nayana) | 4-6 weeks | ✓ Yes |
| BLDC Compressor | 6-8 weeks (import) | ✓ Yes |
| EEV, Sensors | 2-4 weeks | No |
| Sheet Metal Cabinet | 3-4 weeks | No |
| EV Traction Inverter | 4-6 weeks | Yes |
| DC-DC Converter | 2-3 weeks | No |
| Assembly & Testing | 1-2 weeks | No |

**Total Lead Time (New Orders)**: 8-10 weeks for complete units

**Strategy**: Maintain buffer stock of long-lead items (compressors, PCBs) to enable 2-week delivery

---

## Quality Control Checkpoints

### Incoming Inspection
- Compressor bench test (pressure, current draw, noise)
- PCB functional test (all I/O, communication)
- Sensor calibration verification
- Cabinet dimensional check

### Assembly QC
- Refrigerant system leak test (nitrogen pressure test, 24 hours)
- Electrical continuity and insulation resistance
- CAN bus communication verification
- Sensor placement and wiring check

### Final Testing
- **Functional Test**: Cool-down from ambient to -18°C, record time
- **Energy Consumption**: Measure steady-state power draw vs. spec
- **Temperature Stability**: 24-hour monitoring, ±0.5°C target
- **IoT Connectivity**: Verify cloud platform data upload
- **UI Test**: HMI touchscreen response, all screens functional
- **Safety Test**: Ground fault, thermal cut-out, battery protection verification

### Burn-In (Premium Units)
- 72-hour continuous operation before shipment
- Automated data logging of all parameters
- Infant mortality screening

---

## Spare Parts Strategy

### Critical Spares (Field-Replaceable)
- Astra VCU (programmed, calibrated)
- Nayana HMI display
- Temperature sensors (pre-calibrated)
- Door gaskets
- LED light strips
- Fuses and breakers

### Service Parts (Technician-Replaceable)
- BLDC compressor (requires refrigerant handling)
- EEV valve
- Pressure transducers
- DC-DC converter
- Solid state relay

### Warranty Stock
- Maintain 5% of monthly sales volume as spare parts inventory
- Regional service centers (Bangalore, Mumbai, Delhi) with spare parts stock
- 24-hour replacement SLA for critical components (VCU, compressor)

---

*ZAZEN SYSTEMS—Engineered for Excellence*
