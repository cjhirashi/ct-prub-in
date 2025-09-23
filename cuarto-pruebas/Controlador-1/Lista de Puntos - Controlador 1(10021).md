# 📊 Lista Completa de Puntos - Controlador 1 (DDC 10021)

![Status](https://img.shields.io/badge/controlador-operativo-green)
![Points](https://img.shields.io/badge/puntos_BACnet-136-blue)
![IO](https://img.shields.io/badge/IO_físicas-48-orange)
![MAC](https://img.shields.io/badge/MAC_address-21-purple)

> **Controlador principal** para operación directa de VAVs, medición de caudales y control de compuertas en el Cuarto de Pruebas INNES

---

## 📋 **Resumen Ejecutivo**

| **Parámetro** | **Valor** | **Descripción** |
|---------------|-----------|-----------------|
| **Modelo** | KMC BAC-5901C | Controlador DDC principal |
| **Dirección Interna** | 10021 | Identificador BACnet |
| **MAC Address** | 21 | Dirección física MS/TP |
| **Expansiones** | 2x CAN-5901 | 16 I/O adicionales c/u |
| **I/O Físicas** | 24 E + 24 S | Total disponibles |
| **Variables BACnet** | 136 puntos | Variables analógicas + digitales |

---

## 🎯 **Variables Analógicas (AV1-AV120)**

### **📊 Medición de Caudales y Calibración**

#### **Plenum 1 - Variables de Calibración**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV1** | P1_VM_DP | VAV Mediana - Presión diferencial | inWC |
| **AV2** | P1_VM_M | VAV Mediana - Multiplicador calibración | Factor |
| **AV3** | P1_VM_O | VAV Mediana - Offset calibración | CFM |
| **AV4** | P1_VM_Q | VAV Mediana - Caudal calculado | CFM |
| **AV5** | P1_VG_DP | VAV Grande - Presión diferencial | inWC |
| **AV6** | P1_VG_M | VAV Grande - Multiplicador calibración | Factor |
| **AV7** | P1_VG_O | VAV Grande - Offset calibración | CFM |
| **AV8** | P1_VG_Q | VAV Grande - Caudal calculado | CFM |
| **AV9** | P1_Q | Caudal total Plenum 1 | CFM |
| **AV59** | P1_VC_DP | VAV Chica - Presión diferencial | inWC |
| **AV60** | P1_VC_M | VAV Chica - Multiplicador calibración | Factor |
| **AV61** | P1_VC_O | VAV Chica - Offset calibración | CFM |
| **AV62** | P1_VC_Q | VAV Chica - Caudal calculado | CFM |

#### **Plenum 2 - Variables de Calibración**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV10** | P2_VM_DP | VAV Mediana - Presión diferencial | inWC |
| **AV11** | P2_VM_M | VAV Mediana - Multiplicador calibración | Factor |
| **AV12** | P2_VM_O | VAV Mediana - Offset calibración | CFM |
| **AV13** | P2_VM_Q | VAV Mediana - Caudal calculado | CFM |
| **AV14** | P2_VG_DP | VAV Grande - Presión diferencial | inWC |
| **AV15** | P2_VG_M | VAV Grande - Multiplicador calibración | Factor |
| **AV16** | P2_VG_O | VAV Grande - Offset calibración | CFM |
| **AV17** | P2_VG_Q | VAV Grande - Caudal calculado | CFM |
| **AV18** | P2_Q | Caudal total Plenum 2 | CFM |

#### **Plenum 3 - Variables de Calibración**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV63** | P3_VG_DP | VAV Grande - Presión diferencial | inWC |
| **AV64** | P3_VG_M | VAV Grande - Multiplicador calibración | Factor |
| **AV65** | P3_VG_O | VAV Grande - Offset calibración | CFM |
| **AV66** | P3_VG_Q | VAV Grande - Caudal calculado | CFM |

#### **Plenum 4 - Variables de Calibración**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV19** | P4_VM_DP | VAV Mediana - Presión diferencial | inWC |
| **AV20** | P4_VM_M | VAV Mediana - Multiplicador calibración | Factor |
| **AV21** | P4_VM_O | VAV Mediana - Offset calibración | CFM |
| **AV22** | P4_VM_Q | VAV Mediana - Caudal calculado | CFM |
| **AV23** | P4_VG_DP | VAV Grande - Presión diferencial | inWC |
| **AV24** | P4_VG_M | VAV Grande - Multiplicador calibración | Factor |
| **AV25** | P4_VG_O | VAV Grande - Offset calibración | CFM |
| **AV26** | P4_VG_Q | VAV Grande - Caudal calculado | CFM |
| **AV27** | P4_VC_DP | VAV Chica - Presión diferencial | inWC |
| **AV28** | P4_VC_M | VAV Chica - Multiplicador calibración | Factor |
| **AV29** | P4_VC_O | VAV Chica - Offset calibración | CFM |
| **AV30** | P4_VC_Q | VAV Chica - Caudal calculado | CFM |
| **AV31** | P4_Q | Caudal total Plenum 4 | CFM |

#### **Plenum 5 - Variables de Calibración**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV32** | P5_VC_DP | VAV Chica - Presión diferencial | inWC |
| **AV33** | P5_VC_M | VAV Chica - Multiplicador calibración | Factor |
| **AV34** | P5_VC_O | VAV Chica - Offset calibración | CFM |
| **AV35** | P5_VC_Q | VAV Chica - Caudal calculado | CFM |
| **AV36** | P5_VG_DP | VAV Grande - Presión diferencial | inWC |
| **AV37** | P5_VG_M | VAV Grande - Multiplicador calibración | Factor |
| **AV38** | P5_VG_O | VAV Grande - Offset calibración | CFM |
| **AV39** | P5_VG_Q | VAV Grande - Caudal calculado | CFM |
| **AV40** | P5_Q | Caudal total Plenum 5 | CFM |

#### **Plenum 6 - Variables de Calibración**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV41** | P6_VG_DP | VAV Grande - Presión diferencial | inWC |
| **AV42** | P6_VG_M | VAV Grande - Multiplicador calibración | Factor |
| **AV43** | P6_VG_O | VAV Grande - Offset calibración | CFM |
| **AV44** | P6_VG_Q | VAV Grande - Caudal calculado | CFM |
| **AV45** | P6_VM_DP | VAV Mediana - Presión diferencial | inWC |
| **AV46** | P6_VM_M | VAV Mediana - Multiplicador calibración | Factor |
| **AV47** | P6_VM_O | VAV Mediana - Offset calibración | CFM |
| **AV48** | P6_VM_Q | VAV Mediana - Caudal calculado | CFM |
| **AV49** | P6_Q | Caudal total Plenum 6 | CFM |

#### **Plenum R7 (Retorno) - Variables de Calibración**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV50** | PR7_VC_DP | VAV Chica - Presión diferencial | inWC |
| **AV51** | PR7_VC_M | VAV Chica - Multiplicador calibración | Factor |
| **AV52** | PR7_VC_O | VAV Chica - Offset calibración | CFM |
| **AV53** | PR7_VC_Q | VAV Chica - Caudal calculado | CFM |
| **AV54** | PR7_VG_DP | VAV Grande - Presión diferencial | inWC |
| **AV55** | PR7_VG_M | VAV Grande - Multiplicador calibración | Factor |
| **AV56** | PR7_VG_O | VAV Grande - Offset calibración | CFM |
| **AV57** | PR7_VG_Q | VAV Grande - Caudal calculado | CFM |
| **AV58** | PR7_Q | Caudal total Plenum R7 | CFM |

### **🎛️ Variables de Control Operacional**

#### **Demandas por Plenum**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV67** | P1_VC_DEMANDA | Plenum 1 VAV Chica - Demanda | % |
| **AV68** | P3_VG_DEMANDA | Plenum 3 VAV Grande - Demanda | % |
| **AV80** | VGR_DEMANDA | VAV Grande Retorno - Demanda | % |
| **AV81** | VCR_DEMANDA | VAV Chica Retorno - Demanda | % |
| **AV82** | VG_DEMANDA | VAV Grande - Demanda | % |
| **AV83** | VM_DEMANDA | VAV Mediana - Demanda | % |
| **AV84** | VC_DEMANDA | VAV Chica - Demanda | % |
| **AV85** | P1_VM_DEMANDA | Plenum 1 VAV Mediana - Demanda | % |
| **AV86** | P1_VG_DEMANDA | Plenum 1 VAV Grande - Demanda | % |
| **AV87** | P2_VM_DEMANDA | Plenum 2 VAV Mediana - Demanda | % |
| **AV88** | P2_VG_DEMANDA | Plenum 2 VAV Grande - Demanda | % |
| **AV89** | P4_VM_DEMANDA | Plenum 4 VAV Mediana - Demanda | % |
| **AV90** | P4_VG_DEMANDA | Plenum 4 VAV Grande - Demanda | % |
| **AV91** | P4_VC_DEMANDA | Plenum 4 VAV Chica - Demanda | % |
| **AV92** | P5_VC_DEMANDA | Plenum 5 VAV Chica - Demanda | % |
| **AV93** | P5_VG_DEMANDA | Plenum 5 VAV Grande - Demanda | % |
| **AV94** | P6_VG_DEMANDA | Plenum 6 VAV Grande - Demanda | % |
| **AV95** | P6_VM_DEMANDA | Plenum 6 VAV Mediana - Demanda | % |
| **AV96** | PR7_VC_DEMANDA | Plenum R7 VAV Chica - Demanda | % |
| **AV97** | PR7_VG_DEMANDA | Plenum R7 VAV Grande - Demanda | % |

#### **Variables Activas del Sistema**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV98** | VG_Q | VAV Grande Activa - Caudal | CFM |
| **AV99** | VM_Q | VAV Mediana Activa - Caudal | CFM |
| **AV100** | VC_Q | VAV Chica Activa - Caudal | CFM |
| **AV101** | Q_T | VAVs Activas - Caudal total | CFM |
| **AV102** | VGR_Q | VAV Grande Retorno - Caudal | CFM |
| **AV103** | VCR_Q | VAV Chica Retorno - Caudal | CFM |
| **AV104** | QR_T | VAVs Retorno - Caudal total | CFM |

#### **Mediciones y Setpoints del Sistema**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV105** | DP_1 | Plenum Activo - Caída presión sensor 1 | inWC |
| **AV106** | DP_2 | Plenum Activo - Caída presión sensor 2 | inWC |
| **AV107** | VG_Q_SP | VAV Grande Activa - Setpoint caudal | CFM |
| **AV108** | VM_Q_SP | VAV Mediana Activa - Setpoint caudal | CFM |
| **AV109** | VC_Q_SP | VAV Chica Activa - Setpoint caudal | CFM |
| **AV110** | VGR_Q_SP | VAV Grande Retorno - Setpoint caudal | CFM |
| **AV111** | VCR_Q_SP | VAV Chica Retorno - Setpoint caudal | CFM |

#### **Límites Operacionales**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV112** | VG_MIN | VAV Grande Activa - Caudal mínimo | CFM |
| **AV113** | VG_MAX | VAV Grande Activa - Caudal máximo | CFM |
| **AV114** | VM_MIN | VAV Mediana Activa - Caudal mínimo | CFM |
| **AV115** | VM_MAX | VAV Mediana Activa - Caudal máximo | CFM |
| **AV116** | VC_MIN | VAV Chica Activa - Caudal mínimo | CFM |
| **AV117** | VC_MAX | VAV Chica Activa - Caudal máximo | CFM |

#### **Setpoints del Sistema**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV118** | SAT_SP | Temperatura Suministro - Setpoint | °C |
| **AV119** | DP_SP | Presión Diferencial - Setpoint | inWC |

#### **Variables de Control PI**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV69** | GR_P | Caja Grande - Valor Proporcional | - |
| **AV70** | GR_I | Caja Grande - Valor Integral | - |
| **AV71** | MD_P | Caja Mediana - Valor Proporcional | - |
| **AV72** | MD_I | Caja Mediana - Valor Integral | - |
| **AV73** | CH_P | Caja Chica - Valor Proporcional | - |
| **AV74** | CH_I | Caja Chica - Valor Integral | - |

---

## 🔘 **Variables Digitales (BV1-BV42)**

### **Estados del Sistema**
| **Punto** | **Variable** | **Descripción** | **Estados** |
|-----------|--------------|-----------------|-------------|
| **BV1** | SS_CP | Sistema - Activación | ACTIVA/INACTIVA |
| **BV2** | ST_CP | Sistema - Estado | ACTIVA/INACTIVA |

### **Estados de Plenums**
| **Punto** | **Variable** | **Descripción** | **Estados** |
|-----------|--------------|-----------------|-------------|
| **BV3** | ST_P1 | Plenum 1 - Estado | ACTIVA/INACTIVA |
| **BV4** | ST_P2 | Plenum 2 - Estado | ACTIVA/INACTIVA |
| **BV5** | ST_P3 | Plenum 3 - Estado | ACTIVA/INACTIVA |
| **BV6** | ST_P4 | Plenum 4 - Estado | ACTIVA/INACTIVA |
| **BV7** | ST_P5 | Plenum 5 - Estado | ACTIVA/INACTIVA |
| **BV8** | ST_P6 | Plenum 6 - Estado | ACTIVA/INACTIVA |

### **Activación de VAVs**
| **Punto** | **Variable** | **Descripción** | **Estados** |
|-----------|--------------|-----------------|-------------|
| **BV9** | VG_ACT | VAV Grande - Activación | ACTIVA/INACTIVA |
| **BV10** | VM_ACT | VAV Mediana - Activación | ACTIVA/INACTIVA |
| **BV11** | VC_ACT | VAV Chica - Activación | ACTIVA/INACTIVA |
| **BV12** | VGR_ACT | VAV Grande Retorno - Activación | ACTIVA/INACTIVA |
| **BV13** | VCR_ACT | VAV Chica Retorno - Activación | ACTIVA/INACTIVA |

---

## 🔌 **Entradas Físicas (AI3-AI26)**

### **Sensores de Presión Diferencial**
| **I/O** | **Variable** | **Descripción** | **Sensor** | **Rango** |
|---------|--------------|-----------------|------------|-----------|
| **AI3** | P1_VM_IN | Presión diferencial VAV Mediana P1 | MS-311 | 0-2 inWC |
| **AI4** | P1_VG_IN | Presión diferencial VAV Grande P1 | MS-311 | 0-2 inWC |
| **AI5** | P2_VM_IN | Presión diferencial VAV Mediana P2 | MS-311 | 0-2 inWC |
| **AI6** | P2_VG_IN | Presión diferencial VAV Grande P2 | MS-311 | 0-2 inWC |
| **AI7** | P4_VM_IN | Presión diferencial VAV Mediana P4 | MS-311 | 0-2 inWC |
| **AI8** | P4_VG_IN | Presión diferencial VAV Grande P4 | MS-311 | 0-2 inWC |
| **AI9** | P4_VC_IN | Presión diferencial VAV Chica P4 | MS-311 | 0-2 inWC |
| **AI10** | P5_VC_IN | Presión diferencial VAV Chica P5 | MS-311 | 0-2 inWC |
| **AI11** | P5_VG_IN | Presión diferencial VAV Grande P5 | MS-311 | 0-2 inWC |
| **AI12** | P6_VG_IN | Presión diferencial VAV Grande P6 | MS-311 | 0-2 inWC |
| **AI13** | P6_VM_IN | Presión diferencial VAV Mediana P6 | MS-311 | 0-2 inWC |
| **AI14** | PR7_VC_IN | Presión diferencial VAV Chica PR7 | MS-311 | 0-2 inWC |
| **AI15** | PR7_VG_IN | Presión diferencial VAV Grande PR7 | MS-311 | 0-2 inWC |
| **AI16** | P1_VC_IN | Presión diferencial VAV Chica P1 | MS-311 | 0-2 inWC |
| **AI17** | P3_VG_IN | Presión diferencial VAV Grande P3 | MS-311 | 0-2 inWC |

### **Sensores de Presión de Plenum**
| **I/O** | **Variable** | **Descripción** | **Sensor** | **Rango** |
|---------|--------------|-----------------|------------|-----------|
| **AI18** | P1_DP_1 | Plenum 1 - Caída presión 1 | SETRA 2651001 | 0-1 inWC |

### **Sensores de Temperatura**
| **I/O** | **Variable** | **Descripción** | **Sensor** | **Rango** |
|---------|--------------|-----------------|------------|-----------|
| **AI19** | SAT | Temperatura suministro aire | TE-DFG | -40 a +85°C |

### **Sensores de Velocidad Aire - Tiro 1**
| **I/O** | **Variable** | **Descripción** | **Sensor** | **Rango** |
|---------|--------------|-----------------|------------|-----------|
| **AI20** | T1_S1_V | Velocidad aire Tiro 1 - Sensor 1 | ALNOR 8475-075 | 10-500 FPM |
| **AI21** | T1_S2_V | Velocidad aire Tiro 1 - Sensor 2 | ALNOR 8475-075 | 10-500 FPM |
| **AI22** | T1_S3_V | Velocidad aire Tiro 1 - Sensor 3 | ALNOR 8475-075 | 10-500 FPM |
| **AI23** | T1_S4_V | Velocidad aire Tiro 1 - Sensor 4 | ALNOR 8475-075 | 10-500 FPM |
| **AI24** | T1_S5_V | Velocidad aire Tiro 1 - Sensor 5 | ALNOR 8475-075 | 10-500 FPM |
| **AI25** | T1_S6_V | Velocidad aire Tiro 1 - Sensor 6 | ALNOR 8475-075 | 10-500 FPM |
| **AI26** | T1_S7_V | Velocidad aire Tiro 1 - Sensor 7 | ALNOR 8475-075 | 10-500 FPM |

---

## ⚡ **Salidas Físicas**

### **Salidas Analógicas - Compuertas VAV (AO1-AO23)**
| **I/O** | **Variable** | **Descripción** | **Actuador** | **Señal** |
|---------|--------------|-----------------|-------------|-----------|
| **AO1** | P1_VM_COMPVAV | Plenum 1 VAV Mediana - Compuerta | Belimo LMV-D3-MFT | 2-10VDC |
| **AO2** | P1_VG_COMPVAV | Plenum 1 VAV Grande - Compuerta | Belimo LMV-D3-MFT | 2-10VDC |
| **AO3** | P2_VM_COMPVAV | Plenum 2 VAV Mediana - Compuerta | Belimo LMV-D3-MFT | 2-10VDC |
| **AO4** | P2_VG_COMPVAV | Plenum 2 VAV Grande - Compuerta | Belimo LMV-D3-MFT | 2-10VDC |
| **AO5** | P4_VM_COMPVAV | Plenum 4 VAV Mediana - Compuerta | Belimo LMV-D3-MFT | 2-10VDC |
| **AO6** | P4_VG_COMPVAV | Plenum 4 VAV Grande - Compuerta | Belimo LMV-D3-MFT | 2-10VDC |
| **AO7** | P4_VC_COMPVAV | Plenum 4 VAV Chica - Compuerta | Belimo LMV-D3-MFT | 2-10VDC |
| **AO8** | P5_VC_COMPVAV | Plenum 5 VAV Chica - Compuerta | Belimo LMV-D3-MFT | 2-10VDC |
| **AO9** | P5_VG_COMPVAV | Plenum 5 VAV Grande - Compuerta | Belimo LMV-D3-MFT | 2-10VDC |
| **AO10** | P6_VG_COMPVAV | Plenum 6 VAV Grande - Compuerta | Belimo LMV-D3-MFT | 2-10VDC |
| **AO11** | P6_VM_COMPVAV | Plenum 6 VAV Mediana - Compuerta | Belimo LMV-D3-MFT | 2-10VDC |
| **AO12** | PR7_VC_COMPVAV | Plenum R7 VAV Chica - Compuerta | Belimo LMV-D3-MFT | 2-10VDC |
| **AO13** | PR7_VG_COMPVAV | Plenum R7 VAV Grande - Compuerta | Belimo LMV-D3-MFT | 2-10VDC |
| **AO21** | P1_VC_COMPVAV | Plenum 1 VAV Chica - Compuerta | Belimo LMV-D3-MFT | 2-10VDC |
| **AO23** | P3_VG_COMPVAV | Plenum 3 VAV Grande - Compuerta | Belimo LMV-D3-MFT | 2-10VDC |

### **Salidas Digitales - Compuertas Bloqueo (BO14-BO24)**
| **I/O** | **Variable** | **Descripción** | **Actuador** | **Estados** |
|---------|--------------|-----------------|-------------|-------------|
| **BO14** | P1_VM_COMPBLQ | Plenum 1 VAV Mediana - Bloqueo | Belimo LMB24-3 | ABIERTA/CERRADA |
| **BO15** | P1_VG_COMPBLQ | Plenum 1 VAV Grande - Bloqueo | Belimo LMB24-3 | ABIERTA/CERRADA |
| **BO16** | P2_VM_COMPBLQ | Plenum 2 VAV Mediana - Bloqueo | Belimo LMB24-3 | ABIERTA/CERRADA |
| **BO17** | PR7_VC_COMPBLQ | Plenum R7 VAV Chica - Bloqueo | Belimo LMB24-3 | ABIERTA/CERRADA |
| **BO18** | PR7_VG_COMPBLQ | Plenum R7 VAV Grande - Bloqueo | Belimo LMB24-3 | ABIERTA/CERRADA |
| **BO19** | SS_HUMO | Compuerta máquina humo | Belimo LMB24-3 | ABIERTA/CERRADA |
| **BO22** | P1_VC_COMPBLQ | Plenum 1 VAV Chica - Bloqueo | Belimo LMB24-3 | ABIERTA/CERRADA |
| **BO24** | P3_VG_COMPBLQ | Plenum 3 VAV Grande - Bloqueo | Belimo LMB24-3 | ABIERTA/CERRADA |

---

## 📊 **Variable Multi-Estado**

| **Punto** | **Variable** | **Descripción** | **Estados** |
|-----------|--------------|-----------------|-------------|
| **MSV1** | PLENUM | Plenum en operación | 1, 2, 3, 4, 5, 6 |

---

## 🔧 **Programas de Control**

| **Programa** | **Función** | **Variables Principales** | **Ciclo** |
|--------------|-------------|---------------------------|-----------|
| **PRG1_SENSORES** | Cálculo caudales VAV | AV1-AV66 (DP, M, O, Q) | Continuo |
| **PRG2_VAVS** | Control compuertas | AO1-AO23, BO14-BO24 | 5 seg |
| **PRG3_PLENUMS** | Gestión por plenum | MSV1, BV3-BV8, AV98-104 | Continuo |
| **PRG4_DEMANDA** | Algoritmo PI control | AV69-74, AV82-97 | 1 seg |
| **PRG5_UMA** | Sincronización UMA | BV/AV comunicación remota | 30 seg |

---

## ⚠️ **Alarmas y Estados Críticos**

### **Límites de Alarma por Tipo de VAV**
| **Tipo VAV** | **Caudal Min** | **Caudal Max** | **Alarma Baja** | **Alarma Alta** |
|--------------|----------------|----------------|-----------------|-----------------|
| **Chica (VC)** | 50 CFM | 400 CFM | <30 CFM | >450 CFM |
| **Mediana (VM)** | 200 CFM | 800 CFM | <150 CFM | >900 CFM |
| **Grande (VG)** | 500 CFM | 1500 CFM | <400 CFM | >1700 CFM |

### **Variables de Estado Sistema**
- **SS_CP = 0**: Sistema inactivo - Todas las compuertas en posición segura
- **ST_CP = 1**: Sistema operativo - Control automático activo
- **Plenum activo**: Solo un plenum puede estar activo simultáneamente
- **Interlocks**: Compuertas bloqueo previenen operación si están cerradas

---

## 🔗 **Enlaces de Referencia**

### **📋 Documentación Relacionada**
- **[Lista Completa Controlador 2](./puntos-controlador-2.md)** - DDC 10022 Calibración
- **[Mapeo I/O Físicas](./mapeo-io-fisicas.md)** - Conexiones de campo detalladas
- **[Procedimientos Operación](./Procedimientos/operacion-diaria.md)** - Guías de uso
- **[Manual Calibración](./Procedimientos/calibracion-vav.md)** - Proceso completo

### **🔧 Especificaciones Técnicas**
- **[KMC BAC-5901C Manual](./Documentación/Manuales/BAC-5901C.pdf)** - Controlador principal
- **[KMC CAN-5901 Manual](./Documentación/Manuales/CAN-5901.pdf)** - Módulos expansión
- **[Belimo Actuadores](./Documentación/Especificaciones/belimo-actuadores.pdf)** - LMV-D3-MFT, LMB24-3
- **[Dwyer Sensores DP](./Documentación/Especificaciones/dwyer-ms311.pdf)** - MS-311 presión diferencial

### **📊 Diagramas Técnicos**
- **[Diagrama Eléctrico CN-01](./Documentación/Diagramas/AUT-E-CN-1.pdf)** - Conexionado controlador
- **[Diagrama Expansión IO1-01](./Documentación/Diagramas/AUT-E-IO1-1.pdf)** - Primera expansión  
- **[Diagrama Expansión IO1-02](./Documentación/Diagramas/AUT-E-IO1-2.pdf)** - Segunda expansión
- **[Arquitectura General](./Documentación/Diagramas/AUT-CM.pdf)** - Comunicaciones sistema

---

## 📝 **Notas Importantes**

### **🎯 Para Programadores**
- Todas las variables AV con sufijo "_M" y "_O" son parámetros de calibración críticos
- Las demandas (AV82-97) se calculan mediante algoritmos PI en PRG4
- El selector MSV1 determina qué plenum está activo y asigna variables dinámicamente
- Variables AV98-104 son las "activas" que cambian según plenum seleccionado

### **⚡ Para Técnicos de Campo**
- AI3-AI17: Sensores presión diferencial requieren calibración periódica
- AO1-AO23: Salidas proporcionales 2-10VDC para actuadores Belimo
- BO14-BO24: Salidas digitales 24VAC para compuertas bloqueo vía relevadores
- AI18: Sensor presión plenum crítico para control de sistema

### **🔧 Para Mantenimiento**
- Verificar alimentación 24VAC en controlador y expansiones (TR-01, TR-02)
- Revisar comunicación CAN entre controlador base y expansiones
- Monitorear estado BACnet MS/TP (MAC 21) en red principal
- Calibrar sensores Dwyer MS-311 cada 6 meses

---

<div align="center">

**📊 Controlador 1 - INNES Aire**  
*Control operacional directo de 15 VAVs distribuidas en 7 plenums*

[![Manual Operación](https://img.shields.io/badge/📖-Manual_Operación-blue)](./Procedimientos/operacion-diaria.md)
[![Diagramas](https://img.shields.io/badge/📋-Diagramas_Técnicos-green)](./Documentación/Diagramas/)
[![Soporte](https://img.shields.io/badge/📞-Soporte_Técnico-red)](../README.md#contactos-emergencia)

</div>