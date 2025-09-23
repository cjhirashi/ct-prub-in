# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains the **INNES Aire HVAC Automation System** documentation - a comprehensive building automation system for air conditioning, water plants, and an HVAC testing laboratory. The system uses BACnet protocol with KMC DDC controllers distributed across multiple subsystems.

## Repository Structure

The project is organized into major subsystems:

- **`UMA-01/`** - Main Air Handling Unit control system (Controller MAC 6)
- **`Plantas-de-Agua/`** - Water plants (PAH/PAF/PAC) and UMA-02 (Controller MAC 5)
- **`Vigas-Frias/`** - Chilled beam zonal control (Controller MAC 4)
- **`Cuarto-de-Pruebas/`** - HVAC testing laboratory with 15 VAVs + 7 plenums (Controllers MAC 21,22)
- **`cuarto-pruebas/`** - Additional testing lab documentation and procedures
- **`Documentacion/`** - Technical diagrams, manuals, and guides
- **`Recursos/`** - Images, videos, and reference materials

## System Architecture

### Network Infrastructure
- **Protocol**: BACnet MS/TP and BACnet/IP
- **HMI**: Loytec LVIS at 10.0.0.251:47808
- **Controllers**: 8 KMC DDC units (BAC-5901C) with strategic distribution
- **Specialized Devices**: ClimaFlex chillers, Belimo valves, Veris sensors

### Control Programs
The testing laboratory (Cuarto-de-Pruebas) contains the most complex control logic:

**Controller 1 (MAC 21) - Primary Operations:**
- `PRG1_SENSORES` - VAV airflow calculations using differential pressure
- `PRG2_VAVS` - VAV damper control and demand management
- `PRG3_PLENUMS` - Plenum-based airflow distribution control
- `PRG4_DEMANDA` - PI control algorithms for system demand
- `PRG5_UMA` - Air handling unit synchronization

**Controller 2 (MAC 22) - Calibration:**
- `PRG1_CALIBRACION` - Hybrid KMC-Excel calibration system

## Key Operational Concepts

### Testing Laboratory Operation
- **15 VAVs** distributed across 6 supply plenums + 1 return plenum
- **3 VAV sizes**: Chica (VC: 50-400 CFM), Mediana (VM: 200-800 CFM), Grande (VG: 500-1500 CFM)
- **Calibration methodology**: Hybrid approach using KMC controllers for data acquisition and Excel for statistical analysis
- **Measurement precision**: ±2% accuracy with R² > 0.95 requirement for calibration models

### Critical Control Points
- **PAH (Chilled Water)**: 7°C setpoint, 5-12°C range
- **PAF (Cold Water)**: 18°C setpoint, 16-22°C range
- **PAC (Hot Water)**: 45°C setpoint, 40-55°C range
- **Chilled Beams**: 22°C setpoint, 20-26°C range

### BACnet Device Addressing
- UMA-01 Controller: DI 10003, MAC 6
- Water Plants Controller: DI 10002, MAC 5
- Chilled Beams Controller: DI 10001, MAC 4
- Testing Lab Controller 1: DI 10021, MAC 21
- Testing Lab Controller 2: DI 10022, MAC 22
- Independent Temperature Sensors: MAC 23-26

## Development Guidelines

### Documentation Standards
- All technical documentation is in Spanish
- Each controller/subsystem has dedicated README.md with technical specifications
- Program documentation includes functional descriptions and I/O point assignments
- Safety procedures and emergency contacts are documented in each subsystem

### System Safety
- **24 VAC/DC control voltage** throughout the system
- **LOTO procedures** required for all maintenance
- **Pressure limits**: Maximum 2.5 inWC with alarms at 2.3 inWC
- **Temperature monitoring**: Multiple independent sensors for critical measurements

### Calibration Procedures
- **Data acquisition**: Automated through KMC controllers (5-20 samples per test point)
- **Statistical analysis**: External Excel processing for regression analysis
- **Implementation**: Coefficient loading back to KMC controllers
- **Validation**: R² > 0.95 required, <5% error in operational range

## Working with This Repository

This is primarily a documentation repository containing technical specifications, operating procedures, and system architecture for a production HVAC automation system. When working with this codebase:

1. **Respect the production environment** - This documents live building automation systems
2. **Maintain Spanish language** for all technical documentation to match existing standards
3. **Follow BACnet conventions** when referencing device addresses and point names
4. **Preserve technical accuracy** as this documentation supports critical HVAC operations
5. **Reference the main README.md** for current system status and operational parameters

The testing laboratory (Cuarto-de-Pruebas) contains the most detailed technical specifications and would be the primary focus for any system development or modifications.