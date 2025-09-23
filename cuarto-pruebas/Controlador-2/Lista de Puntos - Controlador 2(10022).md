# 🔧 Lista Completa de Puntos - Controlador 2 (DDC 10022)

![Status](https://img.shields.io/badge/controlador-operativo-green)
![Points](https://img.shields.io/badge/puntos_BACnet-152-blue)
![IO](https://img.shields.io/badge/IO_físicas-32-orange)
![MAC](https://img.shields.io/badge/MAC_address-22-purple)

> **Controlador especializado** en calibración avanzada, análisis estadístico y medición de velocidades múltiples en el Cuarto de Pruebas INNES

---

## 📋 **Resumen Ejecutivo**

| **Parámetro** | **Valor** | **Descripción** |
|---------------|-----------|-----------------|
| **Modelo** | KMC BAC-5901C | Controlador DDC especializado |
| **Dirección Interna** | 10022 | Identificador BACnet |
| **MAC Address** | 22 | Dirección física MS/TP |
| **Expansiones** | 1x CAN-5902 | 16 entradas adicionales |
| **I/O Físicas** | 24 E + 8 S | Total disponibles |
| **Variables BACnet** | 152 puntos | Calibración + análisis |

---

## 🎯 **Variables Analógicas (AV1-AV126)**

### **🌡️ Sistema de Temperatura Ambiente**

| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV1** | T_AVG | Temperatura cuarto - Promedio | °C |
| **AV2** | T_1 | Temperatura cuarto 1 | °C |
| **AV3** | T_2 | Temperatura cuarto 2 | °C |
| **AV4** | T_3 | Temperatura cuarto 3 | °C |
| **AV5** | T_4 | Temperatura cuarto 4 | °C |

### **⚙️ Sistema de Calibración Híbrido KMC-Excel**

#### **Parámetros de Configuración**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV6** | CL_M | Número de muestras calibración | 5-20 |
| **AV7** | CL_T | Tiempo entre muestras | Segundos |
| **AV8** | CL_P_L | Apertura compuerta mínima | % |
| **AV9** | CL_P_H | Apertura compuerta máxima | % |
| **AV10** | CL_Q_S_L | Caudal sistema bajo | CFM |
| **AV11** | CL_Q_B_L | Caudal balómetro bajo | CFM |
| **AV12** | CL_Q_S_H | Caudal sistema alto | CFM |
| **AV13** | CL_Q_B_H | Caudal balómetro alto | CFM |

#### **Resultados de Calibración**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV14** | CL_MULTI | Multiplicador sistema calibración | Factor |
| **AV15** | CL_OFFSET | Offset sistema calibración | CFM |

#### **Variables de Control del Proceso**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV21** | NUM_MUESTRA | Número de muestras actual | Contador |
| **AV22** | TM_MUESTRA | Tiempo entre muestras actual | Segundos |

### **📊 Análisis Estadístico - 10 Grupos de Variables**

#### **Grupo 1 - Análisis Estadístico**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV31** | V_PROM_1 | Variable promedio 1 | - |
| **AV32** | V_MAX_1 | Variable máxima 1 | - |
| **AV33** | V_MIN_1 | Variable mínima 1 | - |
| **AV61** | V_MAN_1 | Variable manual 1 | - |
| **AV71** | V_GRUPO-1_1 | Variable grupo 1-1 | - |
| **AV72** | V_GRUPO-1_2 | Variable grupo 1-2 | - |
| **AV73** | V_GRUPO-1_3 | Variable grupo 1-3 | - |
| **AV74** | V_GRUPO-1_4 | Variable grupo 1-4 | - |

#### **Grupo 2 - Análisis Estadístico**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV34** | V_PROM_2 | Variable promedio 2 | - |
| **AV35** | V_MAX_2 | Variable máxima 2 | - |
| **AV36** | V_MIN_2 | Variable mínima 2 | - |
| **AV62** | V_MAN_2 | Variable manual 2 | - |
| **AV75** | V_GRUPO-2_1 | Variable grupo 2-1 | - |
| **AV76** | V_GRUPO-2_2 | Variable grupo 2-2 | - |
| **AV77** | V_GRUPO-2_3 | Variable grupo 2-3 | - |
| **AV78** | V_GRUPO-2_4 | Variable grupo 2-4 | - |

#### **Grupo 3 - Análisis Estadístico**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV37** | V_PROM_3 | Variable promedio 3 | - |
| **AV38** | V_MAX_3 | Variable máxima 3 | - |
| **AV39** | V_MIN_3 | Variable mínima 3 | - |
| **AV63** | V_MAN_3 | Variable manual 3 | - |
| **AV79** | V_GRUPO-3_1 | Variable grupo 3-1 | - |
| **AV80** | V_GRUPO-3_2 | Variable grupo 3-2 | - |
| **AV81** | V_GRUPO-3_3 | Variable grupo 3-3 | - |
| **AV82** | V_GRUPO-3_4 | Variable grupo 3-4 | - |

#### **Grupo 4 - Análisis Estadístico**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV40** | V_PROM_4 | Variable promedio 4 | - |
| **AV41** | V_MAX_4 | Variable máxima 4 | - |
| **AV42** | V_MIN_4 | Variable mínima 4 | - |
| **AV64** | V_MAN_4 | Variable manual 4 | - |
| **AV83** | V_GRUPO-4_1 | Variable grupo 4-1 | - |
| **AV84** | V_GRUPO-4_2 | Variable grupo 4-2 | - |
| **AV85** | V_GRUPO-4_3 | Variable grupo 4-3 | - |
| **AV86** | V_GRUPO-4_4 | Variable grupo 4-4 | - |

#### **Grupo 5 - Análisis Estadístico**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV43** | V_PROM_5 | Variable promedio 5 | - |
| **AV44** | V_MAX_5 | Variable máxima 5 | - |
| **AV45** | V_MIN_5 | Variable mínima 5 | - |
| **AV65** | V_MAN_5 | Variable manual 5 | - |
| **AV87** | V_GRUPO-5_1 | Variable grupo 5-1 | - |
| **AV88** | V_GRUPO-5_2 | Variable grupo 5-2 | - |
| **AV89** | V_GRUPO-5_3 | Variable grupo 5-3 | - |
| **AV90** | V_GRUPO-5_4 | Variable grupo 5-4 | - |

#### **Grupo 6 - Análisis Estadístico**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV46** | V_PROM_6 | Variable promedio 6 | - |
| **AV47** | V_MAX_6 | Variable máxima 6 | - |
| **AV48** | V_MIN_6 | Variable mínima 6 | - |
| **AV66** | V_MAN_6 | Variable manual 6 | - |
| **AV91** | V_GRUPO-6_1 | Variable grupo 6-1 | - |
| **AV92** | V_GRUPO-6_2 | Variable grupo 6-2 | - |
| **AV93** | V_GRUPO-6_3 | Variable grupo 6-3 | - |
| **AV94** | V_GRUPO-6_4 | Variable grupo 6-4 | - |

#### **Grupo 7 - Análisis Estadístico**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV49** | V_PROM_7 | Variable promedio 7 | - |
| **AV50** | V_MAX_7 | Variable máxima 7 | - |
| **AV51** | V_MIN_7 | Variable mínima 7 | - |
| **AV67** | V_MAN_7 | Variable manual 7 | - |
| **AV95** | V_GRUPO-7_1 | Variable grupo 7-1 | - |
| **AV96** | V_GRUPO-7_2 | Variable grupo 7-2 | - |
| **AV97** | V_GRUPO-7_3 | Variable grupo 7-3 | - |
| **AV98** | V_GRUPO-7_4 | Variable grupo 7-4 | - |

#### **Grupo 8 - Análisis Estadístico**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV52** | V_PROM_8 | Variable promedio 8 | - |
| **AV53** | V_MAX_8 | Variable máxima 8 | - |
| **AV54** | V_MIN_8 | Variable mínima 8 | - |
| **AV68** | V_MAN_8 | Variable manual 8 | - |
| **AV99** | V_GRUPO-8_1 | Variable grupo 8-1 | - |
| **AV100** | V_GRUPO-8_2 | Variable grupo 8-2 | - |
| **AV101** | V_GRUPO-8_3 | Variable grupo 8-3 | - |
| **AV102** | V_GRUPO-8_4 | Variable grupo 8-4 | - |

#### **Grupo 9 - Análisis Estadístico**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV55** | V_PROM_9 | Variable promedio 9 | - |
| **AV56** | V_MAX_9 | Variable máxima 9 | - |
| **AV57** | V_MIN_9 | Variable mínima 9 | - |
| **AV69** | V_MAN_9 | Variable manual 9 | - |
| **AV103** | V_GRUPO-9_1 | Variable grupo 9-1 | - |
| **AV104** | V_GRUPO-9_2 | Variable grupo 9-2 | - |
| **AV105** | V_GRUPO-9_3 | Variable grupo 9-3 | - |
| **AV106** | V_GRUPO-9_4 | Variable grupo 9-4 | - |

#### **Grupo 10 - Análisis Estadístico**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV58** | V_PROM_10 | Variable promedio 10 | - |
| **AV59** | V_MAX_10 | Variable máxima 10 | - |
| **AV60** | V_MIN_10 | Variable mínima 10 | - |
| **AV70** | V_MAN_10 | Variable manual 10 | - |
| **AV107** | V_GRUPO-10_1 | Variable grupo 10-1 | - |
| **AV108** | V_GRUPO-10_2 | Variable grupo 10-2 | - |
| **AV109** | V_GRUPO-10_3 | Variable grupo 10-3 | - |
| **AV110** | V_GRUPO-10_4 | Variable grupo 10-4 | - |

### **🔧 Coeficientes de Velocidad por VAV**

#### **Variables de Coeficientes de Velocidad (Comunicación con Controlador 1)**
| **Punto** | **Variable** | **Descripción** | **Unidades** |
|-----------|--------------|-----------------|--------------|
| **AV112** | P1_VM_CV | Plenum 1 VAV Mediana - Coef. velocidad | Factor |
| **AV113** | P1_VG_CV | Plenum 1 VAV Grande - Coef. velocidad | Factor |
| **AV114** | P1_VC_CV | Plenum 1 VAV Chica - Coef. velocidad | Factor |
| **AV115** | P2_VM_CV | Plenum 2 VAV Mediana - Coef. velocidad | Factor |
| **AV116** | P2_VG_CV | Plenum 2 VAV Grande - Coef. velocidad | Factor |
| **AV117** | P3_VG_CV | Plenum 3 VAV Grande - Coef. velocidad | Factor |
| **AV118** | P4_VM_CV | Plenum 4 VAV Mediana - Coef. velocidad | Factor |
| **AV119** | P4_VG_CV | Plenum 4 VAV Grande - Coef. velocidad | Factor |
| **AV120** | P4_VC_CV | Plenum 4 VAV Chica - Coef. velocidad | Factor |
| **AV121** | P5_VC_CV | Plenum 5 VAV Chica - Coef. velocidad | Factor |
| **AV122** | P5_VG_CV | Plenum 5 VAV Grande - Coef. velocidad | Factor |
| **AV123** | P6_VG_CV | Plenum 6 VAV Grande - Coef. velocidad | Factor |
| **AV124** | P6_VM_CV | Plenum 6 VAV Mediana - Coef. velocidad | Factor |
| **AV125** | PR7_VC_CV | Plenum R7 VAV Chica - Coef. velocidad | Factor |
| **AV126** | PR7_VG_CV | Plenum R7 VAV Grande - Coef. velocidad | Factor |

---

## 🔘 **Variables Digitales (BV1-BV40)**

### **Estados de Plenums**
| **Punto** | **Variable** | **Descripción** | **Estados** |
|-----------|--------------|-----------------|-------------|
| **BV1** | PL1 | Plenum 1 | ACTIVA/INACTIVA |
| **BV2** | PL2 | Plenum 2 | ACTIVA/INACTIVA |
| **BV3** | PL3 | Plenum 3 | ACTIVA/INACTIVA |
| **BV4** | PL4 | Plenum 4 | ACTIVA/INACTIVA |
| **BV5** | PL5 | Plenum 5 | ACTIVA/INACTIVA |
| **BV6** | PL6 | Plenum 6 | ACTIVA/INACTIVA |

### **Activaciones de Tipos de Pruebas**
| **Punto** | **Variable** | **Descripción** | **Estados** |
|-----------|--------------|-----------------|-------------|
| **BV15** | ACT_TIRO | Activación prueba tiro | ACTIVA/INACTIVA |
| **BV16** | ACT_AREA | Activación prueba área efectiva | ACTIVA/INACTIVA |
| **BV17** | ACT_PRESION | Activación prueba caída presión | ACTIVA/INACTIVA |
| **BV18** | ACT_RETORNO | Activación prueba caudales retorno | ACTIVA/INACTIVA |

### **Control del Proceso de Pruebas**
| **Punto** | **Variable** | **Descripción** | **Estados** |
|-----------|--------------|-----------------|-------------|
| **BV21** | INICIO_PRUEBA | Inicio de prueba | ACTIVA/INACTIVA |

### **Sistema de Calibración Avanzada**
| **Punto** | **Variable** | **Descripción** | **Estados** |
|-----------|--------------|-----------------|-------------|
| **BV23** | CL_ACTIV | Activación sistema calibración | ACTIVA/INACTIVA |
| **BV24** | CL_INICIO | Inicio proceso calibración | ACTIVA/INACTIVA |
| **BV25** | CL_COMP | Selector apertura compuerta | ACTIVA/INACTIVA |
| **BV26** | CL_LEER | Leer factor calibración | ACTIVA/INACTIVA |
| **BV27** | CL_RESET | Reset factor calibración | ACTIVA/INACTIVA |
| **BV28** | CL_CALCULO | Cálculo factor calibración | ACTIVA/INACTIVA |
| **BV29** | CL_CALIBRAR | Calibrar sistema | ACTIVA/INACTIVA |

### **Variables Digitales Generales**
| **Punto** | **Variable** | **Descripción** | **Estados** |
|-----------|--------------|-----------------|-------------|
| **BV31** | V_DG_1 | Variable digital 1 | ACTIVA/INACTIVA |
| **BV32** | V_DG_2 | Variable digital 2 | ACTIVA/INACTIVA |
| **BV33** | V_DG_3 | Variable digital 3 | ACTIVA/INACTIVA |
| **BV34** | V_DG_4 | Variable digital 4 | ACTIVA/INACTIVA |
| **BV35** | V_DG_5 | Variable digital 5 | ACTIVA/INACTIVA |
| **BV36** | V_DG_6 | Variable digital 6 | ACTIVA/INACTIVA |
| **BV37** | V_DG_7 | Variable digital 7 | ACTIVA/INACTIVA |
| **BV38** | V_DG_8 | Variable digital 8 | ACTIVA/INACTIVA |
| **BV39** | V_DG_9 | Variable digital 9 | ACTIVA/INACTIVA |
| **BV40** | V_DG_10 | Variable digital 10 | ACTIVA/INACTIVA |

---

## 🔌 **Entradas Físicas (AI3-AI25)**

### **Sensores de Presión Diferencial de Plenums**
| **I/O** | **Variable** | **Descripción** | **Sensor** | **Rango** |
|---------|--------------|-----------------|------------|-----------|
| **AI3** | P1_DP_2 | Plenum 1 - Caída presión 2 | SETRA 26512R5 | 0-2.5 inWC |
| **AI4** | P2_DP | Plenum 2 - Caída presión | SETRA 2651001 | 0-1 inWC |
| **AI5** | P4_DP | Plenum 4 - Caída presión | SETRA 2651001 | 0-1 inWC |
| **AI6** | P5_DP | Plenum 5 - Caída presión | SETRA 2651001 | 0-1 inWC |
| **AI7** | P6_DP | Plenum 6 - Caída presión | SETRA 26510R5 | 0-0.5 inWC |
| **AI8** | PR7_DP | Plenum R7 - Caída presión | SETRA 26512R5 | 0-2.5 inWC |

### **Sensor de Velocidad Móvil**
| **I/O** | **Variable** | **Descripción** | **Sensor** | **Rango** |
|---------|--------------|-----------------|------------|-----------|
| **AI10** | V8 | Velocidad aire móvil | ALNOR 8475-075 | 10-500 FPM |

### **Sensores de Velocidad Aire - Tiro 2**
| **I/O** | **Variable** | **Descripción** | **Sensor** | **Rango** |
|---------|--------------|-----------------|------------|-----------|
| **AI11** | V1_T2 | Velocidad aire 1 - Tiro 2 | ALNOR 8475-075 | 10-500 FPM |
| **AI12** | V2_T2 | Velocidad aire 2 - Tiro 2 | ALNOR 8475-075 | 10-500 FPM |
| **AI13** | V3_T2 | Velocidad aire 3 - Tiro 2 | ALNOR 8475-075 | 10-500 FPM |
| **AI14** | V4_T2 | Velocidad aire 4 - Tiro 2 | ALNOR 8475-075 | 10-500 FPM |
| **AI15** | V5_T2 | Velocidad aire 5 - Tiro 2 | ALNOR 8475-075 | 10-500 FPM |
| **AI16** | V6_T2 | Velocidad aire 6 - Tiro 2 | ALNOR 8475-075 | 10-500 FPM |
| **AI17** | V7_T2 | Velocidad aire 7 - Tiro 2 | ALNOR 8475-075 | 10-500 FPM |

### **Sensores de Velocidad Aire - Tiro 3**
| **I/O** | **Variable** | **Descripción